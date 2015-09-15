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
