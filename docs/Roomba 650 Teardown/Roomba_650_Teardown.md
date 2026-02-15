# Roomba 650 Teardown Report

Complete disassembly documentation for reverse engineering and technical analysis.

---

## Step 1 — External Condition Documentation

![Step 1 - External Condition](Assets/Images/Step 1 - External Condition.jpg)

### Operation
Initial external documentation in unpowered state prior to disassembly.

### Mechanical Architecture

**Two-Piece Upper Housing:**
- Primary top shell: Gloss black ABS/PC blend with central control interface (CLEAN, DOCK, SPOT, CLOCK, SCHEDULE buttons)
- Gold accent ring: Cosmetic trim, likely ultrasonic-welded or snap-retained
- Front bumper assembly: Gray polymer semi-circular compliant ring with internal spring-loaded structure for collision detection

**Sensor Apertures:**
- IR windows near front arc for virtual wall detection and docking beacon reception
- Central UI cluster: Membrane switch assembly on secondary PCB beneath cosmetic plate

**Surface Condition:**
- Light scratching on gloss surface
- Minor particulate in bumper seam
- Consistent with normal consumer usage

### Electrical Architecture

**Presumed Internal Subsystems:**
- Main control PCB (microcontroller + motor drivers)
- UI PCB (button matrix + LED drivers)
- IR receiver modules
- Battery pack (14.4V NiMH, internal)
- Wheel encoder assemblies (magnetic encoders on drive motors; optical encoder on caster wheel)
- Bumper sensor microswitch array
- Cliff sensor IR pairs (underside)
- Charging contacts (underside/front)

### Design Analysis
Modular shell design provides access to battery, main PCB, speaker, and vacuum motor. Impact bumper isolated for shock absorption and obstacle detection. Cosmetic trim ring non-structural.

### Risk Assessment
Bumper contains springs/switches requiring controlled removal. Top shell secured by underside fasteners. Battery must be disconnected early to prevent shorting.

---

## Step 2 — Underside Mechanical Survey

![Step 2 - Underside Mechanical Survey](Assets/Images/Step 2 - Underside Mechanical Survey.jpg)

### Operation
Unit inverted to document baseline mechanical layout before fastener removal.

