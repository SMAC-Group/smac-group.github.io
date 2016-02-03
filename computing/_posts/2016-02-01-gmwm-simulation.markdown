---
layout: landing
title:  "Simulation Study using GMWM"
date:   2016-02-01 18:22:52
tags: 
- Generalized Method of Wavelet Moments
- Wavelet variance
- Time Series
- Simulation Study
mathjax: true
spic: "assets/images/site/cities/lavaux_reduced.jpg"
---
Background
==========

The following simulation was designed to mimic the simulation setup in the paper "Maximum Likelihood Identification of Inertial Sensor Noise Model Parameters" of the Generalized Method of Wavelet Moments (GMWM) versus that of the integrated maximum likelihood ($ML_i$). The simulation setup as well as the code used to generate the simulation is contained below to ensure reproducibility.

Replicating the Simulation Values
=================================

On page 172 of Section V-C, the authors of the paper provide a very brief description of the simulation run. In this particular case, they emphasis that the parameters used within the simulation are that of $z$-gyroscope of the BMX0555 MEMS IMU listed in Table II on page 171. However, the simulation results presented in boxplot form in Figure 11 on page 173, indicate that these values could not be selected. Hence, we asked the authors to provide the values for the simulation. Thus, the values listed next are not found on the table. We appreciate the authors taking out time to respond to our request.

The values the authors used to conduct the simulation are:

-   $\tau _b = 530.8$
-   $\sigma _b = 1.148\times 10^{-6}$
-   $\sigma _{w} = 1.064\times 10^{-4}$

Note: The $\sigma$ values listed are the standard deviations and not the variances.

From the simulation, the authors state that the signal lasts for 12 hours. The frequency is not clearly stated, however, previous sections of the paper use 400 Hz. Thus, we have $freq = 400$. With this in hand, the signal length of the synthetic data is given from: $400 \times 60 \times 60 \times 12 = 17,280,000$.

Converting a discrete-time model to a GMWM suitable modeling term
=================================================================

On page 167, the authors then go on to define a discrete-time equivalent of the bias process (1b) as:

$$\begin{align*}
            X_t &= \exp\left(- \frac{1}{\tau_b} \Delta t \right) X_{t-1} + w_t, \\
            & w_t \sim \mathcal{N}(0, \sigma_{b}^2)\\
            & \sigma_{b}^2 = - \frac{\sigma_w^2 \tau_b}{2} \left(\exp\left(- \frac{2 \Delta t}{\tau_b}\right) - 1\right)\\
            Y_t &\sim \mathcal{N} (0,\frac{\sigma_w^2}{\Delta t})\\
            Z_t &= X_t + Y_t
\end{align*}$$

Given this formulation, there needs to be a slight transformation so that the [gmwm R package](cran.r-project.org/web/packages/gmwm) is able to both simulate and estimate the parameters.

Converting to equations preloaded into the framework yields:

AR1: $$\begin{align*}
  \phi  &= \exp \left( { - \frac{1}{ { {\tau _b} } }\Delta t} \right)  = \exp \left( { - \frac{1}{ { {530.8} } }0.0025} \right)  = 0.9999953\\
  \sigma _{AR}^2 &=  - \frac{ {\sigma _b^2{\tau _b} } }{2}\left[ {\exp \left( { - \frac{ {2\Delta t} }{ { {\tau _b} } } } \right) - 1} \right] =  - \frac{ {1.148\times 10^{-6}*{530.8} } }{2}\left[ {\exp \left( { - \frac{ {2* 0.0025} }{ { {530.8} } } } \right) - 1} \right] =  3.2947445\times 10^{-15}\\
\end{align*}$$

WN: $$\sigma _{WN}^2 = \frac{1}{ {\Delta t} }\sigma _w^2 = \frac{1}{ {0.0025} } 1.064\times 10^{-4} = 4.528384\times 10^{-6} $$

Hence, to generate the models one should use:

$AR1(\phi = 0.9999953, \sigma^2 = 3.2947445\times 10^{-15}) + WN(\sigma^2 = 4.528384\times 10^{-6})$

Converting from the GMWM back into the discrete-time model
==========================================================

In order to properly compare the results, the previous transformation into the GMWM must be reverted. To do that, one must solve the equations in terms of the discrete-time model.

Converting from an AR1:

$\phi$:

$$\begin{align*}
  \phi  &= \exp \left( { - \frac{1}{ { {\tau _b} } }\Delta t} \right) \\
  {\tau _b}  &=  - \frac{ {\Delta t} }{ {\ln \left( \phi  \right)} }\\ 
\end{align*} $$

$\sigma_{AR}^2$:

$$\begin{align*}
  \sigma _{AR}^2 =  - \frac{ {\sigma _b^2{\tau _b} } }{2}\left[ {\exp \left( { - \frac{ {2\Delta t} }{ { {\tau _b} } } } \right) - 1} \right] \\
  \sigma _b^2  =  - \frac{ {2\sigma _{AR}^2} }{ { {\tau _b}\left[ {\exp \left( { - \frac{ {2\Delta t} }{ { {\tau _b} } } } \right) - 1} \right]} }
