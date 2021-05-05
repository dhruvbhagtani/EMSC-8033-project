# EMSC4033 project plan template

## Project title

## Executive summary

Large-scale circulatory patterns, called gyres, are omnipresent in the oceans. These gyres are known to be driven primarily by winds, but in recent years, it has come to light that surface buoyancy (heat and salt fluxes) can also affect the formation and evolution of these gyres. Although a full demystifcation of drivers of oceanic gyres is impossible within the time frame of the project, a step in the right direction is to implement a numerical solver for depth-integrated velocities in the presence of density variations (if time permits) for the mixed layer (ML) only. For the purpose of the project, the ML is the only moving layer in the ocean, and there is no exchange of water masses between the ML and thermocline layer.

## Goals

- Solving several 1D test cases, each with a specific forcing, like wind stress, coriolis forcing, effects of surface undulations.
- Coding similar tests for the 2D test cases using several boundary conditions, like free-slip or no-slip.
- Using the depth-integrated velocity equations in a fixed density and variable ML formulation and doing post-processing for obtaining barotropic streamfunction in the absence and presence of wind-stress and surface buoynacy.
- Extending the fixed density formulation to spatially and temporally variable density and ML case.

(Write things that you can assess whether they have been accomplished. For example, a goal like “improve visualisation of ocean output” is vague... But a goal that reads “implement functionality to plot streamlines of horizontal velocities in various slices from 3D ocean output” is specific enough.)

## Background and Innovation  

_Give more details on the scientific problem that you are working on and how this project will advance the discipline or help with your own research.
(Where applicable, describe how people have been achieving this goal up to now, talk about existing packages, their limitations, whether you can generalise something to help other people use your code)._

## Resources & Timeline

_What do you have at your disposal already that will help the project along. Did you convince somebody else to help you ? Are there already some packages you can build upon. What makes it possible to do this project in the time available. Do you intend to continue this project in the future ?_

(For example:
  - I’ll be using data of X from satellite and then also data from baby blue seals…
  - I’ll step on existing package Y and build extra functionality on top of class W.
  - I’ll use textbook Z that describes algorithms a, b, c
  - …
)

## Testing, validation, documentation

**Note:** You need to think about how you will know your code is correct and achieves the goals that are set out above (specific tests that can be implemented automatically using, for example, the `assert` statement in python.)  It can be really helpful if those tests are also part of the documentation so that when you tell people how to do something with the code, the example you give is specifically targetted by some test code.

_Provide some specific tests with values that you can imagine `assert`ing_
