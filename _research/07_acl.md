---
title: "Automated Camera-Based Estimation of Rehabilitation Criteria Following ACL Reconstruction"
image: 
  path: /assets/images/legpress_wide2.png
  thumbnail: /assets/images/legpress_crop.png
  caption: "ACL"
---

Assessing ACL reconstruction rehabilitation from camera data using markerless pose estimation.

## Publication
["Automated Camera-Based Estimation of Rehabilitation Criteria Following ACL Reconstruction."](https://arxiv.org/abs/2002.01591) (Choong Hee Kim, Shannon M. Danforth, **Patrick Holmes**, Daphna Raz, Darlene Yao, Asheesh Bedi, Ram Vasudevan), arXiv preprint, 2018.

## Abstract
Anterior cruciate ligament (ACL) reconstruction necessitates months of rehabilitation, during which a clinician evaluates whether a patient is ready to return to sports or occupation.
Due to their time- and cost-intensive nature, these screenings to assess progress are unavailable to many.
This paper introduces an automated, markerless, camera-based method for estimating rehabilitation criteria following ACL reconstruction.
To evaluate the performance of this novel technique, data were collected weekly from 12 subjects as they used a leg press over the course of a 12-week rehabilitation period. 
The proposed camera-based method for estimating displacement and force was compared to encoder and force plate measurements.
The leg press displacement and force values were estimated with 89.7% and 85.3% accuracy, respectively. These values were then used to calculate lower-limb symmetry and to track patient progress over time.

## Video
Supplementary video for our ICRA 2019 submission about assessing ACL reconstruction rehabilitation using markerless pose estimation.
<div class="youtube-video-container">
<iframe class="youtube-video" src="https://www.youtube.com/embed/rPyNj4e7bC8" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Figures

![intro_fig](/assets/images/ACL/ICRA_figure_intro.png)
This paper employs a camera-based pose estimation algorithm to automatically estimate rehabilitation criteria for 12 ACL-reconstructed patients over the course of a 12-week study. (a) A stereo camera was used to collect video of participants performing a leg press exercise.
A pose estimation algorithm estimated the positions of each of the participant's joints, depicted as a skeleton figure.
(b, c, d) The estimated positions of the shank, thigh, and trunk are plotted at the beginning, middle, and end of a single leg press repetition, respectively.
(e) The estimated force on the foot plate, which can be used to evaluate rate of recovery after an ACL reconstruction, (gray line) is plotted over time, with the vertical black lines corresponding to the times at which (b, c, and d) are plotted.}

![data_collection](/assets/images/ACL/final_datacollection.png)
Setup for data collection, including instrumented leg press with force plate, encoder, and LED indicator to signal when a patient is at $90$ degrees. Video was recorded using a wall-mounted stereo camera (not pictured).

![leg_press_fbd](/assets/images/ACL/legPressFBD_2D.png)
Free body diagram of the entire leg press system.

![estimation](/assets/images/ACL/estimation.png)
(a) Leg press displacement estimation (red line) versus measured (gray line) during the leg press test. (b) Leg press force plate value estimation (blue line) versus measured (gray line). 