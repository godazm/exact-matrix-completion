# Exact Matrix Completion

This repository provides experimental results that are difficult to display in Section 5.2.1 of [1].
The matrices $Q$ and $U$ are stored in CSV format in "Q.csv" and "U.csv", respectively.
Since the length of $\boldsymbol{u}_2$ equals 21, $Q$ is a $21 \times 21$ symmetric matrix.
In addition, the example has 5 constraints
```math
\boldsymbol{h}(\boldsymbol{z}) = [y_1 - 7, y_2 - 3, x_2y_1 + 35, x_2y_3 - 10, x_3y_2 - 9]^\mathrm{T},
```
and $U$ is a $105 \times 105$ symmetric matrix.

We constructed $\boldsymbol{u}_2$ by the following code in Julia:
```julia
using DynamicPolynomials
@polyvar x[1:3]  # x[1] is not used
@polyvar y[1:3]
z = [x[2:3]; y]
vcat([reverse(monomials(z, k)) for k = 0:2]...)
```
and thus $\boldsymbol{u}_2 = [1, x₂, x₃, y₁, y₂, y₃, x₂², x₂x₃, x₂y₁, x₂y₂, x₂y₃, x₃², x₃y₁, x₃y₂, x₃y₃, y₁², y₁y₂, y₁y₃, y₂², y₂y₃, y₃²]^\mathrm{T}$.

# Reference

1. G. Azuma, S. Kim, and M. Yamashita. Exact Matrix Completion via High-Rank Matrices in SOS Relaxations. _arXiv:??.??_, 2023.

