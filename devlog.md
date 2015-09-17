# Development log

## 14.09.15
* [ ] Finish Bryce's design (B01)

### Things to consider
* Cavity length stabilisation: Slow drift in cavity length arises from thermal expansion of ECDL block, in addition to acoustic and mechanical vibrations coupled from outside. Thermally induced variation in cavity length should be small compared to the PZT tuning range (~2um), which encourages short cavity length. Mechanical and acoustic coupling could be minimised by increasing the thickness of the block walls, as well as incorporating passive vibration damping material.
* A *wedge* window should be used to the free-space beam outlet port. Forming an additional optical cavity should be avoided while laser output and hermetic sealing is desired.
* Selecting a piezo transducer: disk type preferred, easy gluing.

## 15.09.15
* [x] Add wedge laser window to CAD: design mounting and seal
  * Part: Thorlabs WW11050-C13-Dia1" - Wedged N-BK7 Laser Window, AR Coated: 700-1100nm
  * Custom CB on the block to glue window directly
  * Beam must be incident on the tapered side
* Configure git to ignore autosave files with ~ in file name
* Rounded slip plate mounting bracket's base and the mounting slot
* O-ring groove redesigned to be referenced from inside
* Fix ref error in the block lid dimensions
* [ ] Shorten cavity length to ~30mm (currently ~60mm)
  * The lens slip mount subasm could be redesigned
  * Spot position on grating can also be optimised

## 16.09.15
* Update *.gitignore*: 
  * add .swp files
  * remove .gitignore 
* Fixed bad referencing in main block's slip-mount slot: in-context at the assembly
* Slip-plate 
  * flip mounting cofig for better accessibility
  * reposition lens-tube holding hole to reduce cavity length
  * redesign slip-plate mounting bracket to reduce size
  * Fix dangerous mating list
* Revise reference for KMSS grating subasm locating holes in block
* Briefly tuned some design params to position grating to be centered on the laser spot
* Slots added on block for mirror mount with dims referenced to the subasm geometry

### Clean references
Prepare for changes in major design parameters, such as the gain-chip mount height for which the slip-plate mounting bracket's dimensions should be referenced to.
* Gain-chip mounting boss
* Remodelled the slip-plate mounting bracket (B01_XY_bracket) *in-context* to the laser gain-chip location and block geometry

## 17.09.15
### ANU ECDL
#### Description
ANU ECDL is a narrow linewidth, broadly tunable external cavity diode laser developed and designed by the Atom Laser group at ANU. It is designed for low cost and manufacturability so that the highly desirable optics and control properties can be practically employed by atomic physics laboritories, etc. The developers attribute its impressive linewidth to acoustic isolation by fibre coupling the gain chip and eliminating acousitc resonances by their custom cavity alignment system, replacing the conventional kinematic mount). ANU ECDL is the design our lab (Truscott Lab at ANU) is basing the new ECDL master laser for the He* experiments. Below is a description of ANU ECDL. 

* System components
  * Gain medium & fibre outcoupling
    * gain-chip: SAF1550P2, Thorlabs - fibre coupled ECDL
    * isolator
      * built-in (insufficient)
      * dual stage 50dB fibre coupled polarization maintaining, **fast-axis** blocked --> robustly single mode & polarized
    * fibre: single transverse mode polarization maintaining    
  * Grating
    * diffraction grating: 1100 lines/mm 90% at 1.56um (05HG1100-900-1, Newport/Richardson)
    * grating mount: POLARIS-K1-H, Thorlabs 
  * Collimator
    * lens: 2.97mm, AR coated moulded aspheric lens (355660-C, Thorlabs)
    * flexure mount

* Design specification
  * Cavity length (optical path length): 60mm 

* Design characteritics
  * Vibration damping
    * laser block on 5cm of acoustic dampening foam
  * Mechanical stiffening
    * **Thick walls**
    * compactness 
  * Mechanical/vibrational isolation
    * fibre coupled output with the output end **rigidly fixed** the **application system's reference plane** for decoupling mech/vibs from environment

* ECDL specification
  * FWHM linewidth: ~10kHz
  * Tuning ranges (10dB): 1420-1620nm (200nm)
  * Stability over time: 
