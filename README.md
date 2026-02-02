Description of the Instance Data

Each Instance is found under the directory with its respective name
The Instance_Build.txt file shows how the instance is build:
InstanceName=Name of the Instance
xDim= Nodes in x direction (horizontal)
yDim= Nodes in y direction (vertical)
zDim= Nodes in z direction (diagonal)
e_module= Young's modulus
Yield= Yield Strength
Security Security factor
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

The Instance_Ground.csv contains the necessary data for generating the disturbance vector.
The files follow the format:
x1;y1;z1;x2;y2;z2;d , with
x1,y1,z1 starting coordinates of a member
x2,y2,z2 end coordinates of a member
