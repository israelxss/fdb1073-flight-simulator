# Flight Incident Report & Telemetry Simulator: Flydubai Flight FZ1073 (A6-FKF)

## 📌 Overview
This repository provides an interactive flight dynamics simulator and telemetry analysis tool based on granular ADS-B data from **Flydubai flight FZ1073** (Dubai to Tel Aviv), which experienced an emergency diversion to Tabuk, Saudi Arabia, following an onboard incident on September 30, 2026.

---

## 🔗 Data Source & Reference
* **Official Flightradar24 Coverage & Granular ADS-B Dataset:**  
  [Flightradar24 Incident Report: Flydubai flight to Tel Aviv diverts to Tabuk amid onboard incident](https://www.flightradar24.com/blog/flight-tracking-news/major-incident/flydubai-flight-to-tel-aviv-diverts-to-tabuk-amid-onboard-incident/)
* **Granular Flight Log File:**  
  [`Flightradar24-Granular-Data-FZ1073-30-September-2026.csv`](Flightradar24-Granular-Data-FZ1073-30-September-2026.csv)

---

## ✈️ Aircraft & Flight Information

| Parameter | Details |
| :--- | :--- |
| **Flight Number** | FZ1073 / FDB1073 |
| **Callsign** | FDB1073 |
| **Airline** | Flydubai (flydubai.com) |
| **Origin** | Dubai International Airport (**DXB / OMDB**), United Arab Emirates |
| **Scheduled Destination** | Ben Gurion Airport (**TLV / LLBG**), Tel Aviv, Israel |
| **Actual Landing / Diversion** | Prince Sultan bin Abdulaziz Regional Airport (**TUU / OETB**), Tabuk, Saudi Arabia |
| **Date of Occurrence** | September 30, 2026 |
| **Aircraft Model** | Boeing 737 MAX 8 (737-8) |
| **Registration / Hex Code** | **A6-FKF** (ICAO 24-bit Mode-S address: `8966E5`) |
| **Engines** | 2x CFM International LEAP-1B |

---

## 🚨 Incident Summary
* **Cruising Phase:**  
  The flight departed Dubai and climbed to its assigned cruising altitude of **FL360 (36,000 ft)**, heading northwest across Saudi Arabia en route to Tel Aviv.
* **Onboard Disturbance / Emergency:**  
  While in northern Saudi airspace, an onboard incident occurred involving an unruly passenger or security disruption.
* **Flight Trajectory & Diversion:**  
  The crew coordinated with air traffic control (ATC), initiated a descent, squawked standard emergency/diversion procedures, and altered course towards **Tabuk (TUU / OETB)**.
* **Safe Landing:**  
  The aircraft touched down safely at Tabuk Regional Airport, where local authorities and ground emergency services met the aircraft on the tarmac. No hull damage or severe structural failures were reported.

---

## 📊 Granular ADS-B Telemetry Analysis
The simulator ingests **10,353 ADS-B transmission records** collected at high frequency (~sub-second to 1-second resolution).

### Key Recorded Telemetry Parameters:
1. **Timestamp (UTC):** Precise mission elapsed time during climb, cruise, diversion maneuvers, and touchdown.
2. **Barometric & Geometric Altitude (ft):** Measured profile showing cruise stabilization at 36,000 ft and controlled descent into Tabuk.
3. **Ground Speed & True/Indicated Airspeed (kts):** High-speed cruise (~450-480 kts GS) transitioning down to final approach and rollout speeds.
4. **Vertical Rate (FPM):** Vertical climb and descent velocities.
5. **Pitch Angle ($\gamma$) & Derived Attitude:** Calculated from vertical velocity vectors and true airspeed:
   $$\gamma = \arcsin\left(\frac{V_v}{V_{TAS}}\right)$$
6. **Estimated G-Force ($N_z$):** Estimated load factor based on vertical acceleration and pitch transitions:
   $$N_z = 1 + \frac{a_z}{g}$$

---

## 🖥️ Interactive Simulator Features
The accompanying application ([`index.html`](index.html)) allows comprehensive visualization of the flight data:
- **100% Single-Window UI (`100vh`):** Fully responsive, zero-scroll interface.
- **Multilingual Support (Hebrew & English):** Automatic language detection with manual toggle and full RTL/LTR dynamic flipping.
- **Vertical Stacked Instruments:**
  - **Top Card:** Lateral Pitch & Attitude Profile (aircraft side silhouette with live pitch protractor).
  - **Bottom Card:** Gyro Artificial Horizon (Attitude Indicator with sky/ground ball, pitch ladders, and G-force load indicator).
- **Interactive High-Resolution Telemetry Charts:** Altitude profile and Speed/Vertical speed graphs with synchronized crosshairs.
- **Playback Controls:** Real-time 1x playback speed as recorded, fast-forward modes (2x, 5x, 15x, 30x), pause, resume, and instant scrub slider.
- **Direct CSV Engine:** Built-in client-side CSV parser allowing users to load any Flightradar24 ADS-B CSV directly into the simulator.

---

## 📁 Repository Structure
```
fdb1073-flight-simulator/
├── README.md                                             # Incident and technical documentation
├── index.html                                            # Main simulator application for GitHub Pages
├── flight_simulator.html                                 # Simulator copy
├── flight_data.js                                        # Standalone preprocessed JSON/JS telemetry array (~1.7 MB)
├── Flightradar24-Granular-Data-FZ1073-30-September-2026.csv # Original Flightradar24 granular ADS-B capture
└── data.json                                             # Telemetry backup in JSON format
```