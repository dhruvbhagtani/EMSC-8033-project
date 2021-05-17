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

11th May, 2021 -> Create a 1D code for advection, and show that the series converge as distance between two points reduces. Also, show how quickly the error reduces, and when it blows up, for different schemes, like the forward difference, backward difference and central difference.

14th May, 2021 -> Implement the same code for 1D diffusion, and again show that the series converge as distance between two points reduces. Also, show how quickly the error reduces, and when it blows up, for different schemes, like the forward difference, backward difference and central difference.

18th May, 2021 -> As the 1D case is finished, implement the same for 2D case (both advection and diffusion), and again show how the results converge by changing the number of points in the domain. Show how the forward difference, backward difference and central difference differ from each other.

21st May, 2021 -> Implement the 1D shallow water equations - test whether the FD, BD or CD are stable or not. 

25th May, 2021 -> Implement the 2D equations in the absence of explcit density or height variation equations - in other words, a Boussinesq set of equations, solving for horizontal velocities in a simplified domain.

28th May, 2021 -> If time permits, allow for density and height variaions in the simplified domain.

This project forms a part of my PhD thesis - I've prepared a set of equations to be used in a simplified model, known as the "Toy Model", where there are very few parametrisations. In order to code this "Toy Model", it is important to test a few basic ideas - for example, a 1D case, followed by a 2D case, considering forcings individually. 

I've devised this timeline considering the scenario where I am unable to finish all the codes in the designated time. The timeline comprises of short independent tasks. Moreover, I intend to continue this project in the future. 

(For example:
  - I’ll be using data of X from satellite and then also data from baby blue seals…
  - I’ll step on existing package Y and build extra functionality on top of class W.
  - I’ll use textbook Z that describes algorithms a, b, c
  - …
)

## Testing, validation, documentation

Testing and validation are important aspects of any code. The reason for starting the toy model from scratch is that since the differential equations are so simplified that we can solve them to obtain analytical solutions, and compare them with the numerical solution. This way, we can lay a strong foundation and build our way upwards. Some more tests can be doing a Von Neumann error analysis to understand why the FD, BD or CD schemes are failing for a specific differential equation. In addition, the _assert_ function is a very handy tool to throw exception errors and understand the source of these errors.

Finally, I intend to document each piece of code in the following fashion:

1. Using one-line comments within the code.
2. Using functions wherever needed to improve modularity. This can help a lot if we are re-using the function. 
3. Writing up docstrings for each function. Every docstring will have a short tagline mentioning the purpose of the function, its inputs and the variable(s) it is returning.
4. Using variable names which are easy to relate. For eg, if I have a MLD evolution equation having two variables, one for the previous and one for the current time step, then instead of declaring them as _h1_ and _h2_, I would declare them as _hm_old_ and _hm_new_.
