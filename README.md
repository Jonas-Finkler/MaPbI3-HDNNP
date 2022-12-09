# MaPbI3-HDNNP
High dimensional neural network potential [1,2] for MaPbI3.   
The potential was developed for Funnel Hopping Monte Carlo study of MaPbI3 [9].
Please cite this reference if you use this potential or the dataset. 


The potential was trained with the RuNNer software [3] using energy and forces of structures from all three perovskite phases (orthorhombic, tetragonal, cubic) 
as well as the two delta phases [4].

The potential can be used with the RuNNer software [3], n2p2 [8] or my implementation of the HDNNP [6].
An example that runs an MD simulation with the potential can be found in a separate branch [7].

### Bias
This repository includes parameters for five HDNNP fits which were generated using the same training data but with a different initialization of the weights.
Each potential should be reliable enough to run MD simulations at up to 400K. 
However, it can be useful to use all five potentials together as the standard deviation between the predictions allows for an estimate of the prediction accuracy. 
Evaluating all five potentials comes at little additional cost, since the most computationally expensive part of the HDNNP, the calculation of the symmetry functions, has to be done only once. 

The uncertainty estimate can also be useful to add a small positive energy bias to the potential for regions with a high uncertainty. 
This bias can be useful for example in funnel hopping MC [5] simulations.
In these simulations a global MC move is constructed which sometimes goes beyond the configuration space represented in the training data.
The bias ensures that moves to these regions which should be high in energy but can appear low due to missing training data are rejected. 
Such a bias is implemented in the example [7].

### References

[1] [Behler, Jörg, and Michele Parrinello. "Generalized neural-network representation of high-dimensional potential-energy surfaces." Physical review letters 98.14 (2007): 146401.](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.98.146401)  
[2] [Behler, Jörg. "Atom-centered symmetry functions for constructing high-dimensional neural network potentials." The Journal of chemical physics 134.7 (2011): 074106.](https://aip.scitation.org/doi/full/10.1063/1.3553717)  
[3] <https://www.uni-goettingen.de/de/560580.html>   
[4] [Flores-Livas, José A., et al. "Emergence of hidden phases of methylammonium lead iodide (CH 3 NH 3 PbI 3) upon compression." Physical Review Materials 2.8 (2018): 085201.](https://journals.aps.org/prmaterials/abstract/10.1103/PhysRevMaterials.2.085201)   
[5] [Finkler, Jonas A., and Stefan Goedecker. "Funnel hopping monte carlo: an efficient method to overcome broken ergodicity." The Journal of Chemical Physics 152.16 (2020): 164106.](https://aip.scitation.org/doi/full/10.1063/5.0004106)  
[6] <https://github.com/Jonas-Finkler/High-Dimensional-Neural-Network-Potential>   
[7] <https://github.com/Jonas-Finkler/High-Dimensional-Neural-Network-Potential/tree/MaPbI3-example>   
[8] <https://github.com/CompPhysVienna/n2p2>   
[9] [Finkler, Jonas A., and Stefan Goedecker. "Experimental Absence of the Non-Perovskite Ground State Phases of MaPbI3 Explained by a Funnel Hopping Monte Carlo Study Based on a Neural Network Potential." Materials Advances (2023).](https://doi.org/10.1039/D2MA00958G)
