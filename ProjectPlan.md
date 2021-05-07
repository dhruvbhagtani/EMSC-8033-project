# EMSC4033 project plan template

## Project title

## Executive summary

Implementing a numerical solver for depth-integrated velocities in the presence of density variations (if time permits) for the mixed layer (ML) only. For the purpose of the project, the ML is the only moving layer in the ocean, and there is no exchange of water masses between the ML and thermocline layer.

## Goals

- Solving several 1D test cases, each with a specific forcing, like wind stress, coriolis forcing, effects of surface undulations.
- Coding similar tests for the 2D test cases using several boundary conditions, like free-slip or no-slip.
- Using the depth-integrated velocity equations in a fixed density and variable ML formulation and doing post-processing for obtaining barotropic streamfunction in the absence and presence of wind-stress and surface buoynacy.
- Extending the fixed density formulation to spatially and temporally variable density and ML case.

## Background and Innovation  

Large-scale circulatory patterns, called gyres, are omnipresent in the oceans. These gyres are known to be driven primarily by winds [Luyten et al, 1983](https://journals.ametsoc.org/view/journals/phoc/13/2/1520-0485_1983_013_0292_tvt_2_0_co_2.xml) and [Wunsh and Ferrari, 2004](https://www.annualreviews.org/doi/abs/10.1146/annurev.fluid.36.050802.122121), but in recent years, it has come to light that surface buoyancy (heat and salt fluxes) can also affect the formation and evolution of these gyres [Hogg and Gayen, 2020](https://agupubs.onlinelibrary.wiley.com/doi/abs/10.1029/2020GL088539).

Extensive research has been done on wind-driven gyres, dating back to as early as 1940s [Stommel, 1948](https://agupubs.onlinelibrary.wiley.com/doi/10.1029/TR029i002p00202). However, from the 1980s, researchers started exploring other ways by which oceanic gyres can be created, such as tidal forces and surface buoyancy fluxes [Luyten and Stommel, 1986](https://journals.ametsoc.org/view/journals/phoc/16/9/1520-0485_1986_016_1551_gdbcwa_2_0_co_2.xml). There are several ways to prescribe these surface buoayncy fluxes - (i) Imposing temperature gradients [Liu and Pedlosky, 1994](), and (ii) Setting heat and freshwater fluxes [Huang and Bryan, 1987]().

This project lays the foundation for a successful implementation of an innovative toy model, which is needed to understand the various feedbacks due to wind and heat fluxes on several ocean properties. The toy model is an idealised version of a typical General Circulation Model (GCM), i.e., the toy model is devoid of any bells and whistles that is present in a GCM. It has a provision of calculating the depth-integrated Eulerian velocity using the Navier-Stoke's equations. Additionally, we can also calculate the temporal and spatial variations in ocean density and mixed layer height. 

To build this toy model, we need to perform several tests, which is achieved through this project.

## Resources & Timeline

This project is part of my PhD. The toy model has been developed to a large extent, but only theoretically. These tests can be simplified into independent tasks, making it a feasible course project. Everything is coded from scratch. There are several tests that can be done - We can test 1D/2D diffusion (or 1D/2D advection) using several schemes (Euler explicit or leap frog scheme) for different discretisation methods (forward, backward and central differences) in the presence of various boundary conditions (Dirichlet, Neumann or periodic). To analyse each test, a convergence and error as a function of model resolution is obtained. A rough timeline for the project is:

11th May, 2021 -> 
14th May, 2021 ->
18th May, 2021 ->
21st May, 2021 ->
25th May, 2021 ->
28th May, 2021 ->

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
