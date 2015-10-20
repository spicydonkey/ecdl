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

## 18.09.15
* [x] Compact B01 design
* [x] Check up with Ross on design
  * material - Aluminium (not happy to try invar, stainless steel)
  * job duration
  * tolerances/precision - give parts with tight tolerances to Ross during machining
  * possible mods - should be easy
* [x] Re-do wall and grating mount referencing

## 21.09.15
* [ ] B01 design evaluation
  * Commendable features
    * grating subasm is compact and easy to tune; brass pin location should allow rigid and stable mechanical stability to cavity
    * compact block and relatively short cavity
    * hermetic sealing
    * thick walls
  * Improvements
    * slip-mount subasm: hard to align XYZ; thermal and vibrational stability unsure;
    * gain-chip Z-stage should be unncessary; should keep it simple
      * gain chip to mount directly onto block, precisely located
    * decoupling fiber from gainchip by rigidly fixing at the exit port at wall

* Part selection
  * Optical isolator (fiber): refer to TODO list below
    * PISO-64-2-C-7-2-FB
  * Diffraction grating: blaze angle as close to 45 deg as possible
    * GR13-1210 - Thorlabs
  * Wedged window: minimum reflectivity at ~1083nm
    * WW11050-C14 - Thorlabs (C14 coating is slightly better than C13 coating ~1100nm)
  * Piezoelectric disc: fine tuning of cavity length and modulation; high resonance; ~3um travel

### Lab meeting
* Select appropriate optical isolator (FC): can afford two?
  * Dual stage?
  * Blocked axis?
* Bill of materials
  * all components required for assembly

### TODO
* [x] Select optical isolator and forward Andrew
  * **PISO-64-2-C-7-2-FB**: Polarization maintaining isolator, 1064nm, dual stage, 3mm cable jacket, 0.75m fiber, FC/APC, slow axis working and fast axis blocked
  * **Dual Stage** (~50dB) - Following DQS's footsteps in maximising optical isolation for a "number of situations"
  * **Fast-axis blocked** - robustly single mode and polarized 
* [x] Set up BOM 
* [x] Measure gainchip fiber connection dimensions

## 22.09.15
* Gave Ross maximum block dimensions (140x100x60mm) for preparation (21.09.15)

### TODO
* [ ] Improve mechanical design for assembly and stability before electrical connection, etc.

### Beam collimation - precise and stable lens positioning
The relative positioning of the high NA lens in all orientation (XYZ) is critical to the operation of an ECDL since the incident beam at the diffraction grating *should* be collimated. Displacement of the lens (rel to the gainchip) will have devastating effect on the ECDL since it shifts the external cavity length and also the spectral feedback from the grating. Listed below are the critical design requirements for the lens subsystem:
* **Stability**
* **Rigidity**
* **Precision**

Considering the above factors, the conceptual design (B01) will be evaluated and improved.

#### Collimation block
A separate block to rapid-protype the collimating lens location and mounting, most likely eliminating XY adjustments of the lens.

#### Lens
The *lens* must be studied first, for the design of the mounting interface must be compatible and take advantages of it.
* Size
* NA: >0.35 (2xNA_diode)
* Focal length: 5-10mm (collimated beam dia. 1.5-3mm)
* Mounting types
  * unmounted/mounted in stainless steel lens cell with metric thread
  * ~~aspheric lens adapters~~ unsuitable
* Distance from gain chip 
  * Working distance

Options:
* **C240TME-1064: f=8.07mm,NA=0.5,1064nm,WD=4.93mm(mount)**
* ~~C230TME-1064: f=4.55mm,NA=0.55,1064nm,WD=2.67mm(mount)~~

## 24.09.15
* [ ] **B02** Integrated block design
  * gainchip mounts directly on block + XYZ adjustable lens
* [ ] **D01** Separate block design
  * a separate machined block for mounting gainchip and lens
  * *slip* or *fixed lens hole* design

Selected *C240TME-1064* to be the collimating lens for its relatively large but suitable f~=8mm, WD~4mm, and **beam diameter~>2mm**.

## 25.09.15
### Wedged window-beam orientation 
Due to the orientation of the gain module and grating selection, the free-space output beam is not perpendicular to the side walls.
The C14_AR coating used in the window provides very good (<0.5%) anti-reflection properties for AOI<30deg, while our beam's AOI should be approx. 10 deg.

### Beam intensity
Calculated maximum beam intensity (~4 safety factor) is **11 W/cm^2** which is significantly lower than the window's damage threshold at CW regime.

* Reduced block size
* slot beam output

### TODO
* [x] Port for fiber output connector: requires hermetic sealing and relatively rigid fixture
  * ~~fiber chuck~~ the fixture and sealing around the black plastic tubing
  * Cord grips
  * **Slotted grip** - putty can be used to hermetic seal
