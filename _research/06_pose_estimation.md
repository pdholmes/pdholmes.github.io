---
title: "Certifiably-optimal 3D Human Pose Reconstruction"
image: 
  path: /assets/images/pose_wide.png
  thumbnail: /assets/images/pose.png
  caption: "pose"
---

Sums-of-Squares optimization for producing 3D human pose estimates that are certified as globally optimal.

## Publication

Chapter 2 of my dissertation, ["Towards Safe Autonomy in Assistive Robots."](https://dx.doi.org/10.7302/2867) (**Patrick D. Holmes**). Committee: Prof. Ram Vasudevan, Prof. Robert D. Gregg, Prof. Talia Y. Moore, Prof. Elliott Rouse. University of Michigan, Department of Mechanical Engineering, 2021.

## Abstract
We consider the challenge of perceiving 3D positions of a human's joints from multiple 2D RGB cameras simultaneously collecting video.
Our approach focuses on obtaining optimal solutions to this problem, which means that with our choice of cost function and constraints, no better solution exists.
Recent multi-view approaches are dominated by neural networks.
These approaches have been shown to produce excellent accuracy on certain datasets, such as the popular Human 3.6m dataset.
However, these datasets utilize validation images that closely match the neural networks' training data.
It remains unclear how well these approaches generalize to real-world scenarios because of this reliance on extensive training data.
In contrast, we propose an optimization-based approach for 3D pose reconstruction, which has several advantages
First, the optimization problem requires no training data.
Second, the optimization problem can employ strict constraints on link length.
Third, the optimization problem may be more computationally efficient in terms of memory and time required for inference.
Fourth and perhaps most importantly, solutions to this optimization can be certified as globally optimal with an easily checkable matrix rank condition, meaning that a better 3D pose estimate does not exist.
The framework we propose is based on the Sparse Bounded Degree Sums-of-Squares (SBSOS) hierarchy of convex relaxations.
Given a polynomial optimization problem, the SBSOS hierarchy gives a sequence of convex relaxations of the original problem that converge to the global solution.
The globally-optimal solution of the original problem is found at the first step of the hierarchy if certain conditions are satisfied, which we show happens over 99% of the time.
We show that our method matches or exceeds the accuracy of the current state of the art, with attractive theoretical guarantees and a shorter inference time.

## Figures

![intro_fig](/assets/images/pose/pose_intro_fig.png)
An example of the two-stage pose estimation framework applied to a test frame from the Human 3.6m dataset.
First, 2D pose estimates are collected from multiple RGB images showing different views of the same subject.
Then, given the extrinsic camera parameters which describe how the cameras are oriented with respect to each other, the multiple views are used to produce an accurate 3D pose estimate.

![notation](/assets/images/pose/pose_notation.png)
This figure explains notation and concepts found in this chapter.
2D pose estimates are generated in each camera frame for each joint *j*.
The estimated 2D pixel location of joint *j* in the *k*-th camera frame is given by *y<sup>jk</sup>*, with confidence *w<sup>jk</sup>*.
These estimates are *unprojected* to form a ray *y<sup>jk</sup><sub>3D</sub>* of 3D points that may have produced the estimate.
The decision variables *x<sup>j</sup>* are chosen to minimize a squared measurement residual representing the distance of *x<sup>j</sup>* from each of these rays.
Link length constraints are enforced between any two linked joints; in this figure, joints *p* and *q* are connected by a link of length *l<sub>pq</sub>*. 

![results](/assets/images/pose/pose_results.png)
Comparison of our method to the current state of the art (Iskakov et al.) on the Human 3.6m dataset.
Results are presented as the absolute MPJPE (in mm) from ground truth. 
The validation set has been filtered according to the protocol done by Iskakov et al., which removed scenes with erroneous ground truth annotations.
Minimum MPJPE in each column is bolded.
The same LT 2D pose detector is used for our method as for Iskakov et al.'s methods to generate the 2D pose estimates, and all camera views are included for inference.
Furthermore, we include results for an unweighted naive triangulation method, which serves as a baseline for comparison.

![results](/assets/images/pose/pose_timing.png)
Comparison of inference time between our method and the current state of the art on the Human 3.6m dataset when using all available cameras.
Inference time for our method is the time to solve the optimization problem using SBSOS with *k=1*, *d=1*.
For the methods used by Iskakov et al., inference time has been reported for the full pipeline, which we use to infer the time for the 3D reconstruction alone.
The same LT 2D pose detector is used in all instances.
*Here, we assume that the algebraic method takes the same amount of 3D inference time as the nearly identical unweighted triangulation approach, and use this to arrive at the time for the volumetric approach

![3D_comparison](/assets/images/pose/pose_3D_comparison.png)
A comparison of 3D pose estimates generated via our method with length constraints when using the LT and OP detectors.
The 3D estimate formed using OpenPose is relatively accurate.
However, it misplaces the 3D position of the left arm because of poor estimates from the back cameras (leftmost two images on the left hand side).