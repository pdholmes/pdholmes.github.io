---
title: "Predicting Sagittal-Plane Swing Hip Kinematics in Response to Trips"
image: 
  path: /assets/images/trip_prediction/trip_prediction_wide.png
  thumbnail: /assets/images/trip_prediction/trip_prediction.png
  caption: "trip_prediction"
---

A Gaussian Process Regression model is validated using data from a 16-subject tripping experiment.

## Publication

["Predicting Sagittal-Plane Swing Hip Kinematics in Response to Trips."](https://ieeexplore.ieee.org/abstract/document/9799740) (Shannon M. Danforth, Xinyi Liu, Martin J. Ward, **Patrick D. Holmes**, Ram Vasudevan), in IEEE Robotics and Automation Letters, 2022. **Best RA-L Paper Award, BioRob 2022.**

## Abstract

State-of-the-art wearable lower-limb robot controllers typically use established baseline human kinematics during common mobility tasks.
Unfortunately due to the variability in human response during perturbations, these lower-limb controllers are unable to effectively assist with perturbation recovery.
Accurate and quick predictions of kinematic responses to unexpected disturbances during motion can help assistive robotic devices safely aid with an individual's recovery.
This paper presents three methods for predicting swing hip kinematics during trip recovery: a Gaussian process regression (GPR) model; a time-series neural network; and a pendulum model with linear feedback. 
Data were collected in an experiment where 16 subjects were tripped at random percentages of swing phase.
The three prediction methods were applied to these data and evaluated for simulation accuracy and computation time.
Both subject-specific and generalized models were investigated.
Results indicate that the GPR model is the best choice for kinematic predictions due to its low simulation error in both subject-specific and generalized cases and lowest computation time.

## Figures

![intro_fig](/assets/images/trip_prediction/biorob_intro_fig.png)
This paper develops and compares predictions of sagittal-plane swing hip kinematics after a trip occurs. The three hip states of interest (height, anterior-posterior position, and flexion-extension angle) are shown in blue to the left. On the right, the stick figures show an example of one subject's trip-recovery response from our experiment. Note that the knee location is determined by the hip flexion-extension angle and thus is plotted in addition to the hip positions. The black line shows the ground truth hip and knee locations, and the pink line shows the predicted response from our Gaussian process regression model.

![trip_exp_strategies](/assets/images/trip_prediction/trip_exp_strategies.png)
Our experiment introduced trips via tethers attached to subjects' feet. (a) shows the trip experiment setup, including tethers attached to each foot, brakes applied at short intervals, and load cells to measure the tether force. (b) illustrates the swing leg during each strategy, adapted from Shirota et al. 2014. (c) shows example swing heel heights for one subject during each type of recovery compared to nominal data

![hip_states](/assets/images/trip_prediction/hip_states.png)
Hip flexion-extension angle, height, and anterior-posterior (AP) position relative to the stance foot, plotted for the elevating, delayed lowering, and lowering strategies in orange, green, and purple, respectively.
The thick black lines show the average nominal hip states.
These data are from one subject in our dataset.

![results_fig](/assets/images/trip_prediction/results_fig.png)
An example of simulation results for one delayed lowering trial using the subject-specific (a) GPR, (b) NARX, and (c) pendulum models.
The GPR model prediction in (a) includes a 95% confidence interval.
The entire ground truth trial is shown in the black line, with the trip onset indicated by the arrow.
The NRMSE for this trial, averaged across each response variable, is provided for each prediction method.
The black dots represent the information provided to each model: 15 conditional points in (a); 15 feedback delay points in (b), and one initial condition for simulation in (c).