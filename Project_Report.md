# EMSC4033 project report

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

FD -> Forward Difference, BD -> Backward Difference, CD -> Central difference

In each notebook, an analytical solution is prepared and solved for each time step, and compared against the numerical solution. A .mp4 file is prepared to show this evolution and comparison. An error analysis is also performed in the end, where the number of points in the domain is varied over several orders of magnitude to test the dependence of spatial distances with accuracy of the numerical solution.

## 1D Advection

The notebook performs 1D advection on a tracer. I've only implemented Periodic Boundary conditions for this case because there are already a lot of variations, like the forward, backward and central difference schemes embedded into this notebook. Summarising the key observations from this notebook:
1. FD scheme in the presence of positive advection velocity is unstable. The same is true for BD scheme when we have negative advection velocity. These results come from the Von-Neumann analysis, which assumes that the solution consists of a convolution of many waves of different frequencies, and for each frequency, the solution should remain finite, i.e., it shouldn't blow up.
2. FD and BD schemes are 1st order accurate.

## 1D Diffusion

The notebook performs 1D diffusion on a tracer. Diffusion is a process where a substance moves from a region of higher concentration to a region of lower concentration. I've implemented it using central difference and periodic boundary conditions. Not shown here are the results for FD and BD schemes, which also give a stable solution but are first order accurate, and hence, discared. Summarising the key observations from this notebook:
1. The BD and FD schemes are first order accurate, whereas the CD scheme is second-order accurate, hence retained in the notebook.
2. In addition to using periodic boundary conditons, I've also implemented ghost points, which are another way of imposing boundary conditions. Ghost points are additional points which do not exist in our domain, they are merely fignment of imagination, introduced to help implement the finite difference approximation for the two end points.

## 1D Advection and Diffusion

The notebook performs both advection and diffusion simultaneously on a tracer on a 1D grid. This is a relatively short test, because we have already performed 1D advection and 1D diffusion before, and since we have created functions, we use the concept of modularity and don't have to rewrite the equations again. Summarising the key observations from this notebook:
1. The tracer advects and diffuses simultaneously, like we expected.

## 1D Shallow Water equations



## 2D Advection and Diffusion
