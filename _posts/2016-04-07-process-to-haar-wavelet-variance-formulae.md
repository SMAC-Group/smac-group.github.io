---
layout: post
title: Process to Haar Wavelet Variance Formulae
author: "James Balamuta"
categories: computing
date:   2016-05-23 01:22:52 -0500
tags: 
- Generalized Method of Wavelet Moments
- Wavelet Variance
- Time Series
- Haar Wavelet Filter
- Allan Variance
mathjax: true
---
  
The following equations are derivations used within the package as they relate to the Haar Wavelet Variance (WV) theoretical quantities. The initial WV formula, $$\nu _j^2$$, are used to calculate process to wavelet variance. The later are used within the asymptotic model selection calculations. 

The initial equations, marked by $$AVa{r_n}\left[ {X\left( t \right)} \right]$$, come from [*Allan variance of time series models for measurement data*](http://iopscience.iop.org/article/10.1088/0026-1394/45/5/009/meta) by Nien Fan Zhang published in Metrologia and [*Analysis and Modeling of Inertial Sensors Using Allan Variance*](http://ieeexplore.ieee.org/xpls/abs_all.jsp?arnumber=4404126&tag=1) by El-Sheimy, et. al. in IEEE Transactions on Instrumentation and Measurement. That is, these equations are derived using the Allan Variance (AV). The relationship between the Allan Variance to the Wavelet Variance is $$\frac{1}{2} AVa{r_n}\left[ {X\left( t \right)} \right] = \nu _j^2$$. Note, the $n$ used in the Allan Variance is equivalent to $$\frac{\tau_j}{2}$$.

The derivations below were done using [Mathematica](https://www.wolfram.com/mathematica/). The derivation file is available at: [http://smac-group.com/assets/supporting_docs/haar_analytical_derivatives_complete.nb](http://smac-group.com/assets/supporting_docs/haar_analytical_derivatives_complete.nb)

If you notice one of the derivations as being incorrected, please let us know via an issue at [https://github.com/smac-group/gmwm/issues](https://github.com/smac-group/gmwm/issues).

## White Noise
  
$$\begin{aligned}
AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{ {\sigma _X^2} }{n} \\
\nu _j^2\left( { {\sigma ^2} } \right) &= \frac{1}{2}\frac{ { {\sigma ^2} } }{ {\left( {\frac{ { {\tau _j} } }{2} } \right)} } \\
&= \frac{ { {\sigma ^2} } }{ { {\tau _j} } } \\ 
  \frac{\partial }{ {\partial {\sigma ^2} } }\nu _j^2\left( { {\sigma ^2} } \right) &= \frac{1}{ { {\tau _j} } } \\
  \frac{ { {\partial ^2} } }{ {\partial {\sigma ^4} } }\nu _j^2\left( { {\sigma ^2} } \right) &= 0  \\ 
\end{aligned}$$
  
## Random Walk
  
$$\begin{aligned}
AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{ {2{n^2} + 1} }{ {6n} }\sigma _a^2 \\
\nu _j^2\left( { {\gamma ^2} } \right) &= \frac{1}{2}\frac{ {\left( {2{ {\left( {\frac{ { {\tau _j} } }{2} } \right)}^2} + 1} \right){\gamma ^2} } }{ {6\left( {\frac{ { {\tau _j} } }{2} } \right)} } \\
&= \frac{ {\left( {\tau _j^2 + 2} \right){\gamma ^2} } }{ {12{\tau _j} } } \\
\frac{\partial }{ {\partial \gamma ^2} }\nu _j^2\left( { {\gamma ^2} } \right) &= \frac{ {\left( { {\tau _j^2} + 2} \right)} }{ {12\tau _j} } \\
\frac{\partial ^2 }{ {\partial \gamma ^4} }\nu _j^2\left( { {\gamma ^2} } \right) &= 0 \\
\end{aligned}$$


## Drift Process

$$\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{ { {n^2}{\omega ^2} } }{2} \\
  \nu _j^2\left( \omega  \right) &= \frac{1}{2}\frac{ { { {\left( {\frac{ { {\tau _j} } }{2} } \right)}^2}{\omega ^2} } }{2} \\
   &= \frac{ {\tau _j^2{\omega ^2} } }{ {16} } \\
  \frac{\partial }{ {\partial \omega } }\nu _j^2\left( \omega  \right) &= \frac{ {\tau _j^2\omega } }{8} \\
  \frac{ { {\partial ^2} } }{ {\partial {\omega ^2} } }\nu _j^2\left( \omega  \right) &= \frac{ {\tau _j^2} }{8} 
\end{aligned}$$

## Quantization Noise (QN)

$$\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{ {3{Q^2} } }{ { {n^2} } } \\
  \nu _j^2\left( Q^2 \right) &= \frac{1}{2}\frac{ {3{Q^2} } }{ { { {\left( {\frac{ { {\tau _j} } }{2} } \right)}^2} } } \\
   &= \frac{ {6{Q^2} } }{ {\tau _j^2} } \\ 
   \frac{\partial }{ {\partial Q^2} }{\nu _j^2}\left( Q^2  \right) &= \frac{6}{ { {\tau _j^2} } } \\
  \frac{ { {\partial ^2} } }{ {\partial Q^4} }{\nu _j^2}\left( Q^2  \right) &= 0
\end{aligned}$$

## AR 1 Process

$$\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{ {n - 3{\phi} - n\phi^2 + 4\phi^{n + 1} - \phi^{2n + 1} } }{ { {n^2}{ {\left( {1 - {\phi} } \right)}^2}\left( {1 - \phi^2} \right)} }\sigma _a^2 \\
  \nu _j^2\left( { {\phi},{\sigma ^2} } \right) &= \frac{1}{2}\frac{ {\left( {\left( {\frac{ { {\tau _j} } }{2} } \right) - 3{\phi} - \left( {\frac{ { {\tau _j} } }{2} } \right)\phi^2 + 4\phi^{\left( {\frac{ { {\tau _j} } }{2} } \right) + 1} - \phi^{2\left( {\frac{ { {\tau _j} } }{2} } \right) + 1} } \right){\sigma ^2} } }{ { { {\left( {\frac{ { {\tau _j} } }{2} } \right)}^2}{ {\left( {1 - {\phi} } \right)}^2}\left( {1 - \phi^2} \right)} } \\
   &= \frac{\sigma ^2 \left(\left(\phi ^2-1\right) \tau _j+2 \phi  \left(\phi ^{\tau _j}-4 \phi ^{\frac{\tau _j}{2} }+3\right)\right)}{(\phi -1)^3 (\phi +1) \tau _j^2}
\end{aligned}$$

**Derivatives w.r.t. $\phi$**

$$\begin{aligned}
  \frac{\partial }{ {\partial {\phi} } }\nu _j^2\left( { {\phi},{\sigma ^2} } \right) &= \frac{2 \sigma ^2 \left(\left(\phi ^2-1\right) \tau _j \left(\phi ^{\tau _j}-2 \phi ^{\frac{\tau _j}{2} }-\phi -1\right)-((3 \phi +2) \phi +1) \left(\phi ^{\tau _j}-4 \phi ^{\frac{\tau _j}{2} }+3\right)\right)}{(\phi -1)^4 (\phi +1)^2 \tau _j^2} \\ 
  \frac{\partial }{ {\partial \phi^2} }\nu _j^2\left( { {\phi},{\sigma ^2} } \right) &=  \frac{ {2{\sigma ^2} } }{ { { {(\phi  - 1)}^5}{ {(\phi  + 1)}^3}\tau _j^2} }\left( \begin{aligned}
  &\left( { {\phi ^2} - 1} \right){\tau _j}\left( {2((7\phi  + 4)\phi  + 1){\phi ^{\frac{ { {\tau _j} } }{2} - 1} } - ((7\phi  + 4)\phi  + 1){\phi ^{ {\tau _j} - 1} } + 3{ {(\phi  + 1)}^2} } \right) +  \\
  &{\left( { {\phi ^2} - 1} \right)^2}\tau _j^2\left( { {\phi ^{\frac{ { {\tau _j} } }{2} } } - 1} \right){\phi ^{\frac{ { {\tau _j} } }{2} - 1} } +  \\
  &4\left( { {\phi ^2} + \phi  + 1} \right)(3\phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) \\ 
\end{aligned}  \right)
\end{aligned}$$

**Derivatives w.r.t. $\sigma ^2$**

$$\begin{aligned}
  \frac{\partial }{ {\partial {\sigma ^2} } }{\nu ^2}(\tau ) &= \frac{\left(\phi ^2-1\right) \tau _j+2 \phi  \left(\phi ^{\tau _j}-4 \phi ^{\frac{\tau _j}{2} }+3\right)}{(\phi -1)^3 (\phi +1) \tau _j^2} \\
  \frac{\partial }{ {\partial {\sigma ^4} } }{\nu ^2}(\tau ) &= 0
\end{aligned}$$


**Derivative w.r.t both $\sigma ^2$ and $\phi$**

Here we opted to take the derivative w.r.t to $\sigma^2$ first and then $\phi$. The order of derivatives do not matter due to Clairaut's Theorem.

$$\frac{\partial }{ {\partial \phi } }\frac{\partial }{ {\partial {\sigma ^2} } }\nu _j^2\left( {\phi ,{\sigma ^2} } \right) = \frac{2 \left(\left(\phi ^2-1\right) \tau _j \left(\phi ^{\tau _j}-2 \phi ^{\frac{\tau _j}{2} }-\phi -1\right)-(\phi  (3 \phi +2)+1) \left(\phi ^{\tau _j}-4 \phi ^{\frac{\tau _j}{2} }+3\right)\right)}{(\phi -1)^4 (\phi +1)^2 \tau _j^2}
$$





## MA 1 Process

*>* **NOTE** For the MA(1) process listed in Zhang on Page 552, there is a sign error between equations (21) and (22). This has been corrected here. 

$$
\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \left( {1 + \theta^2} \right)\frac{ {\left( {n + \left( {2n - 3} \right)\frac{ { {\theta} } }{ {1 + \theta^2} } } \right)} }{ { {n^2} } }\sigma _a^2 \\
  \nu _j^2\left( { {\theta},{\sigma ^2} } \right) &= \frac{1}{2}\left( {1 + \theta^2} \right)\frac{ {\left( {\left( {\frac{ { {\tau _j} } }{2} } \right) + \left( {2\left( {\frac{ { {\tau _j} } }{2} } \right) - 3} \right)\frac{ { {\theta} } }{ {1 + \theta^2} } } \right)} }{ { { {\left( {\frac{ { {\tau _j} } }{2} } \right)}^2} } }{\sigma ^2} \\
   &= \frac{ {\left( { { {\left( { {\theta} + 1} \right)}^2}{\tau _j} - 6{\theta} } \right){\sigma ^2} } }{ {\tau _j^2} } 
\end{aligned}
$$


**Derivatives w.r.t $\theta$**

$$\begin{aligned}
  \frac{\partial }{ {\partial {\theta} } }\nu _j^2\left( { {\theta},{\sigma ^2} } \right) &= \frac{ { {\sigma ^2}\left( {2\left( { {\theta} + 1} \right){\tau _j} - 6} \right)} }{ {\tau _j^2} } \\
  \frac{\partial }{ {\partial \theta^2} }\nu _j^2\left( { {\theta},{\sigma ^2} } \right) &= \frac{ {2{\sigma ^2} } }{ { {\tau _j} } }
\end{aligned}$$


**Derivatives w.r.t. $\sigma ^2$**

$$\begin{aligned}
  \frac{\partial }{ {\partial {\sigma ^2} } }{\nu _j^2\left( { {\theta},{\sigma ^2} } \right)} &= \frac{ {\left( { { {\left( { {\theta} + 1} \right)}^2}{\tau _j} - 6{\theta} } \right)} }{ {\tau _j^2} } \\
  \frac{\partial }{ {\partial {\sigma ^4} } }{\nu _j^2\left( { {\theta},{\sigma ^2} } \right)} &= 0
\end{aligned}$$

**Derivative w.r.t both $\sigma ^2$ and $\theta$**

$$
\frac{\partial }{ {\partial \theta } }\frac{\partial }{ {\partial {\sigma ^2} } }\nu _j^2\left( {\theta ,{\sigma ^2} } \right) = \frac{ {2(\theta  + 1){\tau _j} - 6} }{ {\tau _j^2} }
$$


## ARMA(1,1)

*>* **NOTE** For the ARMA(1,1) process listed in Zhang on Page 553, he references [Time Series Analysis:
Forecasting and Control](http://www.wiley.com/WileyCDA/WileyTitle/productCd-0470272848.html) by Box G E P and Jenkins G M 1976 that contains an error when describing both the process variance and autocorrelation function (ACF).

In this case, the ARMA(1,1) process variance, $\gamma \left( 0 \right)$, and first autocovariance,$\gamma \left( 1 \right)$, is given by:

\[\begin{aligned}
  Var\left( {X\left( t \right)} \right) &= \gamma \left( 0 \right) \\
  &= {\sigma ^2}\frac{ {\left( {1 + 2\theta \phi  + {\theta ^2} } \right)} }{ {\left( {1 - {\phi ^2} } \right)} }  \\
  \gamma \left( 1 \right) &= {\sigma ^2}\frac{ {\left( {1 + \theta \phi } \right)\left( {\phi  + \theta } \right)} }{ {\left( {1 - {\phi ^2} } \right)} } 
\end{aligned} \]

And the ARMA(1,1)'s autocorrelation function (ACF) is given by:

\[\begin{aligned}
  \rho \left( 1 \right) &= \frac{ {\gamma \left( 1 \right)} }{ {\gamma \left( 0 \right)} } \\
  & = \frac{ {\left( {\phi  + \theta } \right)\left( {1 + \phi \theta } \right)} }{ {1 + 2\phi \theta  + {\theta ^2} } } \\
  \rho \left( k \right) &= {\phi ^{k - 1} }\rho \left( 1 \right)
\end{aligned} \]

for $k \ge 1$. 

With this in mind, we rederive the Allan Variance for an ARMA(1,1) using Equation 11 on page 551.

### ARMA(1,1) Derivation

We begin by stating Equation 11 on page 551:

$$  AVa{r_n}\left[ {X\left( t \right)} \right] = \frac{ {n\left( {1 - \rho \left( n \right)} \right) + \sum\limits_{i = 1}^{n - 1} {i\left( {2\rho \left( {n - i} \right) - \rho \left( i \right) - \rho \left( {2n - i} \right)} \right)} } }{ { {n^2} } }\sigma _X^2$$

**Aside:** To continue, we need to solve the series formulation using the recursive properties of ARMA(1,1)'s ACF.

$$\begin{aligned}
\sum\limits_{i = 1}^{n - 1} {i\left( {2\rho \left( {n - i} \right) - \rho \left( i \right) - \rho \left( {2n - i} \right)} \right)}  &= \rho \left( 1 \right)\sum\limits_{i = 1}^{n - 1} {i\left( {2{\phi ^{n - i - 1} } - {\phi ^{i - 1} } - {\phi ^{2n - i - 1} } } \right)} \\
   &= \rho \left( 1 \right)\left( {\frac{ { - {\phi ^{2n + 1} } + \left( {n{ {(\phi  - 1)}^2} + 4\phi } \right){\phi ^n} + \phi ( - 2n(\phi  - 1) - 3)} }{ { { {(\phi  - 1)}^2}\phi } } } \right)\\
   &= \frac{ {(\phi \theta  + 1)(\theta  + \phi )\left( { - {\phi ^{2n + 1} } + \left( {n{ {(\phi  - 1)}^2} + 4\phi } \right){\phi ^n} + \phi ( - 2n(\phi  - 1) - 3)} \right)} }{ { { {(\phi  - 1)}^2}\phi \left( { {\theta ^2} + 2\phi \theta  + 1} \right)} }
\end{aligned}$$

**Returning:** We substitute in to the first equation to obtain the Allan Variance for the ARMA(1,1) process.

$$\begin{aligned}
   &= \frac{ {n\left( {1 - {\phi ^{n - 1} }\frac{ {\left( {\phi  + \theta } \right)\left( {1 + \phi \theta } \right)} }{ {1 + 2\phi \theta  + {\theta ^2} } } } \right) + \frac{ {(\phi \theta  + 1)(\theta  + \phi )\left( { - {\phi ^{2n + 1} } + \left( {n{ {(\phi  - 1)}^2} + 4\phi } \right){\phi ^n} + \phi ( - 2n(\phi  - 1) - 3)} \right)} }{ { { {(\phi  - 1)}^2}\phi \left( { {\theta ^2} + 2\phi \theta  + 1} \right)} } } }{ { {n^2} } }\left( {\frac{ { {\sigma ^2}\left( { {\theta ^2} + 2\theta \phi  + 1} \right)} }{ {1 - {\phi ^2} } } } \right)\\
   &=  - \frac{ { {\sigma ^2}\left( {(\theta  + 1)n(\phi  - 1)(\theta (\phi  - 1) - \phi  - 2\phi \theta  - 1) - (\phi \theta  + 1)(\theta  + \phi )\left( { {\phi ^n} - 3} \right)\left( { {\phi ^n} - 1} \right)} \right)} }{ { {n^2}{ {(\phi  - 1)}^3}(\phi  + 1)} }
\end{aligned}$$


### ARMA(1,1) Process

$$\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &=  - \frac{ { {\sigma ^2}\left( {(\theta  + 1)n(\phi  - 1)(\theta (\phi  - 1) - \phi  - 2\phi \theta  - 1) - (\phi \theta  + 1)(\theta  + \phi )\left( { {\phi ^n} - 3} \right)\left( { {\phi ^n} - 1} \right)} \right)} }{ { {n^2}{ {(\phi  - 1)}^3}(\phi  + 1)} } \\
  \nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &=  - \frac{ { {\sigma ^2}\left( {(\theta  + 1)\left( {\frac{ { {\tau _j} } }{2} } \right)(\phi  - 1)(\theta (\phi  - 1) - \phi  - 2\phi \theta  - 1) - (\phi \theta  + 1)(\theta  + \phi )\left( { {\phi ^{\left( {\frac{ { {\tau _j} } }{2} } \right)} } - 3} \right)\left( { {\phi ^{\left( {\frac{ { {\tau _j} } }{2} } \right)} } - 1} \right)} \right)} }{ { { {\left( {\frac{ { {\tau _j} } }{2} } \right)}^2}{ {(\phi  - 1)}^3}(\phi  + 1)} }\left( {\frac{1}{2} } \right) \\
   &=  - \frac{ {2{\sigma ^2}\left( { - \frac{1}{2}{ {(\theta  + 1)}^2}\left( { {\phi ^2} - 1} \right){\tau _j} - (\theta  + \phi )(\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right)} }{ { { {(\phi  - 1)}^3}(\phi  + 1)\tau _j^2} } \\ 
\end{aligned} $$

**Derivative w.r.t $\phi$**:

$$\begin{aligned}
\frac{\partial }{ {\partial \phi } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &= \frac{ {2{\sigma ^2} } }{ { { {(\phi  - 1)}^4}{ {(\phi  + 1)}^2}\tau _j^2} }\left( \begin{aligned}
  &{\tau _j}\left( { - { {(\theta  + 1)}^2}(\phi  - 1){ {(\phi  + 1)}^2} - 2\left( { {\phi ^2} - 1} \right)(\theta  + \phi )(\theta \phi  + 1){\phi ^{\frac{ { {\tau _j} } }{2} - 1} } + \left( { {\phi ^2} - 1} \right)(\theta \phi  + 1)(\theta  + \phi ){\phi ^{ {\tau _j} - 1} } } \right) \\
   &- \left( { {\theta ^2}((3\phi  + 2)\phi  + 1) + 2\theta \left( {\left( { {\phi ^2} + \phi  + 3} \right)\phi  + 1} \right) + (3\phi  + 2)\phi  + 1} \right)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) \\ 
\end{aligned}  \right) \\
\frac{ { {\partial ^2} } }{ {\partial {\phi ^2} } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &= \frac{ {2{\sigma ^2} } }{ { { {(\phi  - 1)}^5}{ {(\phi  + 1)}^3}\tau _j^2} }\left( \begin{aligned}
  &{(\phi  - 1)^2}\left( { { {(\phi  + 1)}^2}\left( { {\theta ^2}\phi  + \theta {\phi ^2} + \theta  + \phi } \right)\tau _j^2\left( { {\phi ^{\frac{ { {\tau _j} } }{2} } } - 1} \right){\phi ^{\frac{ { {\tau _j} } }{2} - 2} } + \left( { {\phi ^2} - 1} \right)\left( { {\theta ^2}( - \phi ) + \theta \left( { {\phi ^2} + 4\phi  + 1} \right) - \phi } \right){\tau _j}\left( { {\phi ^{\frac{ { {\tau _j} } }{2} } } - 2} \right){\phi ^{\frac{ { {\tau _j} } }{2} - 2} } - 2{ {(\theta  - 1)}^2}\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right) \\
   &- 12{(\phi  + 1)^2}\left( { - \frac{1}{2}{ {(\theta  + 1)}^2}\left( { {\phi ^2} - 1} \right){\tau _j} - (\theta  + \phi )(\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right) \\
   &+ 6(\phi  + 1)(\phi  - 1)\left( {\frac{1}{2}{ {(\theta  + 1)}^2}\left( { {\phi ^2} - 1} \right){\tau _j} + (\theta  + \phi )(\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) + (\phi  + 1)\left( { - (\theta  + \phi )(\theta \phi  + 1){\tau _j}\left( { {\phi ^{\frac{ { {\tau _j} } }{2} } } - 2} \right){\phi ^{\frac{ { {\tau _j} } }{2} - 1} } - \theta (\theta  + \phi )\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) - (\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) - { {(\theta  + 1)}^2}\phi {\tau _j} } \right)} \right) \\ 
\end{aligned}  \right)
\end{aligned}$$


**Derivative w.r.t $\theta$:**

$$\begin{aligned}
  \frac{\partial }{ {\partial \theta } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &= \frac{ {2{\sigma ^2}\left( {(\theta  + 1)\left( { {\phi ^2} - 1} \right){\tau _j} + \left( {2\theta \phi  + {\phi ^2} + 1} \right)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right)} }{ { { {(\phi  - 1)}^3}(\phi  + 1)\tau _j^2} } \\
  \frac{ { {\partial ^2} } }{ {\partial {\theta ^2} } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &= \frac{ {2{\sigma ^2}\left( {\left( { {\phi ^2} - 1} \right){\tau _j} + 2\phi \left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right)} }{ { { {(\phi  - 1)}^3}(\phi  + 1)\tau _j^2} } \\
\end{aligned}$$

**Derivative w.r.t. $\sigma^2$:**

$$\begin{aligned}
\frac{\partial }{ {\partial \sigma ^2 } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &= \frac{2 \sigma ^2 \left(\left(\phi ^2-1\right) \tau _j+2 \phi  \left(\phi ^{\tau _j}-4 \phi ^{\frac{\tau _j}{2} }+3\right)\right)}{(\phi -1)^3 (\phi +1) \tau _j^2} \\
\frac{ { {\partial ^2} } }{ {\partial {\sigma ^4} } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) &= 0 
\end{aligned}$$


**Derivative w.r.t. $\phi$ and $\sigma^2$:**

$$\frac{\partial }{ {\partial \phi } }\frac{\partial }{ {\partial {\sigma ^2} } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) = \frac{2}{ { { {(\phi  - 1)}^4}{ {(\phi  + 1)}^2}\tau _j^2} }\left( \begin{aligned}
   &- (\phi  - 1)(\phi  + 1)\left( \begin{aligned}
   &- (\theta  + \phi )(\theta \phi  + 1){\tau _j}\left( { {\phi ^{\frac{ { {\tau _j} } }{2} } } - 2} \right){\phi ^{\frac{ { {\tau _j} } }{2} - 1} } \\
   &- \theta (\theta  + \phi )\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) \\
   &- (\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) \\
   &- {(\theta  + 1)^2}\phi {\tau _j} \\ 
\end{aligned}  \right) \\
   &+ (\phi  - 1)\left( { - \frac{1}{2}{ {(\theta  + 1)}^2}\left( { {\phi ^2} - 1} \right){\tau _j} - (\theta  + \phi )(\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right) \\
   &+ 3(\phi  + 1)\left( { - \frac{1}{2}{ {(\theta  + 1)}^2}\left( { {\phi ^2} - 1} \right){\tau _j} - (\theta  + \phi )(\theta \phi  + 1)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right) \\ 
\end{aligned}  \right)$$

**Derivative w.r.t. $\theta$ and $\sigma^2$:**

$$\frac{\partial }{ {\partial \theta } }\frac{\partial }{ {\partial {\sigma ^2} } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) = \frac{2}{ { { {(\phi  - 1)}^3}(\phi  + 1)\tau _j^2} }\left( {(\theta  + 1)\left( { {\phi ^2} - 1} \right){\tau _j} + \left( {2\theta \phi  + {\phi ^2} + 1} \right)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right)} \right)$$


**Derivative w.r.t. $\theta$ and $\phi$:**

$$\frac{\partial }{ {\partial \theta } }\frac{\partial }{ {\partial \phi } }\nu _j^2\left( {\phi ,\theta ,{\sigma ^2} } \right) =  - \frac{ {2{\sigma ^2} } }{ { { {(\phi  - 1)}^4}{ {(\phi  + 1)}^2}\tau _j^2} }\left( \begin{aligned}
  &{\tau _j}\left( \begin{aligned}
  &2(\theta  + 1)(\phi  - 1){(\phi  + 1)^2} \\
   &+ 2\left( { {\phi ^2} - 1} \right)\left( {2\theta \phi  + {\phi ^2} + 1} \right){\phi ^{\frac{ { {\tau _j} } }{2} - 1} } \\
   &- \left( { {\phi ^2} - 1} \right)\left( {2\theta \phi  + {\phi ^2} + 1} \right){\phi ^{ {\tau _j} - 1} } \\ 
\end{aligned}  \right) \\
   &+ 2\left( {\theta (\phi (3\phi  + 2) + 1) + \phi \left( { {\phi ^2} + \phi  + 3} \right) + 1} \right)\left( { {\phi ^{ {\tau _j} } } - 4{\phi ^{\frac{ { {\tau _j} } }{2} } } + 3} \right) \\ 
\end{aligned}  \right)$$

