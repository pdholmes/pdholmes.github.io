---
title: "Reachable Sets for Safe, Real-Time Manipulator Trajectory Design"
layout: page
image: 
  path: /assets/images/armtd_wide.png
  thumbnail: /assets/images/armtd.png
  caption: "armtd"
---
Provably-safe motion planning for manipulators.

["Reachable Sets for Safe, Real-Time Manipulator Trajectory Design."](https://arxiv.org/abs/1810.11087) (**Patrick Holmes**, Shreyas Kousik, Bohao Zhang, Daphna Raz, Corina Barbalata, Matthew Johnson-Roberson, Ram Vasudevan), in Robotics: Science and Systems (RSS) 2020. [Recording.](https://youtu.be/6tjnh1Yxr_Q) [Video.](https://youtu.be/ySnux2owlAA) [Bibtex.](/assets/bibtex/armtd_ref.txt)

## Abstract
For robotic arms to operate in arbitrary environments, especially near people, it is critical to certify the safety of their motion planning algorithms.
However, there is often a trade-off between safety and real-time performance; one can either carefully design safe plans, or rapidly generate potentially-unsafe plans.
This work presents a receding-horizon, real-time trajectory planner with safety guarantees, called ARMTD (Autonomous Reachability-based Manipulator Trajectory Design).
The method first computes (offline) a reachable set of parameterized trajectories for each joint of an arm.
Each trajectory includes a fail-safe maneuver (braking to a stop).
At runtime, in each receding-horizon planning iteration, ARMTD constructs a parameterized reachable set of the full arm in workspace and intersects it with obstacles to generate sub-differentiable, provably-conservative collision-avoidance constraints on the trajectory parameters.
ARMTD then performs trajectory optimization over the parameters, subject to these constraints.
On a 6 degree-of-freedom arm, ARMTD outperforms CHOMP in simulation, never crashes, and completes a variety of real-time planning tasks on hardware.

## Videos

Our Robotics: Science and Systems (RSS) 2020 presentation about ARMTD for safe, real-time planning for manipulators using reachable sets.
<div class="youtube-video-container">
<iframe class="youtube-video" src="https://www.youtube.com/embed/6tjnh1Yxr_Q" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

***

ARMTD planning collision-free trajectories in real time on a Fetch manipulator robot:
<div class="youtube-video-container">
<iframe class="youtube-video" src="https://www.youtube.com/embed/ySnux2owlAA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Figures

![fetch_timelapse](/assets/images/armtd/fetch_timelapse.png)
ARMTD performs safe, real-time receding-horizon planning for a Fetch arm around a cabinet in real time, from a start pose (purple, low shelf) to a goal (green, high shelf).
Several intermediate poses are shown (transparent).
The callout on the left, corresponding to the blue intermediate pose, shows a single planning iteration, with the shelf in light red.
In grey is the arm's reachable set for a continuum of parameterized trajectories over a short time horizon.
The smaller blue set is the subset of the reachable set corresponding to the particular trajectory that was selected for this planning iteration, which is guaranteed not to collide with the obstacle

![jrs_overview](/assets/images/armtd/JRS_explanation.png)
An overview of the proposed method for a 2-D, 2-link arm.
Offline, ARMTD computes the JRSs, shown as the collection of small grey sets overlaid on the unit circle (dashed) in the sine and cosine spaces of two joint angles.
Note that each JRS is conservatively approximated, and parameterized by trajectory parameters *K*.
Online, the JRSs are composed to form the arm's reachable set (large light grey sets in *W*), maintaining a parameterization by *K*.
The obstacle *O* (light red) is mapped to the unsafe set of trajectory parameters *K<sub>u</sub>* on the left.
The parameter *k<sup>a</sup>* represents a trajectory, shown at five time steps (blue arms in *W*, and blue dots in joint angle space).
The subset of the arm's reachable set corresponding to *k<sup>a</sup>* is shown for the last time step (light blue boxes with black border), critically not intersecting the obstacle, which is guaranteed because *k<sup>a</sup>* is not in *K<sub>u</sub>*.

![armtd_vs_chomp](/assets/images/armtd/armtd_vs_chomp.png)
A Random Obstacles scene with 8 obstacles in which CHOMP converged to a trajectory with a collision (collision configurations shown in red), whereas ARMTD successfully navigated to the goal (green); the start pose is shown in purple.

![hard_scenarios](/assets/images/armtd/hard_scenarios.png)
The set of seven Hard Scenarios (number in the top left), with start pose shown in purple and goal pose shown in green.
There are seven tasks in the Hard Scenarios set: (1) from below to above a table, (2) from one side of a wall to another, (3) between two vertical posts, (4) from one set of shelves to another, (5) from inside to outside of a box on the ground, (6) from a sink to a cupboard, (7) through a small window.