**Unit Dimensions:**
- Diameter: 340mm (13.4")
- Height: 92mm (3.6")
- Weight: 3.58kg (7.9 lbs)

### Component Identification

**1. Drive Wheel Modules (Left/Right):**
- Independent spring-loaded suspension assemblies
- Self-contained modules: DC brushed motor, reduction gearbox, magnetic encoder (tachometer type)
- Vertical compliance for obstacle climbing
- **Note:** 650 uses magnetic encoders on drive motors (older models used optical encoders that accumulated dirt)

**2. Main Brush Assembly:**
- Dual counter-rotating system: bristle brush + flexible beater brush
- Gray cage frame with yellow tool-less retention tabs
- Removable without full chassis disassembly

**3. Front Caster Wheel:**
- Passive swivel caster
- **Optical encoder underneath:** IR LED/receiver pair reads alternating black/white pattern on caster disk
- Detects direction of travel (backward/sideways movement when caster rotates off-axis)
- Axially offset from swivel shaft for directional sensing

**4. Side Brush Motor Housing:**
- Yellow retention screw cap (right side)
- Asymmetric positioning for edge cleaning
- Motor mounted beneath chassis panel

**5. Cliff Sensors:**
- IR emitter/receiver pairs behind translucent windows
- Front-biased positioning for early edge detection
- JST-style connectors to main PCB

**6. Charging Contacts:**
- Two rectangular conductive pads (front underside)
- Direct electrical interface to dock
- Routed to charging circuit on main PCB

**7. Battery Compartment:**
- Central panel with screw retention
- Houses 14.4V NiMH pack

**8. Perimeter Fasteners:**
- Multiple Phillips screws securing lower chassis to upper shell

### Electrical Subsystems
Two drive motors, vacuum motor (internal), side brush motor, brush deck motor, cliff sensor IR circuits, charging input. Central main PCB architecture above battery cavity.

### Risk Assessment
Drive modules spring-loaded; control extraction to prevent wiring stress. Avoid scratching cliff sensor windows. Battery removal required early for electrical isolation.

---

## Step 3 — Dust Bin Removal

![Step 3 - Dust Bin Removal](Assets/Images/Step 3 - Dust Bin Removal.jpg)

### Operation
Rear dust bin assembly removed via top-mounted release latch. Slides rearward along guide rails and disengages from suction port.

### Construction

**Dust Bin Assembly:**
- Molded polymer enclosure with integrated filter housing
- Internal debris cavity (0.6L capacity)
- Forward-facing suction inlet with compressible seal
- No electrical contacts (basic model variant)

**Chassis Interface:**
- Rear cavity with internal air duct inlet
- Mechanical guide tracks for alignment

**Airflow Path:**
Brush Deck → Internal Plenum → Vacuum Motor → Dust Bin → Exhaust Filter → Atmosphere

### Design Analysis
Tool-less removal for routine maintenance. Modular airflow containment independent of structural shell. Rear extraction avoids drive wheel interference.

### Risk Assessment
Debris on seal surface reduces efficiency. Misalignment during reinstallation impacts suction. Repeated removal wears guide rails.

---

## Step 4 — Bottom Chassis Plate and Battery Removal

![Step 4 - Bottom Chassis Plate and Battery Removal](Assets/Images/Step 4 - Bottom Chassis Plate and Battery Removal.jpg)

### Operation
Perimeter screws removed. Bottom plate separated, exposing internal architecture. Battery pack extracted from central cavity.

### Bottom Plate Assembly

**Construction:**
- Injection-molded polymer with internal ribbing
- Integrated cliff sensor windows, caster opening, charging contact alignment
- No embedded electronics

**Exposed Internal Architecture:**
1. Drive wheel modules: Blue housings with spring-loaded vertical travel
2. Brush deck assembly: Gray cage with blue retention brackets
3. Battery cavity: Central bay with dual metal spring contacts
4. Side brush motor: Yellow cap/screw (right front quadrant)
5. Front caster: Mounted to main chassis

### Battery Pack Specifications

**Type:** NiMH multi-cell pack  
**Nominal Voltage:** 14.4V (verified across all 600-series models)  
**Typical Capacity:** 
- OEM: 2000-3000mAh
- Aftermarket: 2800-4500mAh (higher capacity available, may be physically larger)

**Cell Configuration:** External housing encloses cylindrical cells; no external BMS (regulation on main PCB)  
**Charging Input:** 22.5V DC @ 1.5A from dock (center contact: +, barrel contact: -)

Battery removal achieves full system power isolation.

### Power Distribution Architecture

Battery → Main PCB Power Regulation →
- Left motor driver
- Right motor driver
- Brush motor driver
- Vacuum motor driver
- Side brush motor driver
- Sensor rail (5V/3.3V regulated logic)

### Design Analysis
Bottom plate provides structural closure. Wheel modules independently replaceable. Battery centrally located for mass distribution. Electrical contacts chassis-mounted to avoid stress during pack removal.

### Risk Assessment
Wheel modules under spring tension; avoid lateral force. Battery contacts exposed; prevent shorting. Wiring harness routed above current layer; trace before lifting assemblies.

---

## Step 5 — Main Brush Removal

![Step 5 - Main Brush Removal](Assets/Images/Step 5 - Main Brush Removal.jpg)

### Operation
Dual counter-rotating brushes removed using yellow retention tabs. Brush shafts lifted vertically from bearing seats and drive couplings.

### Brush Assembly Details

**1. Primary Bristle Brush:**
- Cylindrical core with helical bristle rows
- Yellow end caps with keyed drive interface (hex or D-shaped socket)
- One end driven, opposite end free-rotating bearing

**2. Flexible Beater Brush:**
- Elastomeric flaps arranged helically for carpet agitation
- Similar keyed drive interface

**Brush Deck Module:**
- Gray molded housing forming lower airflow plenum
- Two longitudinal brush channels
- Central debris opening routes upward to vacuum inlet
- Yellow latching points for tool-less maintenance
- **Dirt Detect Sensor:** Bronze-colored piezoelectric acoustic disc mounted in brush cage (detects debris impacts, triggers intensive cleaning mode)

### Drive Mechanism

Single brush motor drives both brushes via internal geartrain. Mechanical synchronization (not electronic). Brush motor: brushed DC type, PWM-controlled from main PCB. No encoders on brush assembly in 600-series.

**Electrical Path:**
Main PCB → Brush Motor Driver → Brush Motor → Geartrain → Dual Brush Outputs

### Design Analysis
User-removable brushes without tools. Single-motor dual-brush drive simplifies mechanics. Standardized shaft ends for modular replacement. Airflow engineered to concentrate debris at central intake.

### Risk Assessment
Hair accumulation at bearings increases torque load. Drive-side coupling susceptible to wear. Misalignment during reinstallation may damage keyed interface.

---

## Step 6 — Brush Deck Module Removal

![Step 6 - Brush Deck Module Removal](Assets/Images/Step 6 - Brush Deck Module Removal.jpg)

### Operation
Complete brush deck module detached after electrical connector disengagement. Module includes dual brush channels, geartrain, integrated motor, and debris intake throat.

### Module Construction

**Brush Deck (Self-Contained Assembly):**
- Blue structural side arms as mounting brackets
- Yellow service interface components
- Rear circular outlet port connects to suction plenum when installed

**Chassis Interior (Exposed):**
- Large central cavity with airflow channel to vacuum motor
- Mounting bosses for deck module
- Structural ribbing along internal floor

### Mounting Architecture
Multiple screws into chassis bosses. Molded locating tabs for alignment. JST-style connector for brush motor (two-wire brushed DC connection).

**Motor Type:** Brushed DC  
**Control:** H-bridge or low-side switching from main PCB  
**Feedback:** No closed-loop rotation sensing in this generation

### Design Analysis
High modularity; brush deck as replaceable service unit. Separation of agitation from airflow motor. Independent mounts reduce stress on main PCB. Optimized airflow path lifts debris directly into suction throat.

### Risk Assessment
Wiring harness strain may damage connector. Internal geartrain wear not externally visible. Improper reseating creates air leakage.

---

## Step 7 — Side Brush Motor Disassembly

![Step 7 - Side Brush Motor Disassembly](Assets/Images/Step 7 - Side Brush Motor Disassembly.jpg)

### Operation
Side brush removed via central Phillips screw. Motor assembly extracted and gearbox housing opened to expose reduction geartrain.

### Assembly Architecture

**1. External Removal:**
- Single central screw through brush hub
- Brush hub mounts to motor output shaft (D-shaped or splined interface)

**2. Motor Module:**
- Self-contained motor + gearbox (blue housing)
- Mounted in right-front chassis quadrant
- Wiring harness to main PCB

**3. Gearbox Internals:**
- Brushed DC motor (silver cylindrical can)
- Multi-stage spur gear reduction (high ratio for torque/speed reduction)
- Plastic gears (noise reduction, cost optimization)
- Light grease application
- Two-piece clamshell housing with integrated bearing seats

**Motor Specifications:**
- Type: Brushed DC
- Voltage: 14.4V nominal
- Current: ~200-400mA typical under load
- Connection: Two-wire
- Control: Low-side switching or H-bridge from main PCB
- Feedback: None (no encoder/positional sensing)
- Current monitoring: Indirect via main board for stall detection

### Design Analysis
Dedicated motor independent of main brush system. Gear reduction optimized for torque. Modular assembly enables replacement without full disassembly. Plastic geartrain reduces acoustic signature.

### Risk Assessment
Hair intrusion into output bearing increases friction. Plastic gear wear under stall conditions. Over-torque during reassembly cracks housing.

---

## Step 8 — Drive Wheel Module Removal

![Step 8 - Drive Wheel Module Removal](Assets/Images/Step 8 - Drive Wheel Module Removal.jpg)

### Operation
Left and right drive wheel modules disconnected and removed as complete assemblies after electrical connector disengagement.

### Module Construction

Each module contains:
- DC brushed drive motor (14.4V nominal operating voltage)
- **4-stage reduction gearbox** (confirmed via teardown analysis)
  - High gear reduction for torque amplification
  - Heavy grease lubrication
  - Plastic gears for noise reduction
- Output shaft directly coupled to wheel hub
- Integrated suspension mechanism (large compression spring)
- **Magnetic encoder** (tachometer on motor shaft, replaces older optical encoders)
- **Snap action switch** (normally pressed; opens when wheel lifted, triggers safety cutoff)

### Mounting & Suspension

**Mounting:**
- Modules seated vertically in molded chassis bays
- Screw retention at base/side bosses
- Spring-loaded vertical compliance for obstacle climbing
- Chassis opening provides clearance for vertical motion

**Gearbox:**
- High torque output for obstacle climbing and differential steering
- Wheel hub direct-coupled to gearbox output
- Internal lubrication (grease)

### Electrical Architecture

**Per Module Connections:**
- 2 motor power leads (14.4V from battery rail)
- 2 encoder feedback leads (magnetic encoder signals)

**Motor Specifications:**
- Type: DC brushed motor
- Voltage: 14.4V nominal
- Current: ~200-600mA per motor under normal load (higher indicates stall)
- Recommended H-bridge: 600mA minimum per channel; 2A for heavier applications

**Encoder Type:** Magnetic encoder (tachometer function)  
**Purpose:** Speed measurement for closed-loop velocity control and odometry  
**Advantage over optical:** Dirt-resistant (older models' optical encoders accumulated dust)

**Control Strategy:**
Main PCB → Dual H-bridge motor driver → Drive Motors  
Main PCB ← Encoder pulses (speed feedback)

**Control Features:**
- Differential speed modulation for turning
- Stall detection via current monitoring
- Basic closed-loop velocity control

### Design Analysis
Fully modular drive architecture. Independent removal simplifies service. Integrated suspension improves traction. Magnetic encoder enables dead-reckoning navigation. Structural separation prevents motor vibration transfer to PCB.

**Safety Feature:** Each wheel module contains a snap action switch (normally pressed during operation). When both switches open simultaneously (e.g., unit lifted), Roomba cuts power to wheel motors and emits audio alert. Prevents damage from accidental wheel operation when unit is handled.

### Risk Assessment
Encoder wiring fragile during removal. Gear wear under prolonged high-torque operation. Spring fatigue reduces climbing capability.

---

## Step 9 — Front Bumper Removal

![Step 9 - Front Bumper Removal](Assets/Images/Step 9 - Front Bumper Removal.jpg)

### Operation
Front compliant bumper ring detached via screw/clip release. Semi-circular component separated from chassis perimeter.

### Bumper Construction

**Assembly:**
- Molded polymer shell with internal ribbing
- Semi-circular geometry covering forward 180° arc
- Internal mounting posts, spring seats, actuation tabs

**Chassis Interface:**
- Perimeter frame mounting (screws + snap features)
- Clearance gap indicates floating design
- Contact tabs engage internal microswitches on chassis

### Collision Detection Mechanism

**Mechanical Operation:**
1. Impact displaces bumper
2. Spring compression
3. Internal tabs actuate microswitches
4. Switch state monitored by main PCB

**Wall Detection Sensors:**
- **Six IR LED/receiver pairs** mounted on front bumper subassembly bracket
- Enable wall-following behavior without contact
- Allow Roomba to "see" walls and furniture
- Roomba slows before light contact using these sensors

**Electrical Sensing:**
- Bumper: Mechanical actuation only (no embedded electronics)
- Switches: Mounted on chassis, not bumper
- Purely mechanical transmission from bumper to switches

**Internal Frame Ring (Exposed):**
- Structural mid-frame (black circular frame)
- Load-bearing outer support
- Mounting interface for bumper and top shell
- Symmetrical screw boss distribution

### Design Analysis
Floating bumper enables early obstacle detection. Wide forward arc increases coverage. Mechanical simplicity reduces sensor complexity. Separation of structural ring and cosmetic shell improves modularity.

### Risk Assessment
Spring misalignment may cause false triggers; avoid stressing plastic tabs during reinstallation.

---

## Step 10 — Cosmetic Top Cover Removal

![Step 10 - Cosmetic Top Cover Removal](Assets/Images/Step 10 - Cosmetic Top Cover Removal.jpg)

### Operation
Gloss cosmetic top cover removed after screw/snap release. Upper structural plate with UI assembly now exposed.

### Layer Separation

**Cosmetic Top Cover:**
- High-gloss molded polymer (non-structural)
- Large central aperture for control interface
- Perimeter screws + internal snap tabs
- No embedded electronics

**Exposed Upper Structural Plate:**
- Matte-finish molded polymer
- Button interface assembly
- Speaker port (right of center cluster)
- Radially distributed mounting screws for internal electronics

**User Interface Cluster:**
- Central circular button assembly on structural plate
- Elastomeric membrane contacts or tactile dome switches
- Light pipes for LED indicators
- Gold trim ring attached to structural layer

### Design Analysis
Clear layer hierarchy: decorative surface → structural plate → electronic control layer. Modular UI cluster centered for mechanical symmetry. Light pipe design minimizes PCB complexity.

### Risk Assessment
Snap tab fracture during removal. Over-tightening strips plastic bosses. Light pipes may dislodge if plate separated abruptly.

---

## Step 11 — Upper Structural Shell Removal

![Step 11 - Upper Structural Shell Removal](Assets/Images/Step 11 - Upper Structural Shell Removal.jpg)

### Operation
Upper structural shell separated after screw removal. Shell lifted vertically to avoid wiring strain. Main control PCB and internal wiring exposed.

### Structural Components

**Removed Upper Shell:**
- Injection-molded with internal ribbing
- Mounting bosses for PCB
- Wire routing channels
- Acts as mechanical carrier for UI cluster

**Main PCB (Exposed):**
- Large circular/segmented board (central upper layer)
- White solder mask surface
- Distributed SMD components
- Multiple mounting screws to chassis

### PCB Architecture

**Visible Subsystems:**
- Central microcontroller (likely BGA or QFP package)
- Motor driver ICs (H-bridge packages)
- Voltage regulation circuitry
- Sensor interface circuits
- LED driver sections (aligned with button cluster)

**Button Array:**
- Central circular assembly mechanically aligned to PCB
- Tactile dome switches or elastomeric membrane
- LED indicators beneath translucent light guides
- Screw/plastic post retention

**Wiring Harnesses:**
- Red/black twisted pairs (motor power)
- JST-style friction-fit connectors
- Routed along perimeter frame to: drive modules, side brush, vacuum motor, sensors, charging contacts

### Electrical Architecture

**Power Distribution:**
Battery → Power Regulation →
- 5V logic rail
- 3.3V MCU rail
- Motor supply rail (14.4V)

**MCU Responsibilities:**
- Wheel encoder processing
- Motor PWM generation
- Cliff sensor monitoring
- Bumper switch detection
- Docking IR decoding
- User interface management

**Board Design:**
- No RF shielding (non-WiFi variant)
- Single main logic board (not distributed architecture)
- Radial layout optimized for circular chassis

### Design Analysis
Centralized PCB reduces cost. Radial component distribution matches chassis geometry. Perimeter wiring avoids airflow cavity interference. Structural shell doubles as PCB mount. Integrated button/logic board reduces inter-board connectors.

### Risk Assessment
Wire harness damage during shell lift. PCB stress from uneven screw removal. ESD risk to exposed ICs.

---

## Step 12 — Button Array Removal and Full PCB Exposure

![Step 12 - Button Array Removal and Full PCB Exposure](Assets/Images/Step 12 - Button Array Removal and Full PCB Exposure.jpg)

### Operation
Button array and UI trim removed from PCB. Retaining screws extracted, alignment posts disengaged. Underlying PCB and component layout fully exposed.

### UI Assembly (Removed)

**Multi-Layer Structure:**
- Decorative faceplate
- Button cap cluster (CLEAN, SPOT, DOCK, SCHEDULE, CLOCK)
- Light guide elements (transparent/translucent plastic)
- Mechanical support frame

**Interface Mechanism:**
- Button caps actuate PCB-mounted tactile switches
- Light pipes distribute LED illumination to labeled regions

### Main PCB (Fully Exposed)

**Board Details:**
- Single large circular logic board
- Multiple evenly distributed mounting screws
- White solder mask surface

**Component Population:**
- Central MCU (ARM-based or 8/16-bit microcontroller)
- Motor driver ICs (H-bridge packages for differential drive)
- Voltage regulators (buck converters for logic rails)
- Current sensing components
- Sensor interface circuits (comparators for cliff sensors)
- Discrete passives and filtering networks

**Visible Elements:**
- Multiple green LED emitters (aligned with UI zones)
- Central white circular area (speaker/piezo alignment)
- Front-edge sensor board (cliff sensors/docking IR receiver)
- JST connectors along lower edge

**Front Sensor Board:**
- Separate narrow PCB near front underside
- IR components (cliff sensors, docking beacon receiver)
- Twisted pair wiring to main board

### Electrical System Architecture

**Power Architecture:**
Battery → Power Regulation →
- Logic rail: 3.3V or 5V
- Motor supply: 14.4V (battery direct)

**Subsystem Routing:**
- Drive motors: Dual H-bridge driver ICs
- Side brush/main brush: Low-side switching or discrete drivers
- Vacuum motor: Higher-current MOSFET stage
- Cliff sensors: Analog or comparator circuits
- Bumper switches: Digital GPIO inputs
- Speaker: Small amplifier circuit

**Board Characteristics:**
- Single-layer control architecture (no separate power board)
- Non-WiFi variant (no RF module)
- Radial component distribution for circular chassis
- Consolidated UI/logic integration reduces BOM

### Design Analysis
Consolidated PCB reduces interconnect complexity. Radial distribution aligns with chassis constraints. UI/logic integration lowers cost. Modular front sensor PCB simplifies bumper integration. Twisted motor wiring reduces EMI.

### Risk Assessment
ESD exposure highest at this stage. Screw removal sequence should avoid PCB flex. Wire harness strain during PCB lift may damage JST connectors.

---

## Technical Corrections Summary

### Verified Specifications

**Battery:**
- Voltage: 14.4V (confirmed across all sources)
- Chemistry: NiMH (Nickel Metal Hydride)
- Capacity: 2000-3500mAh (varies by OEM/aftermarket)
- Cell configuration: Multi-cell cylindrical pack

**Motors:**
- All motors: Brushed DC type
- Operating voltage: 14.4V nominal (from battery rail)
- Drive motors: ~200-600mA per motor under normal load
- Encoders: Magnetic encoders (not optical) on drive motors per 650 architecture

**Sensors:**
- Cliff sensors: IR emitter/receiver pairs
- Bumper sensors: Mechanical actuation → microswitch closure
- Top IR sensor: Docking beacon/virtual wall detection
- Wall sensors: IR LED/receiver pairs (6 total)
- Dirt detect: Piezoelectric acoustic sensor in brush cage

**Dimensions:**
- Diameter: 340mm (13.4")
- Height: 92mm (3.6")
- Weight: 3.58kg (7.9 lbs)

### Key Corrections to Original Documentation

1. **Battery voltage confirmed as 14.4V** (document stated "14.4V typical" - confirmed accurate)
2. **Encoder type: Magnetic encoders** on drive motors, not optical (older models used optical, 650 uses magnetic)
3. **Caster wheel contains optical encoder** underneath (alternating black/white pattern for direction detection)
4. **Dirt detect sensor: Piezoelectric acoustic** (bronze disc in brush cage, not mentioned in original)
5. **Wall sensors: Six IR pairs** mounted on front bumper subassembly bracket
6. **No WiFi module** in this generation (650 is non-connected variant)
7. **Dust bin capacity: 0.6L** (not specified in original)

---

## Notes for Reverse Engineering

### Power System
- Main power rail: 14.4V direct from battery
- Logic rails: 5V and/or 3.3V derived from buck converters on main PCB
- No external BMS on battery pack; regulation handled on main PCB
- Charging input: 22.5V DC @ 1.5A from dock (per external sources)

### Motor Control
- Drive motors: Dual H-bridge configuration for independent left/right control
- Differential steering via speed modulation
- Stall detection via current monitoring
- Basic closed-loop velocity control using magnetic encoder feedback
- No sophisticated odometry beyond basic encoder counting

### Navigation System
- **iAdapt Navigation (Generation 1)** - first-generation reactive navigation
- Random walk cleaning pattern with wall-following behavior
- **No room mapping capability** (contrast with iAdapt 2.0+ in 900-series using vSLAM)
- IR-based obstacle detection (no LIDAR/camera)
- Mechanical bumper for contact-based obstacle confirmation

**Sensor Suite:**
- **Cliff sensors:** IR emitter/receiver pairs on underside (stair/drop-off detection)
- **Wall sensors:** Six IR LED/receiver pairs on front bumper bracket (proximity without contact)
- **Top IR sensor:** 360° light guide for docking beacon and virtual wall detection
- **Bumper switches:** Mechanical microswitches for collision confirmation
- **Caster encoder:** Optical encoder underneath caster for directional movement detection
- **Drive encoders:** Magnetic encoders on drive motors for odometry and speed control
- **Dirt detect:** Piezoelectric sensor in brush cage for debris concentration detection

**Control Strategy:**
- Basic closed-loop velocity control using magnetic encoder feedback
- Simple odometry via encoder pulse counting (no sophisticated SLAM)
- Reactive navigation (responds to immediate sensor input, no path planning)

### Modularity Assessment
All major subsystems designed for user or service-level replacement:
- Battery (consumer-replaceable)
- Brushes (tool-less user service)
- Drive wheel modules (service-replaceable units)
- Brush deck assembly (service module)
- Side brush motor (service-replaceable)
- Dust bin and filter (consumer maintenance)

### Design Philosophy
600-series architecture prioritizes:
- Serviceability over integration
- Mechanical simplicity over sensor sophistication
- Cost optimization (plastic gearing, single main PCB, no WiFi)
- User maintenance access (clearly marked screws, snap features)

---

## Complete Technical Specifications Reference

### Physical Specifications
| Parameter | Value |
|-----------|-------|
| Diameter | 340mm (13.4") |
| Height | 92mm (3.6") |
| Weight | 3.58kg (7.9 lbs) |
| Dust bin capacity | 0.6L |

### Electrical Specifications

**Battery System:**
- Voltage: 14.4V nominal
- Chemistry: NiMH (Nickel Metal Hydride)
- Capacity: 2000-3000mAh (OEM), up to 4500mAh (aftermarket)
- Cell type: Cylindrical cells in external housing
- BMS: None on pack; regulation on main PCB
- Charging: 22.5V DC @ 1.5A from dock

**Power Rails:**
- Motor supply: 14.4V (direct from battery)
- Logic rail: 5V and/or 3.3V (buck converters)

**Motor Specifications:**
| Motor | Type | Voltage | Current (typical) | Control |
|-------|------|---------|-------------------|---------|
| Drive motors (2x) | Brushed DC | 14.4V | 200-600mA each | Dual H-bridge |
| Brush motor | Brushed DC | 14.4V | ~400-800mA | H-bridge/low-side |
| Side brush motor | Brushed DC | 14.4V | 200-400mA | Low-side/H-bridge |
| Vacuum motor | Brushed DC | 14.4V | ~1-2A | High-current MOSFET |

### Sensor Specifications

**Cliff Sensors:**
- Type: IR emitter/receiver pairs
- Location: Bottom surface (front-biased)
- Function: Stair/drop-off detection

**Wall Sensors:**
- Type: IR LED/receiver pairs
- Quantity: 6 pairs
- Location: Front bumper subassembly bracket
- Function: Proximity detection without contact

**Bumper Sensors:**
- Type: Mechanical microswitches
- Actuation: Via bumper displacement
- Function: Collision confirmation

**Top IR Sensor:**
- Type: IR receiver with 360° light guide
- Function: Docking beacon and virtual wall detection

**Encoders:**
- Drive motors: Magnetic encoders (tachometer type)
- Caster wheel: Optical encoder (black/white pattern)
- Function: Speed control, odometry, direction detection

**Dirt Detect Sensor:**
- Type: Piezoelectric acoustic sensor
- Location: Bronze disc in brush cage
- Function: Debris impact detection triggers intensive cleaning

### Mechanical Specifications

**Drive System:**
- Configuration: Differential drive (2 independent wheels)
- Gearbox: 4-stage reduction per wheel
- Suspension: Spring-loaded vertical compliance
- Safety: Snap action switches (power cutoff when lifted)

**Brush System:**
- Main brushes: Dual counter-rotating (bristle + beater)
- Drive: Single motor via geartrain
- Side brush: Independent motor with gear reduction

**Navigation:**
- System: iAdapt (Generation 1, reactive)
- Cleaning pattern: Random walk with wall-following
- Mapping: None (no SLAM capability)

---

**Document Version:** 2.0 (Technical Corrections Integrated)  
**Last Updated:** February 2026  
**Model:** iRobot Roomba 650 (4th Generation, Released August 2012)  
**Purpose:** Reverse engineering and technical analysis
