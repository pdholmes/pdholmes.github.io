---
title: "Characterizing human stability during Sit-to-Stand"
image: 
  path: /assets/images/sts_wide.png
  thumbnail: /assets/images/sts.png
  caption: "sts"
---

A perturbative experiment with 11 subjects validates the Stability Basin approach.

## Publication

"Characterizing the limits of human stability during motion: perturbative experiment validates a model-based approach for the Sit-to-Stand task."](http://doi.org/10.1098/rsos.191410) (**Patrick D. Holmes**, Shannon M. Danforth, Xiao-Yu Fu, Talia Y. Moore, Ram Vasudevan), in Royal Society Open Science, 2020. [Repo.](https://github.com/pdholmes/STS_SB) [Dataset.](https://deepblue.lib.umich.edu/data/concern/data_sets/mw22v557c)

## Abstract
Falls affect a growing number of the population each year.
Clinical methods to assess fall risk usually evaluate 
the performance of specific motions such as balancing or Sit-to-Stand.
Unfortunately, these techniques have been shown to have poor predictive power, and are unable to identify the portions of motion that are most unstable.
To this end, it may be useful to identify the set of body configurations that can accomplish a task under a specified control strategy.
The resulting strategy-specific boundary between stable and unstable motion could be used to identify individuals at risk of falling.
The recently proposed Stability Basin
is defined as the set of configurations through time that do not lead to failure for an individual under their chosen control strategy.
This paper presents a novel method to compute the 
Stability Basin and the first experimental validation of the Stability Basin with a perturbative Sit-to-Stand experiment involving forwards or backwards pulls from a motor-driven cable with 11 subjects.
The individually-constructed Stability Basins are used to identify when a trial fails, i.e., when an individual must switch from their chosen control strategy (indicated by a step or sit) to recover from a perturbation.
The constructed Stability Basins correctly predict the outcome of trials where failure was observed with over 90% accuracy, and correctly predict the outcome of successful trials with over 95% accuracy.
The Stability Basin was compared to three other methods and was found to estimate the stable region with over 45% more accuracy in all cases.
This study demonstrates that Stability Basins offer a novel model-based approach for quantifying stability during motion, which could be used in physical therapy for individuals at risk of falling.

## Video

A presentation with early results about Stability Basins for characterizing stability during Sit-to-Stand at Dynamic Walking 2018.
<div class="youtube-video-container">
<iframe class="youtube-video" src="https://www.youtube.com/embed/QGkmM5EE_dw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## Figures

![STS_overview](/assets/images/sts/STS_overview.png)
An illustrative overview of 
Stability Basins for sit-to-stand.
The Stability Basin (shaded blue) represents the set of model states through time that will successfully arrive at a target set (light blue volume, right side) for a given individual and sit-to-stand strategy.
Trajectories of the model are illustrated, with nominal in gray, successful perturbed in blue, and failures in red.

![STS_pert](/assets/images/sts/STS_pertTimeSeries.png)
A typical perturbation time series is shown in this figure.
This particular perturbation was a forwards perturbation at the medium force level.
A baseline tensioning force of 19.6 *N* is commanded, until the start of the perturbation.
The force quickly ramps up to a specified peak, then back down to the baseline tensioning force.

![STS_TIPM](/assets/images/sts/STS_TIPM.png)
Subjects began from a seated position with their arms crossed against their chests (gray).
The subject's COM is illustrated by filled circles.
Cable-pulls applied to the subject sometimes caused them to step or sit (red); otherwise, the trial was considered to be successful (blue).

![STS_controllerModels](/assets/images/sts/STS_controllerModels.png)
These figures show how we construct the controller models from data.
The process is shown for *u<sub>x</sub>*, and is identical for *u<sub>y</sub>*.
In (a), *u<sub>x</sub>* evolves as a function of time *t* and state *x*, which has been depicted as a single dimension for this illustration.
The grey lines represent the input trajectories of nominal and foot-shift trials, while the blue lines represent the input trajectories of perturbed successful trials.
Note that we have not plotted the portions of the successful perturbed trajectories when the perturbations were active, because these segments are not used to train the controller models.
An arbitrary time *t=0.25* is illustrated by the black outline in (a). 
The observed inputs from nominal, foot-shift, and perturbed successful trials at that time are plotted as points in (b - d).
Figure (b) shows that the LQR controller utilizes linear feedback about a nominal trajectory.
Because the LQR controller is generated by minimizing a cost function specified by the matrices *Q* and *R*, its feedback matrix does not necessarily coincide with a line of best fit.
Figure (c) illustrates that the FF+FB controller is given by a line of best fit.
Figure (d) shows how the upper and lower bounds *u<sub>lb</sub>* and *u<sub>ub</sub>* are parallel linear functions of state that encompass all of the successful inputs.

![STS_XT](/assets/images/sts/STS_XT.png)
This figure illustrates how *X<sub>T</sub>* (the target set) is formed from data for a given subject and strategy.
The states (*r<sub>x</sub>* and *v<sub>x</sub>*) at 100% STS of each observed successful trial within a strategy are illustrated as blue dots.
An example *X<sub>T</sub>* represented by the shaded blue zonotope contains all of the states observed to lead to standing.
The zonotope is parameterized by its center *c* and generator vectors *g<sup>1</sup>* and *g<sup>2</sup>*.

![STS_sb_example](/assets/images/sts/STS_sb_example.png)
An example Stability Basin, with projections of horizontal states on the left and vertical states on the right.
The Stability Basin (light gray) is computed as the backwards reachable set of the target set (dark gray, right sides of plots), where black rings are used to accentuate the shape of the basins.
A trajectory from a trial in which the subject was pulled forward is shown in red.
The thick dashed line indicates the time of perturbation application.
A triangle marker indicates the time which the trajectory first exits the Stability Basin, which occurs before failure is initiated, denoted by the cross marker.

![STS_basins_all_controllers](/assets/images/sts/STS_basins_all_controllers.png)
The Stability Basins formed for Subject ID 1's natural sit-to-stand strategy using the LQR controller model (a), FF+FB controller model (b), Input Bounds controller model (c), and the naive method (d) are shown.
The horizontal and vertical projections of the Stability Basins are represented as the regions encapsulated by the light grey borders, where black outlines are used to emphasize the changes in shape of cross-sections over time.
The projection of the target set *X<sub>T</sub>* is shown as the dark grey region on the right side of each plot.

![STS_results_bars](/assets/images/sts/STS_results_bars.png)
This figure compares the predictive accuracy of the SBs formed using the Input Bounds controller to three other methods.
Results are presented for each sit-to-stand strategy, aggregated across subjects.
The Input Bounds controller's predictions for both successes and failures are near the ground truth, while the three other methods predict many more failures than were experimentally observed.
