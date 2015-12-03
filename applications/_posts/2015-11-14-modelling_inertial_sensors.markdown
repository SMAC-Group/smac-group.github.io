---
layout: landing
title:  "Modelling Inertial Sensors"
date:   2015-11-14 21:20:52
tags: 
- Modelling Inertial Sensors
- IMU
- GMWM
- Navigation
spic: "assets/images/site/cities/rome_reduced.jpg"
abstract: "GMWM-based IMU calibration"
---

# Intro
<p align="justify">
In the engineering domain focusing on navigation systems, an increasingly used instrument is the Inertial Measurement Unit (IMU) which is composed of a triad of gyroscopes (which, generally speaking, measure “angular rotation”) and a triad of accelerometers (which, generally speaking, measure acceleration). These sensors constitute the main component of inertial navigation systems which are used in a large range of applications including the navigation of aircrafts, robots, spacecrafts, submarines and ships. Recent advances in the construction of Micro-Electro-Mechanical System (MEMS) devices have made it possible to manufacture small and light IMUs which have a great potential for navigation (see e.g. El-Sheimy and Niu, 2007). These progresses have widened the range of possible applications and nowadays MEMS-IMUs are used, for example, in 3D input devices, robotics, virtual reality, vehicle stability control, human and animal motion capture and so forth
(Woodman, 2007).</p>
<p align="justify">
The correct identification and estimation of the error model of IMUs has been the object of great attention from the engineering community (see e.g. El-Sheimy et al., 2008). In this context the GMWM has been demonstrated to represent a considerable improvement compared to benchmark methods (see e.g. Stebler et al., 2014 for details).</p>


<p align="justify">

As an illustration, we also present here the results of an emulation study (see Stebler et al., 2014 for more details) where using extremely reliable equipments, the trajectory of an helicopter performing airborne laser scanning was precisely determined. From this trajectory, we computed the theoretical inertial measurements (i.e. accelerations and angular rotations) that should be observed along this trajectory. These perfect measurements were then corrupted using real IMU error (perviously obtained in static conditions). Then, these “pseudo” measurements were used together with the real GPS measurements to compute a trajectory. At one point, we introduced relatively short one-minute artificial gaps in GPS observations (in practice, such gaps are very common) and compared the deviations of the trajectories obtained with different inertial error models estimated. These error models were calculated using benchmark techniques in this field known as Allan variance and self-tuned approach (a detailed discussion on these methods can be found for example in Stebler et al., 2014) as well as the GMWM-based approach on previously collected inertial data. The trajectories are depicted in Figure 2 along with the “true” trajectory. It can be seen that the GMWM-based model
(black-dashed line) significantly limits the error growth during the GPS-signal outage compared to the other two benchmark methods, which diverged from the “true” trajectory by several thousand meters. This clearly indicates that the GMWM is able to estimate far more precisely the error models of such sensors compared to alternative techniques. The poor performances of these standard methods explains the recent explosion of the research conducted to determine the stochastic modeling of MEMS-type inertial sensors.</p>



# Papers

* Stebler, Y., Guerrier, S. & Skaloud, J., “An Approach for Observing and Modeling Errors in MEMS-based Inertial Sensors under Vehicle Dynamic”. IEEE Transactions on Instrumentation and Measurement, 2015. [Full text](/assets/pdfs/Modeling Errors in MEMS-Based Inertial Sensors.pdf)
* Stebler, Y., Guerrier, S., Skaloud, J. & Victoria-Feser, M.-P., “The Generalized Method of Wavelet Moments for Inertial Navigation Filter Design”, IEEE Transactions on Aerospace and Electronic Systems, 2014.[Full text](/assets/pdfs/The Generalized Method of Wavelet Moments for Inertial Navigation Filter Design.pdf)
* Guerrier, S., Skaloud, J., Waegli, A. & Victoria-Feser, M.-P., “Fault Detection and Isolation in Multiple MEMS-IMUs Configurations”, IEEE Transactions on Aerospace and Electronic Systems, 2012. [Full text](/assets/pdfs/Fault Detection and Isolation in Multiple MEMS-IMUs Configurationspdf.pdf)
* Stebler, Y., Guerrier, S., Skaloud, J. & Victoria-Feser, M.-P., “Constrained EM Algorithm for Stochastic Inertial Error Modelling: Study of Feasibility”, Journal of Measurement Science & Technology, 2011.[Full text](/assets/pdfs/Constrained EM algorithm for stochastic inertial error modeling.pdf)
* Waegli, A., Skaloud, J., Guerrier, S., Par ́es, M. & Colomina, I., “Noise Reduction and Estimation in Multiple Micro-Electro-Mechanical Inertial Systems”, Journal of Measurement Science & Technology, 2010. [Full text](/assets/pdfs/Noise reduction and estimation in multiple micro-electro-mechanical inertial systems.pdf)


# Proceedings
* Balamuta, J., Molinari, R., Guerrier, S. & Skaloud, J., “A Computationally Efficient Platform for Inertial Sensor Calibration”, in Proceedings of the ION GNSS 2015, Tampa, FL, USA, 2015.[Full Presentation](/assets/pdfs/gmwm_ion2015_part1.pdf)
* Molinari, R., Balamuta, J., Guerrier, S. & Skaloud, J., “Automatic and Computationally Efficient Method For Model Selection In Inertial Sensor Calibration”, in Proceedings of the ION GNSS 2015, Tampa, FL, USA, 2015. [Full Presentation](/assets/pdfs/gmwm_ion2015_part2.pdf)
* Stebler, Y., Guerrier, S., Skaloud, J., Molinari, R., & Victoria-Feser, M.-P., “Study of MEMS-based Inertial Sensors Operating in Dynamic Conditions”, in Proceedings of IEEE/ION PLANS 2014, Monterey, CA, USA, 2014.
* Guerrier, S., Molinari, Skaloud, J. & Victoria-Feser, M.-P., “An Algorithm for Auto- matic Inertial Sensors Calibration”, in Proceedings of the ION GNSS 2013, Nashville, TN, USA, 2013.
* Stebler, Y., Guerrier, S., Skaloud, J. & Victoria-Feser, M.-P., “A Framework for Inertial Sensor Calibration Using Complex Stochastic Error Models”, in Proceedings of IEEE/ION PLANS 2012, Myrtle Beach, SC, USA, 2012.
* Stebler, Y., Guerrier, S., Skaloud, J. & Victoria-Feser, M.-P., “Improving Modeling of MEMS-IMUs Operating in GNSS-denied Conditions”, in Proceedings of the ION GNSS 2011, Portland, OR, USA, 2011.
* Guerrier, S., Skaloud, J., Waegli, A. & Victoria-Feser, M.-P.,“Robust FDI in Redundant MEMS-IMUs Systems”, EuroCow, the Calibration and Orientation Workshop (Euro- pean Spatial Data Research), Barcelona, Spain, 2010.
* Guerrier, S., “Improving Accuracy with Multiple Sensors: Study of Redundant MEMS- IMU/GPS Configurations”, in Proceedings of the ION GNSS 2009, Savannah, GA, USA, 2009.
* Waegli, A., Guerrier, S. & Skaloud, J., “Redundant MEMS-IMU integrated with GPS for Performance Assessment in Sports”, in Proceedings of IEEE/ION PLANS 2008, Monterey, CA, USA, 2008.

# Software
