The following equations are derivations used within the package as they relate to the Haar Wavelet Variance (WV) theoretical quantities. The initial WV formula, \(\nu _j^2\), are used to calculate process to wavelet variance. The later are used within the asymptotic model selection calculations.

The initial equations, marked by \(AVa{r_n}\left[ {X\left( t \right)} \right]\), come from *Allan variance of time series models for measurement data* by Nien Fan Zhang published in Metrologia and *Analysis and Modeling of Inertial Sensors Using Allan Variance* by El-Sheimy, et. al. in IEEE Transactions on Instrumentation and Measurement. That is, these equations are derived using the Allan Variance. The relationship between the Allan variance to the Wavelet Variance is \(\frac{1}{2} AVa{r_n}\left[ {X\left( t \right)} \right] = \nu _j^2\). Note, the \(n\) used in the Allan variance is equivalent to \(\frac{\tau_j}{2}\).

The derivations below were done using [Mathematica](https://www.wolfram.com/mathematica/). The derivation file is available at: <http://smac-group.com/supporting_docs/haar_analytical_derivatives_complete.nb>

If you notice one of the derivations as being incorrected, please let us know via an issue at <https://github.com/smac-group/gmwm/issues>.

**White Noise:**

\[\begin{aligned}
AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{{\sigma _X^2}}{n} \\
\nu _j^2\left( {{\sigma ^2}} \right) &= \frac{1}{2}\frac{{{\sigma ^2}}}{{\left( {\frac{{{\tau _j}}}{2}} \right)}} \\
&= \frac{{{\sigma ^2}}}{{{\tau _j}}} \\ 
\nu _j^2\left( {{\sigma ^2}} \right)  &= \frac{1}{\tau _j} \\
\nu _j^2\left( {{\sigma ^2}} \right)  &= 0 \\
\end{aligned}\]

**Random Walk:**

\[\begin{aligned}
AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{{2{n^2} + 1}}{{6n}}\sigma _a^2 \\
\nu _j^2\left( {{\gamma ^2}} \right) &= \frac{1}{2}\frac{{2{{\left( {\frac{{{\tau _j}}}{2}} \right)}^2} + 1}}{{\left( {\frac{{{\tau _j}}}{2}} \right)n}}{\gamma ^2} \\
&= \frac{{\left( {\tau _j^2 + 2} \right){\gamma ^2}}}{{12{\tau _j}}} \\
\frac{\partial }{{\partial \gamma ^2}}\nu _j^2\left( {{\gamma ^2}} \right) &= \frac{{\left( {{\tau _j^2} + 2} \right)}}{{12\tau _j^2 }} \\
\frac{\partial ^2 }{{\partial \gamma ^4}}\nu _j^2\left( {{\gamma ^2}} \right) &= 0 \\
\end{aligned}\]

**Drift Process:**

\[\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{{{n^2}{\omega ^2}}}{2} \\
  \nu _j^2\left( \omega  \right) &= \frac{1}{2}\frac{{{{\left( {\frac{{{\tau _j}}}{2}} \right)}^2}{\omega ^2}}}{2} \\
   &= \frac{{\tau _j^2{\omega ^2}}}{{16}} \\
  \frac{\partial }{{\partial {\omega ^2}}}{\nu _j^2}(\omega ) &= \frac{{{\tau _j^2}}}{{16}}\\
  \frac{\partial }{{\partial {\omega ^4}}}{\nu _j^2}(\omega ) &= 0
\end{aligned}\]

**Quantization Noise (QN):**

\[\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{{3{Q^2}}}{{{n^2}}} \\
  \nu _j^2\left( \omega  \right) &= \frac{1}{2}\frac{{3{Q^2}}}{{{{\left( {\frac{{{\tau _j}}}{2}} \right)}^2}}} \\
   &= \frac{{6{Q^2}}}{{\tau _j^2}} \\ 
   \frac{\partial }{{\partial Q_0^2}}{\nu _j^2}\left( \tau  \right) &= \frac{6}{{{\tau _j^2}}} \\
  \frac{{{\partial ^2}}}{{\partial Q_0^4}}{\nu _j^2}\left( \tau  \right) &= 0
\end{aligned}\]

**AR 1 Process:**

\[\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{{n - 3{\phi _1} - n\phi _1^2 + 4\phi _1^{n + 1} - \phi _1^{2n + 1}}}{{{n^2}{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)}}\sigma _a^2 \\
  \nu _j^2\left( {{\phi _1},{\sigma ^2}} \right) &= \frac{1}{2}\frac{{\left( {\left( {\frac{{{\tau _j}}}{2}} \right) - 3{\phi _1} - \left( {\frac{{{\tau _j}}}{2}} \right)\phi _1^2 + 4\phi _1^{\left( {\frac{{{\tau _j}}}{2}} \right) + 1} - \phi _1^{2\left( {\frac{{{\tau _j}}}{2}} \right) + 1}} \right){\sigma ^2}}}{{{{\left( {\frac{{{\tau _j}}}{2}} \right)}^2}{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)}} \\
   &= \frac{{\left( {{\tau _j} - 3{\phi _1} - \left( {\frac{{{\tau _j}}}{2}} \right)\phi _1^2 + 4\phi _1^{\left( {\frac{{{\tau _j}}}{2}} \right) + 1} - \phi _1^{{\tau _j} + 1}} \right){\sigma ^2}}}{{\left( {\frac{{\tau _j^2}}{2}} \right){{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)}} \\ 
\end{aligned}\]

**Derivatives w.r.t. \(\phi\)**

\[\begin{aligned}
  \frac{\partial }{{\partial {\phi _1}}}\nu _j^2\left( {{\phi _1},{\sigma ^2}} \right) &= \frac{{2{\sigma ^2}\left( {4\left( {\frac{{{\tau _j}}}{2} + 1} \right)\phi _1^{\frac{{{\tau _j}}}{2}} - \left( {{\tau _j} + 1} \right)\phi _1^{{\tau _j}} - {\phi _1}{\tau _j} - 3} \right)}}{{{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)\tau _j^2}}   \\
  &+ \frac{{4{\sigma ^2}\left( {4\phi _1^{\frac{{{\tau _j}}}{2} + 1} - \phi _1^{{\tau _j} + 1} - \frac{1}{2}\phi _1^2{\tau _j} + \frac{{{\tau _j}}}{2} - 3{\phi _1}} \right)}}{{{{\left( {1 - {\phi _1}} \right)}^3}\left( {1 - \phi _1^2} \right)\tau _j^2}}   \\
  &+ \frac{{4{\sigma ^2}{\phi _1}\left( {4\phi _1^{\frac{{{\tau _j}}}{2} + 1} - \phi _1^{{\tau _j} + 1} - \frac{1}{2}\phi _1^2{\tau _j} + \frac{{{\tau _j}}}{2} - 3{\phi _1}} \right)}}{{{{\left( {1 - {\phi _1}} \right)}^2}{{\left( {1 - \phi _1^2} \right)}^2}\tau _j^2}} \\ 
  \frac{\partial }{{\partial \phi _1^2}}\nu _j^2\left( {{\phi _1},{\sigma ^2}} \right) &= \frac{{2{\sigma ^2}}}{{\tau _j^2}}\left( \begin{aligned}
  &\frac{{2\left( {\frac{{{\tau _j}}}{2} + 1} \right){\tau _j}\phi _1^{\frac{{{\tau _j}}}{2} - 1} - {\tau _j}\left( {{\tau _j} + 1} \right)\phi _1^{{\tau _j} - 1} - {\tau _j}}}{{{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)}} \\
   +& \left( {\frac{{8{\phi _1}}}{{{{\left( {1 - {\phi _1}} \right)}^3}{{\left( {1 - \phi _1^2} \right)}^2}}} + \frac{{\frac{{8\phi _1^2}}{{{{\left( {1 - \phi _1^2} \right)}^3}}} + \frac{2}{{{{\left( {1 - \phi _1^2} \right)}^2}}}}}{{{{\left( {1 - {\phi _1}} \right)}^2}}} + \frac{6}{{{{\left( {1 - {\phi _1}} \right)}^4}\left( {1 - \phi _1^2} \right)}}} \right)\left( {4\phi _1^{\frac{{{\tau _j}}}{2} + 1} - \phi _1^{{\tau _j} + 1} - \frac{1}{2}\phi _1^2{\tau _j} + \frac{{{\tau _j}}}{2} - 3{\phi _1}} \right) \\
   +& 2\left( {\frac{{2{\phi _1}}}{{{{\left( {1 - {\phi _1}} \right)}^2}{{\left( {1 - \phi _1^2} \right)}^2}}} + \frac{2}{{{{\left( {1 - {\phi _1}} \right)}^3}\left( {1 - \phi _1^2} \right)}}} \right)\left( {4\left( {\frac{{{\tau _j}}}{2} + 1} \right)\phi _1^{\frac{{{\tau _j}}}{2}} - \left( {{\tau _j} + 1} \right)\phi _1^{{\tau _j}} - {\phi _1}{\tau _j} - 3} \right) \\ 
\end{aligned}  \right)
\end{aligned}\]

**Derivatives w.r.t. \(\sigma^2\)**

\[\begin{aligned}
  \frac{\partial }{{\partial {\sigma ^2}}}{\nu ^2}(\tau ) &= \frac{{\frac{\tau }{2} - 3\phi  - \frac{{\tau {\phi ^2}}}{2} + 4{\phi ^{\frac{\tau }{2} + 1}} - {\phi ^{\tau  + 1}}}}{{\frac{{{\tau ^2}}}{2}{{(1 - \phi )}^2}(1 - {\phi ^2})}}\\
  \frac{\partial }{{\partial {\sigma ^4}}}{\nu ^2}(\tau ) &= 0
\end{aligned}\]

*&gt;* **NOTE** For the MA(1) process listed in Zhang on Page 552, there is a sign error between equations (21) and (22). This has been corrected here.

**MA 1 process:** \[
\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \left( {1 + \theta _1^2} \right)\frac{{\left( {n + \left( {2n - 3} \right)\frac{{{\theta _1}}}{{1 + \theta _1^2}}} \right)}}{{{n^2}}}\sigma _a^2 \\
  \nu _j^2\left( {{\theta _1},{\sigma ^2}} \right) &= \frac{1}{2}\left( {1 + \theta _1^2} \right)\frac{{\left( {\left( {\frac{{{\tau _j}}}{2}} \right) + \left( {2\left( {\frac{{{\tau _j}}}{2}} \right) - 3} \right)\frac{{{\theta _1}}}{{1 + \theta _1^2}}} \right)}}{{{{\left( {\frac{{{\tau _j}}}{2}} \right)}^2}}}{\sigma ^2} \\
   &= \frac{{\left( {{{\left( {{\theta _1} + 1} \right)}^2}{\tau _j} - 6{\theta _1}} \right){\sigma ^2}}}{{\tau _j^2}} 
\end{aligned}
\]

**Derivatives w.r.t \(\theta\)** \[\begin{aligned}
  \frac{\partial }{{\partial {\theta _1}}}\nu _j^2\left( {{\theta _1},{\sigma ^2}} \right) &= \frac{{{\sigma ^2}\left( {2\left( {{\theta _1} + 1} \right){\tau _j} - 6} \right)}}{{\tau _j^2}} \\
  \frac{\partial }{{\partial \theta _1^2}}\nu _j^2\left( {{\theta _1},{\sigma ^2}} \right) &= \frac{{2{\sigma ^2}}}{{{\tau _j}}}
\end{aligned}\]

**Derivatives w.r.t. \(\sigma^2\)**

\[\begin{aligned}
  \frac{\partial }{{\partial {\sigma ^2}}}{\nu _j^2\left( {{\theta _1},{\sigma ^2}} \right)} &= \frac{{\left( {{{\left( {{\theta _1} + 1} \right)}^2}{\tau _j} - 6{\theta _1}} \right)}}{{\tau _j^2}} \\
  \frac{\partial }{{\partial {\sigma ^4}}}{\nu _j^2\left( {{\theta _1},{\sigma ^2}} \right)} &= 0
\end{aligned}\]

**ARMA(1,1) Process:**

\[\begin{aligned}
  AVa{r_n}\left[ {X\left( t \right)} \right] &= \frac{{\left( {n{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - 2{\phi _1}{\theta _1} + \theta _1^2} \right) + \left( {{\phi _1} - {\theta _1}} \right)\left( {1 - {\phi _1}{\theta _1}} \right)\left( {2n - 3 - 2n{\phi _1} + 4\phi _1^n - \phi _1^{2n}} \right)} \right){\sigma ^2}}}{{{n^2}{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)}} \\
  \nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= \frac{1}{2}\frac{{\left( {\left( {\frac{{{\tau _j}}}{2}} \right){{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - 2{\phi _1}{\theta _1} + \theta _1^2} \right) + \left( {{\phi _1} - {\theta _1}} \right)\left( {1 - {\phi _1}{\theta _1}} \right)\left( {2\left( {\frac{{{\tau _j}}}{2}} \right) - 3 - 2\left( {\frac{{{\tau _j}}}{2}} \right){\phi _1} + 4\phi _1^{\left( {\frac{{{\tau _j}}}{2}} \right)} - \phi _1^{2\left( {\frac{{{\tau _j}}}{2}} \right)}} \right)} \right){\sigma ^2}}}{{{{\left( {\frac{{{\tau _j}}}{2}} \right)}^2}{{\left( {1 - {\phi _1}} \right)}^2}\left( {1 - \phi _1^2} \right)}} \\
   &= \frac{{2{\sigma ^2}\left( {\frac{1}{2}{{\left( {{\phi _1} - 1} \right)}^2}\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} - \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right)}}{{{{\left( {{\phi _1} - 1} \right)}^2}\left( {1 - \phi _1^2} \right)\tau _j^2}} \\ 
\end{aligned}
\]

**Derivative w.r.t.\(\sigma^2\):**

\[\begin{aligned}
  \frac{\partial }{{\partial {\sigma ^2}}}\nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= \frac{{2\left( {\frac{1}{2}{{\left( {{\phi _1} - 1} \right)}^2}\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} - \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right)}}{{{{\left( {{\phi _1} - 1} \right)}^2}\left( {1 - \phi _1^2} \right)\tau _j^2}} \\
  \frac{\partial }{{\partial {\sigma ^4}}}\nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= 0 \\
\end{aligned} \]

**Derivative w.r.t \(\theta _1\):**

\[\begin{aligned}
  \frac{\partial }{{\partial {\theta _1}}}\nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= \frac{{2{\sigma ^2}\left( {\frac{1}{2}{{\left( {{\phi _1} - 1} \right)}^2}\left( {2{\theta _1} - 2{\phi _1}} \right){\tau _j} - {\phi _1}\left( {{\theta _1} - {\phi _1}} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right) - \left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right)}}{{{{\left( {{\phi _1} - 1} \right)}^2}\left( {1 - \phi _1^2} \right)\tau _j^2}} \\
  \frac{\partial }{{\partial \theta _1^2}}\nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= \frac{{2{\sigma ^2}\left( {{{\left( {{\phi _1} - 1} \right)}^2}{\tau _j} - 2{\phi _1}\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right)}}{{{{\left( {{\phi _1} - 1} \right)}^2}\left( {1 - \phi _1^2} \right)\tau _j^2}} \\ 
\end{aligned}\]

**Derivative w.r.t \(\phi _1\)**:

\[\begin{aligned}
  \frac{\partial }{{\partial {\phi _1}}}\nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= \frac{{4{\sigma ^2}{\phi _1}\left( {\frac{1}{2}{{\left( {{\phi _1} - 1} \right)}^2}\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} - \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right)}}{{{{\left( {{\phi _1} - 1} \right)}^2}{{\left( {1 - \phi _1^2} \right)}^2}\tau _j^2}} \\
   &- \frac{{4{\sigma ^2}\left( {\frac{1}{2}{{\left( {{\phi _1} - 1} \right)}^2}\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} - \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right)}}{{{{\left( {{\phi _1} - 1} \right)}^3}\left( {1 - \phi _1^2} \right)\tau _j^2}} \\
   &+ \frac{{2{\sigma ^2}\left( \begin{aligned}
   &- {\theta _1}{\left( {{\phi _1} - 1} \right)^2}{\tau _j} + \left( {{\phi _1} - 1} \right)\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} \\
   &- \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 2{\tau _j}\phi _1^{\frac{{{\tau _j}}}{2} - 1} + {\tau _j}\phi _1^{{\tau _j} - 1} + {\tau _j}} \right) \\
   &- {\theta _1}\left( {{\theta _1} - {\phi _1}} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right) \\
   &+ \left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right) \\ 
\end{aligned}  \right)}}{{{{\left( {{\phi _1} - 1} \right)}^2}\left( {1 - \phi _1^2} \right)\tau _j^2}} \\
   \\
   \\
  \frac{\partial }{{\partial \phi _1^2}}\nu _j^2\left( {{\theta _1},{\phi _1},{\sigma ^2}} \right) &= \frac{{2{\sigma ^2}}}{{\tau _j^2}}\left( \begin{aligned}
  &2\left( {\frac{{2{\phi _1}}}{{{{\left( {{\phi _1} - 1} \right)}^2}{{\left( {1 - \phi _1^2} \right)}^2}}} - \frac{2}{{{{\left( {{\phi _1} - 1} \right)}^3}\left( {1 - \phi _1^2} \right)}}} \right)\left( \begin{aligned}
   &- {\theta _1}{\left( {{\phi _1} - 1} \right)^2}{\tau _j} + \left( {{\phi _1} - 1} \right)\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} - \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 2{\tau _j}\phi _1^{\frac{{{\tau _j}}}{2} - 1} + {\tau _j}\phi _1^{{\tau _j} - 1} + {\tau _j}} \right) \\
   &- {\theta _1}\left( {{\theta _1} - {\phi _1}} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right) + \left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right) \\ 
