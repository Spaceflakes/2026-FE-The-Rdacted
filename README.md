<div align="center">
	
# WRO-2026

# The Redacted


**_The official repository of The Redacted for WRO - Future Engineers 2026_**
</div>
	
## Content
### **Folders**
* `Engineering Manual` is the official manual of team The Redacted for WRO FE 26. It contains the diagrams and details of all the CAD and parts used.
* `PCBA` contains the complete set of KiCad Printed Circuit Board (PCB) files, manufacturing outputs, and documentation required to view, modify, assemble, and produce this board.
* `t-photos` contains 1 formal image and 2 informal images
* `v-photos` contains 6 photos of the vehicle (from every side, from top and bottom)
* `video` contains the video.md file with the link to a video where driving demonstration exists
* `schemes` contains schematic diagrams of components illustrating all the elements (electronic components and motors) used in the vehicle and how they connect to each other, along with the models of the PCB.
* `src` contains code of control software for all components which were programmed to participate in the competition
* `models` is for the files for 3D models used by to produce the vehicle elements.

### **Index**
 [The Redacted](#The-Redacted) 
   
   - Members
   
   - Small introduction to them

   - Team Pictures

[Vehicle Photos and Video](#Vehicle-Photos-and-Video)

- Shows the vehicle from all 6 sides and shows a sample video of it working
   
 [Hardware Materials](#Hardware-Materials)

 - Name of parts

 - Links

 - Rate per part

 [Mobility Management](#Mobility-Management)
 
 - Gives an overview of our bots parts

[Design](#Design)

- Tells how every component is placed. 

[Power Management and Sense Management](#Power-Management-and-Sense-Management)

  - Gives an overview about the power consumption of our bot and use of each sensor

[Schematic Diagram](#Schematic-Diagram)

 - Shows all connections between the parts

[Obstacle Management](#Obstacle-Management)

- Basic overview of our strategy

- Shows our logic for dectecing the pillars and parking logic

[Our Journal](#Our-Journal)

- Tells our jounery making the bot


## The Redacted
Members:
1) Anvay Jain

In Grade 9 at the Sanskaar Valley School, proud brother of Siddesh, and head of this repo. First time in participation, but second time visiting the Competition... I like Space, Science, and KSP and math.

2) Siddesh Jain

12th Grader in Billabong High, third time in WRO, the lead engineer and the head of the developement team, responsible for the CAD and all the choices. Races FPV drones and likes math.
   
3) Prayash

Space for your bio


### Team Pictures


#### Formal


#### Informal



# Vehicle Photos and Video

#### Photos



#### Videos



## Hardware Materials

| Name |	Link |
|------|------|
| Rpi 4B/5	| https://www.raspberrypi.com/products/raspberry-pi-5 |
| LiDAR	| https://robu.in/product/ydlidar-x4-pro-360-degree-ros-scanner-for-navigation-collision-avoidance-10m/#tab-specification|
| Servo	| https://robu.in/product/surpass-hobby-25kg-s2500m-servo/	|	
| Wheels |	https://robu.in/product/65mm-robot-smart-car-12-rim-wheel-blue/ |	167 |	
| Pi Camera	| https://robu.in/product/arducam-8mp-imx219-175-degree-ultra-wide-angle-raspberry-pi-camera-module-compatible-with-raspberry-pi-4-model-b-pi-3-3b-and-pi-zero-2w/ |
|Stepdown Module | https://robu.in/product/mini560-dc-5v-5a-step-down-stabilized-module/ |\	
| ESC + Motor |	https://www.hobbywingdirect.com/collections/quicrun-brushless-system/products/quicrun-wp-10bl120-sl-system-g2?variant=41474386854003 |
| Battery |	- |	
| Gears | - |		
| PCB | - |		
| CF | - |

### PCB Design & Prototype PCB

##### Prototype PCB


##### PCB Design


							

## Mobility Management



 ## Design




## Power Management and Sense Management




## Schematic Diagram


## Obstacle Management

### Strategy

1) We are using a mix of LiDAR and the Pi Camera sensors which enables obstacle avoidance.

- LiDAR offers highly accurate 3D mapping, critical for safe navigation and obstacle detection.

- Cameras provide detailed 2D imagery, that complements the 3D data from LiDAR.
  
2) We are using ROS 2 as our main programming framework because it provides a modular and real-time system that connects all our sensors efficiently. This setup ensures smooth communication and coordination between the hardware and software, allowing our system to respond quickly and reliably. Additionally, ROS 2 makes it easy to expand and add new features as the project grows. Overall, ROS 2 gives us a flexible and robust platform suited for developing our project.

By combining these technologies, we achieve a robust perception system that enhances accuracy, safety, and reliability in autonomous vehicle operation.

### Logic
Open Challenge (Round 1)
1) ROS 2 Node Initialization

   - All system modules and ROS 2 nodes (including motion, perception, and sensor fusion) are launched.

2) Start Switch Monitoring

   - The robot waits in an idle state until it receives the official start switch input.

3) Lane Navigation & Dynamic Obstacle Avoidance Loop

- The vehicle drives forward, continuously evaluating the distances to the side walls.

- If both sides readings > 2.8m, the bot turns gently toward the side with the higher clearance to maintain centrality and avoid collision.

- The LiDAR module operates in parallel, providing high-frequency wall distance measurements. These are used in a feedback loop for counter-steering—dynamically correcting to keep the chassis parallel to the lane boundaries and maximizing lap speed and safety.

4) Lap Counter & Completion Logic

- Each complete revolution of the track increments a lap counter.

- If laps > 3, the system initiates the Parallel Parking Sequence. Otherwise, the navigation loop repeats.

Obstacle Challenge (Round 2)
1) LiDAR-Based Mapping & Pillar Detection Initialization

- The LiDAR system bootstraps, performing environmental scans to map both static field features and dynamic obstacles (pillars).

2) Pillar Tracking & Color Classification

- Upon locating a pillar by proximity in the LiDAR map, the camera is triggered to capture and classify the pillar’s color by majority pixel average.

- If green, a navigation waypoint is generated to the left of the pillar; if red, to the right.

- Waypoints are fed to the main path-planner, which recalculates trajectories dynamically for precise lane-keeping and object avoidance.

3) Loop Logic for Laps

- The above mapping, classification, and navigation run continuously throughout the three laps, with the robot always tracking its section, progress, and upcoming pillar positions.

4) Autonomous Parallel Parking Sequence

- Parking Lot Detection: At lap completion, sensors (LiDAR/camera) search for the parking lot boundary markers as per field specs.

- Initial Alignment: The vehicle slows, aligning itself parallel to the field’s outer wall by continuously comparing left/right LiDAR readings and using IMU orientation checks (< 2cm and < 2° tolerance).

- Entry Positioning: Advance until the rear wheel crosses the intended parking zone entry (based on rotary encoder ticks or real-time field feature estimation).

- Reverse Maneuver, Step 1: Start reversing with maximum steering toward the parking bay (usually right).

- Reverse Maneuver, Step 2: Once halfway inside, immediately steer to full opposite lock (left), continuing the reverse arc.

- Final Alignment: Stop as soon as sensors (LiDAR/camera) confirm the entire robot is within boundaries and parallel to the wall (verify < 2cm tolerance). If needed, issue slight forward/backward correction maneuvers using PID feedback from the sensors.

- Completion: Power down drive motors and alert completion via buzzer/LED.

### Flow Charts

##### Open Round


##### Obstacle Round


## Our Journal


### June:


##### The Original Sketch of our car.


## July:


##### The car by the end of the month


## August:


## Gantt Chart

 
  

