# WRO-2026

# The Redacted
<img width="2160" height="1620" alt="logo" src="https://github.com/user-attachments/assets/49680355-e819-4500-abdb-3093ef056ef4" />

**The official repository of The Redacted for WRO - Future Engineers 2026**

## Content

### Folders
- **Engineering Manual:** Official manual of team The Redacted for WRO FE 26 (manual.pdf). Contains component selection, CAD, PCB schematics, and assembly guides.
- **PCBA:** Complete set of KiCad PCB files, manufacturing outputs (Gerbers), interactive HTML BOM, and documentation.
- **t-photos:** Team photos (1 formal, 2 informal).
- **v-photos:** 6 photos of the vehicle (front, back, left, right, top, bottom).
- **video:** video.md file with the official vehicle demonstration video link.
- **schemes:** Schematic diagrams, motor connections, power distribution, and 3D PCB renders.
- **src:** ROS 2 control software nodes (motion, LiDAR, camera/vision, parking logic).
- **models:** 3D CAD model files (STEP format).

### Index
- [The Redacted](#the-redacted)
- [Vehicle Photos and Video](#vehicle-photos-and-video)
- [Hardware Materials](#hardware-materials)
- [Mobility Management](#mobility-management)
- [Design](#design)
- [Power Management and Sense Management](#power-management-and-sense-management)
- [Schematic Diagram](#schematic-diagram)
- [Obstacle Management](#obstacle-management)
- [Our Journal](#our-journal)
- [Gantt Chart](#gantt-chart)

---

## The Redacted

### Members
1. **Anvay Jain**  
   Grade 9, The Sanskaar Valley School. Head of this repository. Interested in Space, Science, KSP, and Mathematics.
2. **Siddesh Jain**  
   12th Grader, Billabong High International School. Lead engineer/development head. CAD, hardware, system architecture.
3. **Prayash**  
   Co-engineer and robotics developer. Software integration, testing, and mechanical assembly.

### Team Pictures
#### Formal
![Formal Team Photo](path/to/formal_photo.jpg)

#### Informal
![Informal Team Photo 1](path/to/informal_1.jpg)  
![Informal Team Photo 2](path/to/informal_2.jpg)

---

# Vehicle Photos and Video

### Photos
Vehicle photographs showing all 6 sides are available in the [/v-photos](./v-photos) folder.

### Videos
The demonstration video link and operational breakdown are located in [/video/video.md](./video/video.md).

---

## Hardware Materials

| Name | Link |
| :--- | :--- |
| Rpi 4B/5 | [Link](https://www.raspberrypi.com/products/raspberry-pi-5) |
| LiDAR | [Link](https://robu.in/product/ydlidar-x4-pro-360-degree-ros-scanner-for-navigation-collision-avoidance-10m/#tab-specification) |
| Servo | [Link](https://robu.in/product/surpass-hobby-25kg-s2500m-servo/) |
| Wheels | [Link](https://robu.in/product/65mm-robot-smart-car-12-rim-wheel-blue/) |
| Pi Camera | [Link](https://robu.in/product/arducam-8mp-imx219-175-degree-ultra-wide-angle-raspberry-pi-camera-module-compatible-with-raspberry-pi-4-model-b-pi-3-3b-and-pi-zero-2w/) |
| Custom 2026 WRO Hat PCB | [Link](https://github.com/The-Redacted/WRO-2026/tree/main/PCBA) |
| ESC + Motor | [Link](https://www.hobbywingdirect.com/collections/quicrun-brushless-system/products/quicrun-wp-10bl120-sl-system-g2?variant=41474386854003) |
| Battery | 2x DOGCOM 4S 850 mAh 150C LiPo |
| Gears | Custom 3D Printed Bevel Gears |
| PCB Components | TI LM61460 (5.15V @ 6A) & TPS62932 (8V @ 2A) |
| Carbon Fiber Stock | 12mm OD x 10mm ID Tubes & 3mm OD Rods |

### PCB Design & Prototype PCB
#### Prototype PCB
- **Issue:** Standard 5.0V buck converters caused under-voltage warnings on the Pi 4B under load.
- **Solution:** Designed 2026 WRO Hat for a stabilized 5.15V rail at 6A using the TI LM61460.
- **LC Hot-Plug Fix:** Added a 1000 µF electrolytic capacitor between switch output and GND to dissipate inrush energy and prevent voltage ringing.

#### PCB Design
- **4-Layer Stackup:**
    - Layer 1: High-speed switching/control.
    - Layer 2: Ground plane.
    - Layer 3: Power planes (BATT, 5.15V, 8.0V).
    - Layer 4: Ground plane and secondary signals.

---

## Mobility Management
- **Drive System:** Surpass Hobby 3674 1700KV brushless motor + 120A 4S ESC.
- **Differential Gearbox:** 3D-printed, 2:7 gear reduction ratio.
- **Steering:** Direct-drive Ackerman system with S2500M 25 kg-cm servo on 8V rail.
- **Bearing/Axle Support:** Needle roller/thrust bearings for front knuckles; carbon fiber tubes for rear axles.

---

## Design
- **Wheelbase:** 184.3 mm.
- **Width:** <180 mm.
- **Height:** <80 mm.
- **Chassis:** Carbon fiber rods for structural rigidity.

---

## Power Management and Sense Management

### Power Management
- **Battery:** 2x DOGCOM 4S 850 mAh LiPo in parallel (1700 mAh total).
- **5.15V Rail:** TI LM61460 (6A) for RPi 4B and LiDAR.
- **8.0V Rail:** TI TPS62932 (2A) for steering servo.

### Sense Management
- **YD-LiDAR X4 Pro:** 360° 2D Laser Range Finder for mapping/navigation.
- **Arducam IMX219:** 175° FOV camera for pillar color classification.

---

## Schematic Diagram
- **Power Input:** XT30 connector (14.8V–16.8V).
- **Interfaces:** RPi 4B GPIO, USB (LiDAR), CSI (Camera), Expansion Ports (ToF sensors).

---

## Obstacle Management

### Strategy
Uses ROS 2 for modularity, combining LiDAR for 3D mapping and Camera for 2D pillar color classification.

### Logic
- **Round 1 (Open):** Wall-following via LiDAR and lane maintenance.
- **Round 2 (Obstacle):** Pillar detection -> Camera classification -> Dynamic path planning.
- **Parking:** Automated sequence using LiDAR/Camera boundary detection and PID feedback.

---

## Our Journal
- **June:** Strategy, sensing evaluation, concept sketches.
- **July:** CAD modeling, PCB design, tire molding, printing.
- **August:** Assembly, PCB reflow, ROS 2 software development, documentation.

**The journal is one of the most detailed description and accounts for all the decision made. It should most definitely be read.**

---

## Gantt Chart

| Task / Milestone | June | July | August |
| :--- | :--- | :--- | :--- |
| Concept & Selection | X | | |
| 3D CAD Modeling | | X | |
| KiCad PCB Design | | X | |
| SLA Tire Molds | | X | |
| 3D Print & Assembly | | X | X |
| PCB & Reflow | | | X |
| ROS 2 Software | | | X |
| Integration & Testing | | | X |
