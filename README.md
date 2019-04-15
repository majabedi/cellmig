README
------

This is the custom `LAMMPS` fix for active migration of a polarized cell. 

## HOW TO USE

### Build LAMMPS

1. Add MC and MOLECULE packages ro lammps using: 
`make yes-MC`
`make yes-MOLECULE`
2. Put `fix_cell_migrate.cpp`/`fix_cell_migrate.h`/`bond_harmonic.cpp` files into `src` folder of `LAMMPS`.
3. Build `LAMMPS`.

### Use it in input file

```
fix ID group-ID cell/migrate Nevery nucleus-atomtype membrane-atomtype membrane_extended-atomtype ECM-atomtype Rmin dir:x/y/z prob membrane-ECM_binding-bond nucleus-membrane_normal-bond nucleus-membrane_extended-bond 
```

* ID, group-ID
* cell/migrate = style name of this fix command
* Nevery = use input values every this many timesteps
* nucleus-atomtype = atom type of nucleus elemets
* membrane-atomtype = atom type of membrane elements
* membrane_extended-atomtype = atom type of a membrane element which has made a protrusion
* ECM-atomtype = atom type of a ExtreaCellular Matrix elements
* Rmin = 2 elements from ECM and membrane should be separated by less than Rmin to make bond (distance units)
* dir = direction of polarization and migratiopn could be x/y/z
* prob = the probablity of making a binding when two elements are close enough
* membrane-ECM_binding-bond = bond type of membrane-ECM binding
* nucleus-membrane_normal-bond = bond type of nucleus-membrane_element normal binding
* nucleus-membrane_extended-bond = bond type of nucleus-membrane_element extended binding

### Examples

```
fix cellmig all cell/migrate 5000 1 2 4 3 2.3 x 0.8 4 1 5
```

## IMPORTANT NOTES

* :heavy_exclamation_mark: **Please use this fix only with the serial version.**



