---
title: "Safe, Aggressive Quadrotor Flight via Reachability-based Trajectory Design"
image: 
  path: /assets/images/quadrotor_rtd_wide.png
  thumbnail: /assets/images/quadrotor_rtd.png
  caption: "quadrotor_rtd"
---

Provably-safe motion planning for quadrotors.

## Publication

["Safe, Aggressive Quadrotor Flight via Reachability-based Trajectory Design."](https://arxiv.org/abs/1904.05728) (Shreyas Kousik, **Patrick Holmes**, Ram Vasudevan), in ASME Dynamic Systems and Control Conference (DSCC), 2019. **Best Student Paper Award.** [Video.](https://youtu.be/1cldHVQK3Yw)

## Abstract

Quadrotors can provide services such as infrastructure inspection and search-and-rescue, which require operating autonomously in cluttered environments. 
Autonomy is typically achieved with receding-horizon planning, where a short plan is executed while a new one is computed, because sensors receive limited information at any time.
To ensure safety and prevent robot loss, plans must be verified as collision free despite uncertainty (e.g, tracking error).
Existing spline-based planners dilate obstacles uniformly to compensate for uncertainty, which can be conservative.
On the other hand, reachability-based planners can include trajectory-dependent uncertainty as a function of the planned trajectory.
This work applies Reachability-based Trajectory Design (RTD) to plan quadrotor trajectories that are safe despite trajectory-dependent tracking error.
This is achieved by using zonotopes in a novel way for online planning.
Simulations show aggressive flight up to 5 m/s with zero crashes in 500 cluttered, randomized environments.

## Videos

Our quadrotor RTD algorithm at work in simulation:
<div class="youtube-video-container">
<iframe class="youtube-video" src="https://www.youtube.com/embed/1cldHVQK3Yw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Figures

![RTD_overview](/assets/images/quadrotor_rtd/RTD_overview.png)
An overview of the proposed method.
Points in the trajectory parameter space (on the left) correspond to desired trajectories (the dashed blue line on the right).
The quadrotor, shown with its body-fixed coordinate frame, executes the solid blue trajectory, which has tracking error that depends on the desired trajectory.
A Forward Reachable Set (FRS) is computed over all desired trajectories, plus tracking error and the body of the robot.
The FRS is intersected with obstacles (red box on the right) to identify unsafe trajectories (red area on the left).
Then, the subset of the FRS given by any safe trajectory parameter (blue tube on the right) will not intersect any obstacles.
The particular desired trajectory shown attempts to reach a waypoint (gold star).

![example_world_fpv](/assets/images/quadrotor_rtd/example_world_fpv.png)
An example trajectory planned online in a cluttered environment with obstacles in light red and the ground in brown.
The tube of light blue boxes, which does not intersect any obstacles, is the subset of the zonotope FRS for the current plan plus tracking error, so the quadrotor (in dark blue) is guaranteed to fly within the tube.
The world and trajectory are shown in the next figure.

![example_world](/assets/images/quadrotor_rtd/example_world.png)
The example simulated world from the previous figure, with obstacles in light red, the ground in brown, world boundaries as axes, and the global goal as a light green sphere.
A trajectory of the quadrotor is shown in dark blue, and goes from left to right.
The quadrotor's reachable set (light blue) is shown for the same planning iteration as in the previous figure.