# EMSC4033 Project Report

## Toy Model Development

## Contents of the repository

* Euler
  * Periodic_1D.py: Python code storing methods to implement several functionalities of Navier Stokes equations in 1D
  * Periodic_2D.py: Python code storing methods to implement several functionalities of Navier Stokes equations in 2D
* 1D_Advection.ipynb: Implemented 1D advection using periodic boundary conditions for FD, BD and CD.
* 1D_Diffusion.ipynb: Implemented 1D diffusion using periodic boundary conditions for FD, BD and CD.
* 1D_Advection_DIffusion.ipynb: Implemented 1D advection and diffusion simultaneously using periodic boundary conditions for FD, BD and CD.
* 1D_SWE.ipynb: Implemented 1D shallow water equations for non-rotating and rotating domain for Neumann, Dirichlet and periodic boundary conditions.
* 2D_Advection_Diffusion.ipynb: Implemented 2D advection and diffusion simultaneously using periodic boundary conditions for FD, BD and CD.
* 2D_Coriolis_forcing.ipynb: Implemented 2D forcing using wind stress and coriolis effects.
* Videos : Outputs for different tests
  * 1D_Adv
    * 1D_BD_Advection_2.mp4
    * 1D_BD_Advection.mp4
    * 1D_FD_Advection.mp4
    * 1D_stable_Advection.mp4
  * 1D_Diff
    * 1D_Diffusion.mp4
    * 1D_Diffusion_GP.mp4
  * 1D_AD
    * 1D_Adv_Diff.mp4 
  * 1D_SWE
    * 1D_SWE_NCons_um.mp4
    * 1D_SWE_NCons_vm.mp4
    * 1D_SWE_NCons_hm.mp4
    * 1D_SWE_Cons_um.mp4
    * 1D_SWE_Cons_hm.mp4
    * 1D_SWE_Cons_um_NBC.mp4
    * 1D_SWE_Cons_hm_NBC.mp4
    * 1D_SWE_Cons_um_PBC.mp4
    * 1D_SWE_Cons_hm_PBC.mp4
    * 1D_SWE_coriolis_um.mp4
    * 1D_SWE_coriolis_vm.mp4
    * 1D_SWE_coriolis_hm.mp4
  * 2D_AD
    * 2D_Adv.mp4
    * 2D_Adv_Error.mp4
    * 2D_Diff.mp4
    * 2D_Diff_Error.mp4
    * 2D_Adv_Diff.mp4
    * 2D_Adv_Diff_Error.mp4
  * 2D_Cor
    * um_new.mp4
    * um_new_error.mp4 
    * vm_new.mp4
    * vm_new_error.mp4 

FD -> Forward Difference, BD -> Backward Difference, CD -> Central difference

In each notebook, an analytical solution is prepared and solved for each time step, and compared against the numerical solution. A .mp4 file is prepared to show this evolution and comparison. An error analysis is also performed in the end, where the number of points in the domain is varied over several orders of magnitude to test the dependence of spatial distances with accuracy of the numerical solution.

## 1D Advection