\end{aligned}  \right) \\
   &+ \left( { - \frac{{8{\phi _1}}}{{{{\left( {{\phi _1} - 1} \right)}^3}{{\left( {1 - \phi _1^2} \right)}^2}}} + \frac{{\frac{{8\phi _1^2}}{{{{\left( {1 - \phi _1^2} \right)}^3}}} + \frac{2}{{{{\left( {1 - \phi _1^2} \right)}^2}}}}}{{{{\left( {{\phi _1} - 1} \right)}^2}}} + \frac{6}{{{{\left( {{\phi _1} - 1} \right)}^4}\left( {1 - \phi _1^2} \right)}}} \right)\left( \begin{aligned}
  &\frac{1}{2}{\left( {{\phi _1} - 1} \right)^2}\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right){\tau _j} \\
   &- \left( {{\theta _1} - {\phi _1}} \right)\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right) \\ 
\end{aligned}  \right) \\
   &+ \frac{1}{{{{\left( {{\phi _1} - 1} \right)}^2}\left( {1 - \phi _1^2} \right)}}\left( \begin{aligned}
  &\frac{1}{2}\left( {2\left( { - 2{\theta _1}{\phi _1} + \theta _1^2 + 1} \right) - 8{\theta _1}\left( {{\phi _1} - 1} \right)} \right){\tau _j} \\
   &- \left( {{\theta _1} - {\phi _1}} \right)\left( {\left( {{\theta _1}{\phi _1} - 1} \right)\left( {\left( {{\tau _j} - 1} \right){\tau _j}\phi _1^{{\tau _j} - 2} - 2\left( {\frac{{{\tau _j}}}{2} - 1} \right){\tau _j}\phi _1^{\frac{{{\tau _j}}}{2} - 2}} \right) + 2{\theta _1}\left( { - 2{\tau _j}\phi _1^{\frac{{{\tau _j}}}{2} - 1} + {\tau _j}\phi _1^{{\tau _j} - 1} + {\tau _j}} \right)} \right) \\
   &+ 2\left( {\left( {{\theta _1}{\phi _1} - 1} \right)\left( { - 2{\tau _j}\phi _1^{\frac{{{\tau _j}}}{2} - 1} + {\tau _j}\phi _1^{{\tau _j} - 1} + {\tau _j}} \right) + {\theta _1}\left( { - 4\phi _1^{\frac{{{\tau _j}}}{2}} + \phi _1^{{\tau _j}} + \left( {{\phi _1} - 1} \right){\tau _j} + 3} \right)} \right) \\ 
\end{aligned}  \right) \\ 
\end{aligned}  \right) \\ 
\end{aligned} \]
