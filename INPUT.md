# blastfoam

_blastFoam_ is a solver for multi-component compressible flow with application to high-explosive detonation, explosive safety and air blast. 


## Get the code

blastFoam is free and opensource. blastFoam is currently in pre-release beta. If you'd like to request a copy of the code and solver before the official public release, while we're in beta, just get in touch: blastfoam@synthetik-technologies.com


## Features

_blastFoam_ currently supports the following features:

- An arbitrary number of phases/EOS's
- JLW equation of state with constant, linear, and "Miller" afterburn models
- Multiple example and tutorial cases
- Automatic mesh refinement (AMR)
- Single and multi-point detonation
- High-order (1st, 2nd, and 4th order in time; 3rd order spatial)
- HLLC, AUSM+, Kurganov, Tadmor flux schemes
- Parallel (MPI)
- Compatible with all standard OpenFOAM mesh generation, pre- and post-processing utilities



## Equations of State

blastFoam includes the following equations of state:

- Jones Wilkens Lee (with afterburn)
- Ideal Gas
- Stiffened Perfect Gas
- Cochran-Chan
- Tait



## Verification and Validation

_blastFoam_ has been validated against known solutions to standard gas dynamics problems, and against data from physical tests.  






## Governing Equations


The evolution of a two phase, compressible, and inviscid mixture can be defined by a set of coupled evolution equations for mass, momentum, and energy. 

$$
    \partial_t \mathbf{U} + \nabla \cdot \mathbf{F} = \mathbf{S}
$$

$$
    \mathbf{U} = 
        \left( \begin{array}{c}
           \alpha_1 \\
           \alpha_1 \rho_1 \\
           \alpha_2 \rho2 \\
           \rho \mathbf{u} \\
           \rho E
        \end{array} \right)
    \mathbf{F} = 
        \left( \begin{array}{c}
           \alpha_1 \mathbf{u} \\
           \alpha_1 \rho_1 \mathbf{u} \\
           \alpha_2 \rho_2 \mathbf{u} \\
           \rho \mathbf{u} \otimes \mathbf{u} + p \mathbf{I}\\
           (\rho E + p) \mathbf{u}
        \end{array} \right)
    \mathbf{S} = 
        \left( \begin{array}{c}
           \alpha_1 \nabla \cdot \mathbf{u} \\
           0 \\
           0 \\
           0 \\
           0
        \end{array} \right)
$$

where $\rho$ is the mixture density, $\mathbf{u}$ the mixture velocity, $E$ the total energy, $p$ the pressure, and $rho_i$ and $\alpha_i$ are the density and volume fraction of each phase. 





$$
    \alpha_2 = 1 - \alpha_1
$$


$$
    \rho = \sum_i \alpha_i \rho_i
$$


$$
    \rho E = \rho e + \frac{1}{2}\rho |\mathbf{u}|^2
$$

$$
    \rho e = \sum_i \alpha_i \rho_i e_i
$$

The pressure will be defined using a specified equation of state where the mixture internal energy, densities, and volume fraction are used to calculate the total pressure. The equations of state will be used in the Mie-Gruneisen form.

$$
    p_i(\rho_i, e_i, \rho) = (\Gamma(\rho_i) - 1) \rho_i e_i - \Pi(\rho_i)
$$










## Citation
If you use this code for your work or research, please cite this repository:

```
@software{heylmun_blastfoam:_2019,
	title = {{blastFoam}: An {OpenFOAM} Solver for Compressible Multi-Fluid Flow with Application to High-Explosive Detonation},
	url = {https://github.com/synthetik-technologies/blastfoam},
	publisher = {Synthetik Applied Technologies, {LLC}.},
	author = {Heylmun, Jeffrey and Vonk, Peter and Brewer, Timothy},
	date = {2019-10-22}
}
```