This [notebook](https://github.com/dhruvbhagtani2105/EMSC-8033-project/blob/main/1D_Advection.ipynb) performs 1D advection on a tracer. I've only implemented Periodic Boundary conditions for this case because there are already a lot of variations, like the forward, backward and central difference schemes embedded into this notebook. Summarising the key observations from this notebook:
1. FD scheme in the presence of positive advection velocity is unstable. The same is true for BD scheme when we have negative advection velocity. These results come from the Von-Neumann analysis, which assumes that the solution consists of a convolution of many waves of different frequencies, and for each frequency, the solution should remain finite, i.e., it shouldn't blow up.
2. FD and BD schemes are 1st order accurate.

## 1D Diffusion

This [notebook](https://github.com/dhruvbhagtani2105/EMSC-8033-project/blob/main/1D_Diffusion.ipynb) performs 1D diffusion on a tracer. Diffusion is a process where a substance moves from a region of higher concentration to a region of lower concentration. I've implemented it using central difference and periodic boundary conditions. Not shown here are the results for FD and BD schemes, which also give a stable solution but are first order accurate, and hence, discared. Summarising the key observations from this notebook:
1. The BD and FD schemes are first order accurate, whereas the CD scheme is second-order accurate, hence retained in the notebook.
2. In addition to using periodic boundary conditons, I've also implemented ghost points, which are another way of imposing boundary conditions. Ghost points are additional points which do not exist in our domain, they are merely fignment of imagination, introduced to help implement the finite difference approximation for the two end points.

## 1D Advection and Diffusion

This [notebook](https://github.com/dhruvbhagtani2105/EMSC-8033-project/blob/main/1D_Advection_Diffusion.ipynb) performs both advection and diffusion simultaneously on a tracer on a 1D grid. This is a relatively short test, because we have already performed 1D advection and 1D diffusion before, and since we have created functions, we use the concept of modularity and don't have to rewrite the equations again. Summarising the key observations from this notebook:
1. The tracer advects and diffuses simultaneously, like we expected.

## 1D Shallow Water equations

This [notebook](https://github.com/dhruvbhagtani2105/EMSC-8033-project/blob/main/1D_SWE.ipynb) performs an evolution on the x and y direction fluid velocities in a 1D domain using an idealised form of Navier Stokes equations, known as the shallow water equations (SWE). The shallow water equations are a set of hyperbolic partial differential equations (or parabolic if viscous shear is considered) that describe the flow below a pressure surface in a fluid (sometimes, but not necessarily, a free surface). We perform this analysis using all three boundary conditons - Dirichlet, Neumann and Periodic. 

For each test in this notebook, we have a small wave in the middle of the domain. As time elapse, the wave breaks into two waves, each having half the amplitude of the original wave. These two waves start travelling in the opposite directions and when they reach the edges, they interact with the imposed boundary conditions. Summarising the key observations from this notebook:
1. We first use an unstaggered grid in a non-rotating domain, meaning that the tracer and momentum variables are placed and evolved on the same grid. This is easier to code, but in most global circulation models, it is not favoured. The reason is easily seen from this analysis - the simulation isn't stable for any number of points in the domain. It is stable until it reaches the boundaries, where it starts blowing up.
2. The next test is to use a staggered grid in a non-rotating domain, i.e., the tracer (wave height) and momentum (x and y velocities) variables are evolved at different places in the domain. This is belived to be more stable, and is often used in GCMs. When applied to the 1D SWE, the staggered grid works well, and produces correct results even after interacting with the boundaries.
3. The Dirichlet boundary conditions are also called reflecting boundary conditions, and we can see the reason why. When applied to the staggered grid, the wave bounces to the other side of the x-axis and starts propagating in the opposite direction. For Neumann boundary conditions, the wave does start moving in the opposite direction, but it doesn't flip about the x-axis.
4. Finally, we apply the staggered grid to 1D SWE in a rotating domaain. The results are similar to (2) - we get a stable evolution of the wave. A point worth mentioning is that small oscillations in the wave heights start to develop as both waves interact with each other.

## 2D Advection and Diffusion

This [notebook](https://github.com/dhruvbhagtani2105/EMSC-8033-project/blob/main/2D_Advection_Diffusion.ipynb) performs both advection and diffusion simultaneously on a tracer, but this time on a 2D grid. We use an ustaggered grid here. Summarising the key observations from this notebook:
1. The first test is 2D advection. The code is generalised, so we can have two different velocities in x and y directions, and even different velocities for each grid point. The numerical solution matches well with the true solution for all time steps.
2. The next test is 2D diffusion. Again, we can impose different diffusivities in x and y directions, and even for each grid point. The errors are very less when compared against the numerical solution, so 2D diffusion code works.
3. Finally, we add these two functionalities into a single piece of code. We solve for a tracer experiencing both advection and diffusion simultaneously. When compared against the true solution, the errors are minute. 
4. We also perform an error analysis for each of the three cases above, and for each case, the error goes down as we increase the number of points in the domain. The decreasing line follows the expected order of convergence, based on what sort of finite differencing scheme we have used for each operatoin.

## 2D Coriolis and Wind Forcing

This final [notebook](https://github.com/dhruvbhagtani2105/EMSC-8033-project/blob/main/2D_wind_forcing_and_Coriolis.ipynb) helps our understanding of the Coriolis and wind forces in a 2D domain. Summarising the key observations from this notebook:
1. The first test involves only the wind forcing, i.e., we have a non-rotating region. We numerically evolve the horizontal velocities and compare them against the true solution, which is found analytically.
2. Next, we have a rotating 2D region. The analytical solution is much more difficult to find, and the math is done in the notebook. Finally, we compare our numerical solution with this analytical solution, and our results match to a large extent.

With all the bits and pieces coded individaully, the next step of this project is to write down a code for 2D Navier Stoke's equations with fixed height and density. Unfortunately, contrary to what I had written down in the Project Plan, I couldn't reach this stage, and this becomes a future work for this project.
