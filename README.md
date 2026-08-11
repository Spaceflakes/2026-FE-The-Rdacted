# WRO 2026 — Self-Driving Vehicle (Engineering Materials)

Short project summary
This repository contains the engineering documentation, photos, schematics, models and control software for our self-driven vehicle that participated in the WRO Future Engineers 2026 competition.

Status
- Team: The Redacted
- Competition: WRO Future Engineers — Season 2026
- Status: In final stages of development

Table of Contents
- [Content overview](#content-overview)
- [Hardware & BOM](#hardware--bom)
- [Software & Architecture](#software--architecture)
- [Setup and Run](#setup-and-run)
- [Demo video & media](#demo-video--media)
- [Repository structure](#repository-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

Content overview
- t-photos: team photos (official and fun group photo)
- v-photos: vehicle photos (front, back, sides, top, bottom)
- video: video.md (link to driving demonstration)
- schemes: schematic diagrams showing electronics, motors and wiring (JPEG/PNG/PDF)
- src: control software for microcontrollers/SBC used in the vehicle
- models: 3D-print / laser / CNC files used to produce vehicle parts
- other: additional docs, datasets, instructions for uploading to SBC/SBM, etc.

Hardware & BOM
- Main controller:
- Motor drivers:
- Motors:
- Sensors: LIDAR, camera, etc
- Power:
- Peripherals:
- Bill of Materials (BOM):
  
Software & Architecture
- Languages: Python
- Modules:
  - core/vehicle_control — motor & sensor abstraction
  - nav — navigation, path planning
  - vision — camera processing (object detection/line following)
  - utils — logging, config
- Supported hardware targets:
- Dependencies: list libraries and versions
  
Setup and Run
Prerequisites
- Hardware assembled and connected as described in `schemes/`
- OS image for SBC if applicable (link to image)
- Required packages:

Quick start
1. Clone the repository:
   git clone https://github.com/Spaceflakes/2026-FE-The-Rdacted.git
2. Enter project directory and install dependencies:
   cd 2026-FE-The-Rdacted/src
   pip install -r requirements.txt
3. Configure hardware:
   - Edit `config/default.yaml` to match ports and sensors
4. Run demo:
   python run_demo.py --profile competition

Testing
- How to run unit/integration tests (if present)
- How to run validation on hardware

Demo video & media
- video/video.md — link to the demonstration video (YouTube or private link)
- Add short timestamped notes explaining what judges should look for

Repository structure
Explain important files and where to find them:
- /t-photos — team photos
- /v-photos — vehicle photos
- /schemes — wiring diagrams and schematics
- /src — source code (see README inside /src for build/run details)
- /models — CAD/STL files used for manufacturing
- /video/video.md — demo video link
- /other — datasets, upload instructions, extra docs

Contributing
- This is an engineering submission repository. If you want to re-use or adapt the project:
  - Fork or use the template (do not edit this repository directly unless you are a team member).
  - Open a PR for changes; include hardware used, test results and photos.
- If this repository is a template, use GitHub's "Use this template" button to create a new repo for your team.

License
- Add a license file
- Put short license note here and include LICENSE file at repo root.

Contact
- Team lead: Name — email@example.com

Changelog
- v1.0 — initial submission (date)
