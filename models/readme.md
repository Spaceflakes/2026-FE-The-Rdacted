# Models Directory (/models) - 3D CAD Files & Hardware Overview

**Team:** The Redacted  
**File Format:** 3D CAD STEP (`.step` / `.stp`)  
**License:** GNU Affero General Public License v3.0 (AGPLv3)

---

## Directory Structure & CAD File Index

This folder contains all 3D CAD models (STEP format), manufacturing jigs/molds, and hardware specifications for the vehicle assembly.

```text
models/
├── Acc/                     # Accessories & Mounting Hardware
│   ├── Raspberry Pi Mount.step  # Mounts RPi 4B to bottom 3mm carbon fiber spine rods (2x M2.5x8mm screws)
│   └── ESC Wire Mount.step      # Zip-tie routing guide for motor and ESC power leads
├── Center/                  # Central Chassis Frame & Sensor Mounts
│   ├── Top Brace.step           # Main structural chassis bridge connecting motor mount to steering column
│   ├── Bottom Left Brace.step   # Interlocking lower left brace connecting top brace to bottom carbon fiber spine
│   ├── Bottom Right Brace.step  # Interlocking lower right brace connecting top brace to bottom carbon fiber spine
│   ├── Left Bearing Mount.step  # Holds BCWG-NK12/12 needle roller bearing and left battery strap
│   ├── Right Bearing Mount.step # Holds BCWG-NK12/12 needle roller bearing and right battery strap
│   └── LiDAR & ESC Mount.step   # Platform mounting YD-LiDAR X4 Pro and Surpass 120A ESC
├── Diff/                    # Differential Gearbox Assembly (2:7 Net Reduction)
│   ├── Spider Gear.step         # 3x 9T Bevel Gears (m=1.5, 20° PA, 30.96° Bevel Angle)
│   ├── Main Gear.step           # 2x 15T Bevel Gears (m=1.5, 20° PA, 59.04° Bevel Angle)
│   ├── Spider Center.step       # Triangular carrier suspending spider gears (via 3x M3x10mm Button Head screws)
│   ├── Left Housing.step        # Left housing half with integrated 28T ring gear (houses 6901ZZ bearing)
│   ├── Right Housing.step       # Right housing half (houses 6901ZZ bearing)
│   ├── Attaching Cup.step       # Split mounting cups connecting main gears to 12mm carbon fiber rear axles
│   └── Spacer Disk.step         # PLA pre-load shim between housing and outer 6901ZZ bearings
├── Rear/                    # Rear Drivetrain & Axle Mounts
│   ├── Rear Axle Mount Front.step # Motor mount housing 3674 motor, bottom carbon rods, and M3 heat-set inserts
│   └── Rear Axle Mount Rear.step  # Rear back mount holding BCWG-NK12/12 & 6901ZZ bearings and top carbon rods
├── Screws BOM.csv           # Complete hardware Bill of Materials (screws, nuts, inserts, standoffs, bearings)
├── Steering/                # Direct-Drive Ackerman Steering Assembly
│   ├── Front Wheel Adapter Pin.step # 12mm OD capped pins with BCWN-T-d12-IR combined needle/thrust bearings
│   ├── Steering Knuckle.step    # Clamping knuckles holding thrust bearings (uses 2x M3x12mm screws & nuts per knuckle)
│   ├── Top Brace.step           # Upper steering column mount for S2500M servo and IMX219 camera
│   ├── Bottom Brace.step        # Lower steering column brace spanning wheelbase
│   ├── Side Brace.step          # Side column braces with M3 heat-set inserts
│   ├── Servo Horn.step          # Clamps to servo shaft with press-fit M3x6mm brass standoff spacer
│   ├── Servo Link.step          # Linkage arm connecting servo horn to steering rod
│   ├── Wheel Link.step          # Linkage arm connecting steering rod to steering knuckle (uses M2x20mm screw)
│   └── TPU Spacer.step          # 95A TPU shims (16mm OD x 12.8mm ID) providing pre-load on thrust bearings
├── Tools/                   # Manufacturing Jigs & Fabrication Molds
│   ├── Tire Mold.step           # 2-part SLA/FDM mold for polyurethane tires (clamps with 4x M3x30mm screws & nuts)
│   ├── Standoff Cutting Tool.step # Razor slot jig for trimming nylon standoffs to 14mm
│   ├── Axle Cutting Jig.step    # Saw guide for cutting 12mm carbon fiber tube axles to ~60mm
│   └── Axle Drilling Guide.step # Precision guide for drilling 2mm holes at 4.5mm offset on carbon fiber tubes
└── Wheel Hub.step           # 3D STEP model for custom wheel hub (18mm width, fuzzy skin tire interface)
```

## 3D Printing & Material Guidelines

* **Slicer Setup:** Orca Slicer / PreFlight using the Arachne wall engine.
* **Perimeters & Infill:** 3 perimeters (0.4 mm nominal nozzle), 25% Gyroid infill. Use 100% solid infill for steering links and TPU spacers.
* **Layer Heights:** 0.20 mm for structural chassis parts and mounts; 0.12 mm for gears, differential housing, and steering linkage parts.
* **Materials:**
  * **PLA:** Standard chassis structures, gears, housing, and mounts.
  * **TPU (95A Shore Hardness):** Front bearing stack pre-load shims (`Steering/TPU Spacer`).
  * **Resin (SLA):** Two-part polyurethane tire casting molds (`Tools/Tire Mold`).
* **Non-Printed Stock:** 12mm OD x 10mm ID roll-wrapped carbon fiber tubes (rear axles) and 3mm OD solid pultruded carbon fiber rods (spine and steering rods).

---

## Hardware Summary (Screws BOM.csv)

A complete component-by-component hardware listing is provided in `Screws BOM.csv` within this folder, including:

* **Screws:** M2x12mm, M2x20mm, M2.5x8mm, M3x8mm (Socket/CSK), M3x10mm (Socket/Button/CSK), M3x12mm, M3x16mm, M3x20mm (Socket/Button), M3x30mm.
* **Nuts & Inserts:** M2, M2.5, M3 Hex Nuts; M3x4mm and M3x6mm Brass Threaded Heat-Set Inserts.
* **Standoffs & Bearings:** M2.5x15mm Nylon Standoffs (cut to 14mm), M3x6mm Brass Standoffs, BCWN-T-d12-IR Thrust Bearings, 6901ZZ Ball Bearings, and BCWG-NK12/12 Needle Roller Bearings.

---

## License

All CAD files (`.STEP`) in this directory are released under the **GNU Affero General Public License v3.0 (AGPLv3)**. Any modified or derivative 3D models must be made publicly available under the same license terms.
