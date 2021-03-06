# Exercise 7

The goal of this exercise is to implement, optimize, parallelize and benchmark 1D, 2D and 3D stencil algorithms calculating heat propagation using Jacobi iterations. (see https://en.wikipedia.org/wiki/Stencil_code) The basic algorithm updates each cell (in a 1D, 2D or 3D grid) based on the values of its neighbours, or fixed values at the boundaries (e.g. the left neighbour of the cell at the point `(0)` in a 1D grid, or the top neighbour of the point `(x,0)` in a 2D grid).

The programs should support setting arbitrary boundary conditions (2 for 1D, 4 for 2D, 6 for 3D), and iterate until the rate of overall change in the system falls below some epsilon value.

**The total iteration time should be measured.** Parallelization should occur across the update steps for each cell. *For this exercise, implement shared memory parallelization using OpenMP.*

## Unit Testing
Your program and its individual components should be unit tested. 
E.g. you can provide some fixed boundary conditions such as `left=1; right=0` for a 1D grid of `N=10` points, and check against the correct solution (+/- epsilon at each of the 10 points) after running all iterations.

## Shared memory stencil benchmarking

Benchmark using this setup:
- 2D grid of 512x512 cells
- 5 point heat stencil
- **`double`** datatype
- Iterate until Epsilon (as the sum of all changes across the grid) is less than **10.0**
- North/East/South/West boundaries fixed at **1.0, 0.5, 0.0 and -0.5** respectively
- All initial values should be set to **0.0**
- Use the **-O3 and -march=native** compiler flags (not -Ofast)

With 1, 2, 4 and 8 threads on a single node of the cluster.

## LCC2
All benchmarks should be performed on the LCC2 cluster. *Please try to make sure that your individual benchmarking runs do not take more than 1 minute.* Shorter runs are preferable.

## General Note
*Every* member of your group should be ready to explain your methods and findings. All of you should also be able to answer in-depth question about the problem studied.
