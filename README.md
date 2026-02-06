# revAmp

A ground-up modernization of my University of Alabama in Huntsville (UAH) Honors College capstone + thesis project: a vacuum tube headphone amplifier.

This repo is the “professional redo” of that original amp — keeping what sounded great, fixing what didn’t, and rebuilding the whole thing around robust PCB-based hardware.

---

## Background

In college, my Honors College capstone project and thesis centered on a vacuum tube headphone amplifier I designed and built. The amp itself sounded excellent and was electrically quiet at the output — no audible hum, no obvious supply noise in the headphones.

However, the *power supply architecture* was very “old school”: a doubler/bridge feeding a large LC filter bank. Functionally it worked, but the power factor was **terrible** — to the point that when the amp was powered on, I could *hear its effect on the mains* through my computer speakers (via other devices on the same circuit). The amp didn’t hum — it just made everything else’s life miserable.

A few years later, during a move, the amp took a hard bump. The next time I powered it up it went **“pop”** and released the magic smoke. Sad day — that build has a lot of memories wrapped up in it.

But that failure also created a perfect opportunity: rebuild it properly with the experience I’ve gained as a professional electrical engineer.

Thus: **revAmp**.

---

## Project Goals

- Preserve the original amp’s sound and overall tube topology
- Eliminate mains pollution by using active PFC with high power factor
- Improve mechanical robustness and long-term reliability
- Replace the fragile “rats nest” point-to-point construction with modular PCBs
- Add proper sequencing, protection, and inrush limiting

---

## Architecture Overview

revAmp is built as a multi-board system:

1. **PFC Preregulator PCB**
   - Boosts 120 VAC mains to a regulated high-voltage DC bus  
   - Target: **300 VDC**, up to **1 A max**
   - Target power factor: **≥ 0.99**
   - Topology: **boost PFC** at **200 kHz**
   - Includes:
     - Internal auxiliary power generation
     - Power sequencing
     - Active inrush current limiting

2. **High-Voltage Linear Regulator PCB** *(Work in Progress)*
   - Drops the 300 VDC bus down to a **250 VDC plate supply**
   - Goal: quiet, stiff supply for the tube stages
   - This section is under active development — README will evolve as the design matures.

3. **Left Channel Audio PCB**
4. **Right Channel Audio PCB**
   - The analog audio circuits are largely a “copy/paste” of the original UAH project
   - Minor changes are being made primarily for:
     - Power handling margin
     - Component package selection
     - Longevity and robustness

---

## Tube Audio Topology (Analog Boards)

The audio path is a classic two-stage arrangement:

- **Voltage gain stage:** common-cathode preamp based on **ECC88**
- **Output buffer:** cathode follower based on **6AS7G**

The intent here is to preserve the sonic character of the original amplifier while modernizing the supporting infrastructure and improving reliability.

---

## Repo Contents (Planned)

This repository is intended to collect *everything needed to rebuild revAmp*:

- Schematics
- PCB layouts
- BOMs
- Simulation notes and results
- Power-stage math (PFC design, loop compensation, etc.)
- Bring-up notes and validation results
- Mechanical notes where relevant (connectors, mounting, grounding strategy)

---

## Status

- ✅ PFC preregulator: defined architecture and design targets; implementation in progress
- 🚧 Linear regulator: work in progress
- ✅ Audio circuits: based heavily on the original design; adapting for PCB implementation

---

## Safety Disclaimer (High Voltage)

This project involves **lethal voltages** (300 VDC bus, 250 VDC plate supply, mains input).  
If you build or test hardware from this repo, you are responsible for safe practices:

- Use an isolation transformer where appropriate
- Follow proper creepage/clearance rules
- Implement fusing and protective earth correctly
- Discharge capacitors before handling
- Treat everything as live until proven otherwise

---

## Contributing / Collaboration

This is primarily a personal rebuild project, but constructive feedback is welcome — especially around:
- PFC control-loop stability and compensation
- EMI / layout practices at 200 kHz
- Grounding strategy for mixed HV power + low-noise audio
- Sequencing and protection philosophy

Open an issue or PR if you want to discuss improvements.

---

## Credits

Original concept/design: my UAH Honors College capstone + thesis project.  
revAmp is the modern, PCB-based redesign and reliability upgrade.

This is a [LibrePCB](https://librepcb.org) project!
Just edit this file to add a description about it.

## License

### Hardware (schematics, PCB layouts, BOMs, mechanical CAD)
Licensed under the CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2.0).  
You may obtain a copy of the license at: https://ohwr.org/cern_ohl_s_v2.txt

### Software (firmware, scripts, utilities)
Licensed under the MIT License.  
You may obtain a copy of the license at: https://opensource.org/license/mit/

### Documentation (README, design notes, PDFs)
Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).  
You may obtain a copy of the license at: https://creativecommons.org/licenses/by/4.0/