* [ ] Electrical cables and DVI port
  * shield wires for isolating cross-coupling (esp. from TEC and laser diode current)
  * research commercial solutions with electrical wires
* [x] thermistor hole
* [x] Mounting the block
  * Peltier - rough dimensions
    * MOGlabs: ~40x40x5mm (block 70x70x40mm)
    * our block: ~100x100x60 
  * connection to outer block: metal bolts through plastic sleeves OR **plastic bolts**
* [x] Main block modularity: for cannister diode lasers, different gain module, lens, etc.  
* [x] **re-do** plug for collimating hole
  * a bolt
* [x] base plate and external housing design
  * elec insulated fixture - plastic sleeves | plastic bolts
* [x] PZT from Piezomechanik could be more suitable (ring design with wider profile but thinner)
* [ ] GM beam polarization direction and grating
  * emailed Innolume (Alexey Shkolnik): polarization parallel to the chip
* [ ] Research mirror mounts from Newport and compare to current mini Thorlabs 
* [ ] freespace beam dump
  * window in casing 

## 29.09.15 - 30.09.15
### Meeting: Review of design B02 and B03
* Majority favoured **B03**
* B03's reduced thermal contact and alignment should be solved
* Hermetic sealing the ecdl block with blu-tak/putty/epoxy
* Consider panel mount FC fiber connector at the outer casing by wrapping fiber around the block in casing

* Added a locating slot (Z free) in GM mount so that the M4 bolts are only for rigid fixture not locating
* Changed fixture type of GM mount to CB instead of CSK

### B03 design refinement
#### Lens tube
* [x] Dimension
  * [x] check against Thorlabs dims and fit with lens mount
* [ ] Drawing
  * [x] create and dimension drawing
  * [x] check
* [x] Send to manufacturing
* Developments
  * o-ring compression fit for lens (mounted)

#### Gainchip mount
* [x] Dimension
  * [x] check: GM, lens tube, block
* [x] Drawing
  * [x] create and dimension
  * [x] check
* [x] Manufacturing
* Devs

#### ECDL block
* [x] Dimension
  * [x] check
* [x] Drawing
  * [x] create and dim
  * [x] check
* Manufacturing
* Devs
  * Fiber output

#### block lid
* [x] Dims
  * [x] check
* [x] Drawing
  * [x] create and dim
  * [x] check
* manuf
* devs
  * engraving ANU logo etc.

### TODO
* [x] Peltier
  * [x] list
  * [x] select: APH-127-10-20-S: Peltier cooler module, 2.3A, 15.4V, 20W, 30x30x4
  * [x] update ECDL block recess for TEC
  

## 02.10.15
* Decreased O-ring groove depth to 1.2mm (from 1.3mm) - using 1.6mm o-ring
* Block and GM mount sent to Craig

## 06-08.10.15
### Purchasing
#### Optics
* [x] Fiber optic beam splitters
  * ~~POBS-64-C-3-7-2-25ER~~
  * couplers!
  * PFC-64-1-split_ratio-L-fiber_type-7-2-FB (e.g. 50,P for the 50/50 to tapered amplifiers)
  * 50/50, PM: PFC-64-1-50-L-P-7-2-FB
  * 10/90, PM: PFC-64-1-10-L-P-7-2-FB
* [x] FC connector adaptors at outer casing
  * FC connectors are narrow key (type R)
  * afwoptics: ADA-PM-22-R-S
* [ ] Lens for SAS
  * specs?
  * fiber collimating lens 

#### Electronics
* [x] thermistor
  * Epcos 10 kOhm 60mW Measurement NTC Thermistor, 15s, 2.41 Dia x 6.5mm
    * RS 706-2759
* [ ] diode protection circuitry
* [x] Peltier
  * Uniform heat flux
  * ~12W operating cooling from GM 
  * dimension: <70x70 
  * APH-127-10-25-S: 17W,1.9A, 15.4V, 30x30x4.5
    * Element14: 2466916
  * ~~Would like 4 for a wider heat flux area~~ 2 is enough. localised heat source and appropriate thermistor location
* [x] DVI panel mount connector
  * RS electronics
    * 822-3217 - right angle, 29 way
    * 822-3210 - straight, 24 way
* [x] Connector for block
  * >11 pin 
  * Piezo ~100V
  * Sensitive currents
  * Mil-spec circular connector: 12 way, high V, high I connectors
    * Box mount: 62GB-12E14-12-PN(416)
    * Cable mount: 62GB-56T14-12-SN(416)

#### MiscPH-127-10-20-S
* [x] sealant
  * Dow Corning 732 RTV

## 20.10.15
### Fiber storage reel
