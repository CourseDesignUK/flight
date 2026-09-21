# UK Civil Airport 3D Flight Tracker

A client-side 3D flight simulation and approach tracking tool built with [CesiumJS](https://cesium.com/platform/cesiumjs/). Visualises an aircraft on a straight-in 6-mile final approach, touchdown, and rollout across 27 UK commercial airports, complete with synchronized VHF radio transcripts, text-to-speech audio, and emergency failure sequences.

---

## Overview

The application simulates a commercial flight navigating instrument approaches under UK Air Traffic Control. It pairs geospatial 3D trajectory tracking with real-world airport telemetry, procedural ATC comms, an interactive Heads-Up Display (HUD), and dynamic particle effects for emergency scenarios.

---

## Key Features

- **3D Geospatial Visualisation:** Rendered via CesiumJS v1.124 over high-resolution ArcGIS World Imagery tiles.
- **Airport Coverage:** 27 UK commercial aerodromes preconfigured with genuine coordinates, runway designations, field elevations, and active approach/tower frequencies (e.g., Heathrow, Gatwick, Manchester, Edinburgh, Jersey).
- **Synthetic Waypoint Generation:** Computes straight-in reciprocal glide paths from 6 NM out through glidepath intercept, threshold crossing (50 ft), touchdown, and deceleration to a full stop.
- **Dynamic Heads-Up Display (HUD):**
  - **Airport Telemetry Panel:** Tracks callsign, approach phase, altitude (AMSL), calculated ground speed (kts), threshold distance (NM), and coordinate fix.
  - **Cockpit HUD Overlay:** Vector SVG HUD displaying pitch ladder, boresight reticle, compass tape, and airspeed/altitude readouts.
- **VHF Radio Comm Simulation:**
  - Synchronized approach and tower frequency handoffs with accurate aviation phraseology.
  - Native Web Speech API integration (`speechSynthesis`) using UK English (`en-GB`) voices with distinct pitch profiles for ATC and flight crew.
  - Automatic phonetic string parsing for runway identifiers, QNH values, ILS/DME markers, and decimal frequency readouts.
- **In-Flight Emergency Injection:**
  - **Engine Fire:** Trigger engine fire and trailing smoke particle emitters; initiates emergency priority diversion dialogue and runway evacuation.
  - **Cockpit Fumes:** Cockpit particle emitter with smoke donned-mask communication sequence.
  - **Stuck Gear:** Ground rollout failure with nose friction spark emitters post-touchdown.
- **Camera Tracking Modes:**
  - **Chase Cam:** Dynamic entity-locked chase perspective.
  - **Cockpit View:** Fixed nose-mount camera transformed relative to aircraft orientation and flight vector.
  - **Tower View:** Static airport observation point oriented toward the approach corridor.
  - **Free Orbit:** Unconstrained 6DoF camera.
- **Simulation Controls:** Time scale adjustments (1x, 2x, 4x), play/pause synchronization, and day/night scene lighting toggle.

---

## Aerodrome Database

Includes data for:

| ICAO | Airport Name | Runway | App Freq (MHz) | Twr Freq (MHz) |
| :--- | :--- | :--- | :--- | :--- |
| **EGLL** | London Heathrow | 27R | 119.725 | 118.500 |
| **EGKK** | London Gatwick | 26L | 126.825 | 124.225 |
| **EGSS** | London Stansted | 22 | 120.625 | 123.800 |
| **EGGW** | London Luton | 26 | 129.550 | 132.550 |
| **EGLC** | London City | 27 | 132.700 | 118.075 |
| **EGCC** | Manchester | 23R | 118.575 | 118.625 |
| **EGBB** | Birmingham | 33 | 131.000 | 118.300 |
| **EGPH** | Edinburgh | 24 | 121.200 | 118.700 |
| **EGPF** | Glasgow | 23 | 119.100 | 118.800 |
| **EGGD** | Bristol | 27 | 125.650 | 133.850 |
| *+17 more* | Newcastle, Liverpool, Leeds Bradford, East Midlands, Belfast (Intl/City), Aberdeen, Cardiff, Exeter, Southampton, Bournemouth, Norwich, Inverness, Cambridge, Isle of Man, Guernsey, Jersey. | | | |

---

## Technical Stack

- **CesiumJS (1.124):** Core rendering engine, Cartesian math transforms, particle system management, and time-dynamic entity tracking (`SampledPositionProperty`).
- **Web Speech API:** Speech synthesis for ATC and pilot voice dialogue.
- **ArcGIS REST Services:** Base imagery provider (`World_Imagery/MapServer`).
- **HTML5 / CSS3 / SVG:** Glassmorphism UI overlays and HUD instrumentation.

---

## Getting Started

### Prerequisites

A modern web browser supporting WebGL and the Web Speech API (Chrome, Edge, Firefox, Safari).

### Installation

No build pipeline or package manager required. The application runs as a standalone single-page file.

1. Clone or download the repository:
   ```bash
   git clone [https://github.com/](https://github.com/)<your-username>/<repo-name>.git
   cd <repo-name>
