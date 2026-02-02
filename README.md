# Description of the Repository
This repository is an online companion to the paper "Considering Kinematic Stability in Truss Topology
Optimization via a Singular Disturbance Scenario", which is currently under review at "Structural and Multidisciplinary Optimization". A preprint of the paper is available  [HERE](https://doi.org/10.21203/rs.3.rs-8154217/v1).

# Description of the Instance Data

Instances are sorted according to the experiments shown in the paper. For each experiment, the respective "*_build.txt" file shows main information on the instance:
InstanceName= Name of the Instance
xDim= Nodes in x direction (horizontal)
yDim= Nodes in y direction (vertical)
zDim= Nodes in z direction (diagonal)
e_module= Young's modulus
Yield= Yield Strength
Security= Security factor
MinWidth= minimum allowed diamater
MaxWidth= maximum allowed diameter
BasicLength= starting length of a member
Bearings: Bearing location F indicates fixed support, while L indicates loose support
F= Fixed support location
L= Loose support location
/Bearings
Forces: Nodal Location direction and amount of force
(v = vertical load, d = diagonal load, h = horizontal load)
Nodenumber_Fdirection=  load in N
END

The directories include the .lp and .sol file of the NLR approach, the SDS approach as well as the Initial approach (Basic) without the repaired structure.

The nodes are numbered direction-wise: first horizontally, then vertically, and finally diagonally.

The "*_ground.csv" files contain the data on the ground structure and are needed for generating the disturbance vector.

# Description of the Direction Optimizer

The python notebook "SDS_direction.ipynb" can be used to create disturbance directions according to Model (1) as presented in the paper. In order to calculate the vector, make changes to the following code segment, which can be found at the start of the notebook.

```
file='data/2_cantilever/9x6/cantileverLarge_ground.csv'
dimension=2
SingleDirection=True
NonNegativeDirection=True
eps=1e-5
```

For three-dimensional groundstructures, set dimension=3, and name the columns in your csv "x1;y1;z1;x2;y2;z2;s;t", where (x1,y1,z1) is one endpoint and (x2,y2,z2) is the other endpoint of a potential member; s and t are respective node numbers.

For two-dimensional groundstructures, set dimension=2, and name the columns in your csv "x1;y1;x2;y2;s;t", where (x1,y1) is one endpoint and (x2,y2) is the other endpoint of a potential member.

Set SingleDirection=True, if you want to obtain a single direction of the disturbance force, that takes into account ALL existing edges, regardless at which node. If SingleDirection=False, a separate direction for every node will be returned, only taking into account the adjacent edges.

Set NonNegativeDirection=True, if you want the direction to be in the first quadrant/octant, i.e., if you want every entry to be non-negative. If NonNegativeDirection=False, the direction is not restricted to a quadrant/octant.

The value eps describes the selected accuracy. In particular, values that are less than eps are considered to be zero. This is in particular relevant when it comes to detecting parallel members and planes.
