---
title: "Real-Time Trip-Recovery Planning in Robotic Prostheses using Predicted Sets of Human Motion"
image: 
  path: /assets/images/triprtd_wide.png
  thumbnail: /assets/images/triprtd.png
  caption: "triprtd"
---

Online trip recovery planning for robotic prosthetic legs.

## Publication
**Article in preparation for IEEE Transactions on Robotics.**

See also:

Chapter 5 of my dissertation, ["Towards Safe Autonomy in Assistive Robots."](https://dx.doi.org/10.7302/2867) (**Patrick D. Holmes**). Committee: Prof. Ram Vasudevan, Prof. Robert D. Gregg, Prof. Talia Y. Moore, Prof. Elliott Rouse. University of Michigan, Department of Mechanical Engineering, 2021.

["Trip Recovery in Lower-Limb Prostheses using Reachable Sets of Predicted Human Motion."](https://arxiv.org/abs/2010.11228) (Shannon M. Danforth, **Patrick D. Holmes**, Ram Vasudevan), arXiv preprint, 2020.



## Abstract
People with lower-limb loss, the majority of which use passive prostheses, exhibit a high incidence of falls each year. 
Powered lower-limb prostheses have the potential to reduce fall rates by actively helping the user recover from a trip, but the unpredictability of the human response makes it difficult to design controllers that ensure a successful recovery. 
This paper presents a framework for online trip-recovery trajectory planning in a knee-ankle prosthesis that can robustly accommodate a set of predicted human trip-recovery behavior, which can directly account for uncertainty in the predicted human response.
Using this predicted set of human behavior, the proposed method computes a parameterized reachable set of trajectories for the human-prosthesis system.
To ensure safety at run-time, the framework selects a trajectory for the prosthesis via an optimization problem.
The problem's constraint guarantees that the foot will avoid scuffing the ground for the predicted set of swing hip behavior throughout swing phase, and the cost aims to place the foot in a desired location at the end of the step.
In a simulated environment using real-world trip-recovery data from 16 subjects, the framework produced feasible solutions for 87.2% of trip trials.
Of the feasible solutions, the framework avoided premature foot scuffs for 99.3% of trials and placed the foot an average of 3.4 cm from the desired location at the end of the step.
For comparison, a nominal impedance-based controller avoided premature foot scuffs for only 56% of trials and placed the foot an average of 8.2 cm from the desired location at the end of the step.

## Figures
![overview](/assets/images/triprtd/overview_fig.png)
The framework developed in this paper plans trajectories for robotic knee and ankle prostheses during and after a stumble that ensure successful recoveries for a set of predicted human behavior.
The kinematic model used in this work contains human and prosthesis subsystems, constructed from experimental data.
This figure shows reachable sets for the model, which depend on both human and prosthesis behavior, after a toe catch perturbation.
The gray zonotopes at the hip and knee represent the range of joint locations from the subject's predicted swing hip response.
The light orange and light purple zonotopes at the foot represent the set of prosthesis heel and toe locations for a range of parameterized prosthesis behavior.
Our framework selects one heel and toe parameter in an optimization program, which produce the darker orange and purple subsets.
The optimization program aims to (1) avoid toe scuffs and (2) ensure the heel strike location lands as close as possible to a *target set* representing desired foot contact location, shown by the green lines (in the callout), for each time step where ground contact is possible.
