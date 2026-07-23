# Three-Band Analog Audio Equalizer

An active three-band audio equalizer designed and built as part of **Purdue Electrical Engineering Lab** (November 2025).

---

## Overview

This project implements a fully analog, active three-band audio equalizer capable of independently boosting or cutting low, mid, and high frequency bands. The design uses **RC filter networks** for frequency selection and **op-amp gain stages** for active amplification, with frequency response measured and tuned for low-distortion output across the audio band.

---

## Band Specifications

| Band | Frequency Range | Filter Type |
|------|----------------|-------------|
| Low  | < 300 Hz       | Active Low-Pass  |
| Mid  | 300 Hz – 3 kHz | Active Band-Pass |
| High | > 3 kHz        | Active High-Pass |

Each band feeds into an inverting summing amplifier that recombines the three signals into a single output.

---

## Signal Chain

```
Audio Input
     │
     ├──── Low-Pass Filter  ──── Gain Stage (Low)  ────┐
     │                                                   │
     ├──── Band-Pass Filter ──── Gain Stage (Mid)  ────►  Summing Amplifier ──── Output
     │                                                   │
     └──── High-Pass Filter ──── Gain Stage (High) ────┘
```

---

## Design Details

- **Filter topology:** Sallen-Key (2nd order) for low and high bands; multiple-feedback (MFB) for mid band
- **Op-amps:** TL072 dual op-amp (low noise, JFET input)
- **Gain control:** Variable resistors (potentiometers) on each gain stage allow ±12 dB boost/cut per band
- **Supply:** ±15V dual supply
- **Load impedance:** Designed for 10 kΩ output load

---

## Measured Results

- Frequency response verified with a function generator and oscilloscope sweep
- Low-distortion output confirmed across 20 Hz – 20 kHz audio band
- Crosstalk between bands measured at < −40 dB at crossover frequencies
- Unity gain (flat response) confirmed with all potentiometers at center position

---

## Repository Contents

```
├── schematics/
│   └── audio_equalizer.pdf        # Full circuit schematic
├── data/
│   └── frequency_response.csv     # Measured gain vs. frequency data
├── plots/
│   └── bode_plot.png              # Measured Bode plot (all three bands)
└── analysis/
    └── plot_response.py           # Plot frequency response from CSV data
```

---

## Dependencies

```
numpy
matplotlib
```

Course: Purdue University — Electrical Engineering Laboratory, November 2025
