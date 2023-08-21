# SURFace-Algorithms
SURFace algorithms are programs that calculate solvent accessible surface area and curvature corrected solvent accessible surface area.
System requirements

SURFace algorithms run on linux systems.
No windows OS version available.


## surfv calculates solvent accessible area which is defined by a probe as it rolls on the surface of the molecule. 
Thus use of a zero radius probe will give the Van der Walls surface area.

It is executed by a single command line as in
`surfv (resolution) (probe radius) (sizefile) (pdbfile) 1(0) 1(0) 1(0)`
where resolution indicates the fineness of the mesh generated on the template sphere. It takes on integer values 1 - 4 with 4 giving the finest mesh. Usually avalue of 2 or 3 will suffice

* 1 - 122 points on the template sphere
* 2 - 482
* 3 - 1922
* 4 - 7682

`probe radius` is usually assigned a value of 1.4A which is often used in rendering molecular surfaces

`sizefile` gives the radii of atoms; it has to be in a specific format (see def.siz for format)

`pdbfile` is the standard brookhaven file giving the cartesian coordinates of atoms

The last 3 parameters add additional features to the program.

A non-zero integer in the 5th field will print out the residue areas in file pdbfile.res. Likewise a non-zero integer in the 6th field will write out atomic areas in pdbfile.atm

By default surfv will ignore hydrogens in area calculations even if there is an entry for them in the size file. You can override this option by using a non-zero integer in the 7th field of the input line

The atm and res files are in multi-column format. If you want single column format output (if you need to use this output in your script) then invoke surfv with an -s option as in

`surfv -s (nlevel) .......`


## surfcv calculates solvent accessible area and an average curvature 

It is executed by a single command line as in

`surfcv (resolution) (probe radius) (sizefile) (pdbfile) 1(0) 1(0) 1(0)`

where resolution indicates the fineness of the mesh generated on the template sphere. It takes on integer values 1 - 4 with 4 giving the finest mesh. Usually a value of 2 or 3 will suffice

`probe radius` is usually assigned a value of 1.4A which is often used in rendering molecular surfaces

`sizefile` gives the radii of atoms; it has to be in a specific format (see def.siz for format)

`pdbfile` is the standard brookhaven file giving the cartesian coordinates of atoms

The last 3 parameters add additional features to the program.

A non-zero integer in the 5th field will print out the residue areas and curvatures in file fort.7. Likewise a non-zero integer in the 6th field will write out atomic areas and curvatures in fort.8

By default surfcv will ignore hydrogens in area calculations even if there is an entry for them in the size file. You can override this option by using a non-zero integer in the 7th field of the input line.


## References

Nicholls A, Sharp KA, Honig B. **Protein folding and association: insights from the interfacial and thermodynamic properties of hydrocarbons.** Proteins. 1991;11(4):281-96.

Rocchia W, Sridharan S, Nicholls A, Alexov E, Chiabrera A, Honig B. **Rapid grid-based construction of the molecular surface and the use of induced surface charge to calculate reaction field energies: applications to the molecular systems and geometric objects.** J. Comput. Chem. (2002) 23:128-37.