\end{align*} $$

Converting from WN:

$\sigma_{WN}^2$:

$$\begin{align*}
  \frac{1}{ {\Delta t} }\sigma _w^2 &= \sigma _{WN}^2 \\
  {\sigma ^2} &= \Delta t\sigma _{WN}^2 \\ 
\end{align*} $$

Simulation Code
===============

Within this section, the code used to power the simulation is used. The first part is a queuing file as the simulation was deployed to the Illinois Campus Cluster to obtain the results quickly. The second part is the simulation file itself.

Note, from the above equation manipulations, the values that will be used to generate the models are:

$AR1(\phi = 0.9999953, \sigma^2 = 3.2947445\times 10^{-15}) + WN(\sigma^2 = 4.528384\times 10^{-6})$

These values are generated in the "Conversion to GMWM Model Parameters"

PBS File
--------

``` bash
#!/bin/bash
#
## Set the maximum amount of runtime to 4 Hours (queue limit) 
## Note: The simulation finishes in an hour and 22 minutes
#PBS -l walltime=04:00:00
##
## Request one node with and one core
#PBS -l nodes=1:ppn=1
#PBS -l naccesspolicy=singleuser
## Name the job, queue in the secondary queue, and merge standard output into error output
#PBS -N gmwm_est
#PBS -q secondary
#PBS -j oe
#####################################

## Grab the job id from an environment variable and create a directory for the
## data output
export JOBID=`echo "$PBS_JOBID" | cut -d"[" -f1`
mkdir $PBS_O_WORKDIR/"$JOBID"

cd $PBS_O_WORKDIR/"$JOBID"

# Load R
module load R

## Run R script in batch mode without file output
R CMD BATCH --no-save --quiet --slave $HOME/gmwm/gmwm_comm.R
```

R Simulation Script
-------------------

``` r
# Auto install and load if necessary
inst_pkgs = load_pkgs = c("gmwm")
inst_pkgs = inst_pkgs[!(inst_pkgs %in% installed.packages()[,"Package"])]
if(length(inst_pkgs)) install.packages(inst_pkgs)

pkgs_loaded = lapply(load_pkgs, require, character.only=T)

# Control how many replications
B = 100

# Store results
results = matrix(NA, B, 4)

# Set RNG for Parallelization
RNGkind("L'Ecuyer-CMRG") 

# Values for Simulation
freq = 400
delta.t = 1/freq

tau = 5.308*10^2
sigma_b = 1.148*10^(-6)
sigma_w = 1.064*10^(-4)

# Conversion to GMWM Model Parameters
phi = exp(-1/tau * delta.t)
sigma_ar = -sigma_b^2*tau/2 * (exp(-2*delta.t/tau) - 1)
sigma_wn = 1/delta.t * sigma_w^2

# Model statement
mod = AR1(phi = phi, sigma2 = sigma_ar) + WN(sigma2 = sigma_wn)

for(i in 1:B){
  
  # Set a seed to reproduce error componentss
  set.seed(5567 + i)
  
  # Generate Data
  d = gen.gts(mod, 17280000)
  
  # Estimate
  o = gmwm.imu(mod, d)
  
  # Store results
  results[i,] = c(i, o$estimate[1,], o$estimate[2,], o$estimate[3,])
  
}

save(results, file="~/Desktop/res_gmwm_corr.rda")
write.csv(results, file="~/Desktop/res_gmwm_corr.csv", row.names = F)
```

Converting Simulation Results
=============================

Before observing the results, the transformation back into the discrete-time scale model must be performed. To do so, one must:

1.  Load in data obtained via simulation

``` r
# Set working directory
setwd("~/BoxSync/GMWM_project/ICC")

# Load in Data
load("res_gmwm_corr.rda")

# Create data.frame for ggplot2
d = data.frame(results)
names(d) =  c("ID","Phi","Sig_AR1","Sig_WN")
```

1.  Convert values to MLi model

``` r
# Calculate delta t
freq = 400
delta.t = 1/freq

# Calculate Tau values
Tau_b = -1*delta.t/log(d$Phi)

# Calculate Sigma_b values
Sig_b = sqrt(-2*d$Sig_AR1/(Tau_b*(exp(-2*delta.t/Tau_b) - 1)))

# Calculate Sigma_w values
Sig_w = sqrt(delta.t*d$Sig_WN)
```

Observing Simulation Results
============================

Below are the results from the parameter recovery simulation.

$\tau = 530.8$ parameter recovery

![Tau Parameter Recovery](/assets/images/posts/gmwm-simulation/tau_graph-1.png)
 
 $\sigma_b = 1.148\times 10^{-6}$ parameter recovery

![Sigma_b Parameter Recovery](/assets/images/posts/gmwm-simulation/sigb_graph-1.png)
 
 $\sigma_w = 1.064\times 10^{-4}$ parameter recovery

![Sigma_w Parameter Recovery](/assets/images/posts/gmwm-simulation/sigw_graph-1.png)
