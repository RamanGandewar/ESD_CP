# Acoustic Leak Detection System

**Smart, Cost-Effective Early Warning for Water Pipeline Leaks**

---

## Overview

The Acoustic Leak Detection System is an advanced embedded solution designed to detect and pinpoint underground water pipeline leaks with industry-leading accuracy and affordability. Built around ARM Cortex-M4 technology, this system leverages edge AI, high-sensitivity sensors, and long-range networking to deliver real-time alerts and location data—enabling utilities and industries to reduce water loss, optimize maintenance, and safeguard infrastructure.

---

## Key Features

- **High Accuracy Leak Detection:** Identifies leaks as small as 0.1 GPM, with location precision to ±5 meters.
- **Edge AI Signal Processing:** Real-time classification and noise filtering performed locally on each sensor node.
- **Multi-Sensor Triangulation:** Networked sensors correlate signals for pinpoint leak localization.
- **Low Cost:** ~$800 per sensor, offering a 10x cost advantage over traditional systems.
- **Long Battery Life:** 5+ years operation, solar and lithium battery powered.
- **Robust Communication:** LoRaWAN networking for reliable data transmission over 10+ km.
- **Environmental Durability:** IP68 waterproof, corrosion-resistant, MIL-STD-810G vibration compliant.

---

## System Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Sensor Node   │    │   Sensor Node   │    │   Sensor Node   │
│  (ARM Cortex-M4)│    │  (ARM Cortex-M4)│    │  (ARM Cortex-M4)│
│                 │    │                 │    │                 │
│ • Accelerometer │    │ • Accelerometer │    │ • Accelerometer │
│ • Hydrophone    │    │ • Hydrophone    │    │ • Hydrophone    │
│ • AI Processing │    │ • AI Processing │    │ • AI Processing │
│ • LoRaWAN       │    │ • LoRaWAN       │    │ • LoRaWAN       │
└─────────┬───────┘    └─────────┬───────┘    └─────────┬───────┘
          │                      │                      │
          │              ┌───────┴───────┐              │
          └──────────────┤  LoRaWAN      ├──────────────┘
                         │  Gateway      │
                         └───────┬───────┘
                                 │
                         ┌───────┴───────┐
                         │  Cloud        │
                         │  Platform     │
                         │               │
                         │ • Data Analytics
                         │ • Leak Correlation
                         │ • Alert Management
                         │ • Utility Dashboard
                         └───────────────┘
```

---

## Hardware Components

- **Microcontroller:** STM32F407VGT6 (ARM Cortex-M4F), 168 MHz, 1MB Flash, 192KB RAM
- **Sensors:** ADXL355 Accelerometer, Custom Piezoelectric Hydrophone, 24-bit ADC (ADS1256)
- **Networking:** RN2903 LoRaWAN Module, 915/868 MHz, 10+ km range
- **Power:** 10W Solar Panel, 10,000mAh LiFePO4 Battery, MPPT Charge Controller
- **Enclosure:** IP68 Aluminum, MIL-STD-810G vibration, -40°C to +85°C operation

---

## Software Architecture

- **OS:** FreeRTOS (v10.4.6)
- **Signal Processing:** ARM CMSIS-DSP, custom filtering and FFT
- **Machine Learning:** TensorFlow Lite Micro (quantized models, <100ms inference)
- **Communication:** LoRaWAN protocol stack, AES-128 encryption
- **Cloud Analytics:** Time-series database, leak correlation, dashboard, GIS integration

### Signal Processing Pipeline

1. **Data Acquisition:** 8kHz audio sampling via DMA
2. **Preprocessing:** High-pass filtering, windowing, noise reduction
3. **Feature Extraction:** FFT, spectral centroid, MFCC, harmonic analysis
4. **Classification:** Edge ML for leak detection, confidence scoring, temporal smoothing

---

## How It Works

1. **Continuous Monitoring:** Each sensor node samples pipeline vibrations and sounds, processing signals in real-time.
2. **Leak Detection:** AI models distinguish leak signatures from ambient noise, minimizing false alarms.
3. **Location Triangulation:** Multiple nodes correlate and analyze signals to pinpoint leak locations within ±5 meters.
4. **Alert & Reporting:** Detected leaks trigger immediate alerts via LoRaWAN. Status reports and analytics are uploaded to the cloud dashboard.
5. **Remote Management:** Nodes support OTA firmware updates and remote configuration.

---

## Getting Started

> **Note:** This project requires experience with embedded systems, ARM microcontroller development, DSP, and IoT networking.

### Hardware Setup

- Refer to `docs/hardware_specs.md` for detailed component list, PCB layouts, and enclosure drawings.
- Assemble sensor nodes using provided BOM and guidelines.
- Install nodes along pipeline routes, ensuring waterproofing and proper antenna placement.

### Firmware Development

- Clone the repository and set up the FreeRTOS environment.
- Configure ADC, DMA, and sensor interfaces per `docs/software_architecture.md`.
- Load signal processing and ML models onto the MCU.
- Flash the firmware and validate signal acquisition and leak detection algorithms.

### Networking & Cloud Integration

- Set up LoRaWAN gateway and register sensor nodes.
- Configure cloud platform (InfluxDB, dashboard, analytics pipeline).
- Integrate alerts via SMS/email and enable GIS mapping features.

### Field Deployment

- Conduct laboratory and field validation tests using procedures in `docs/test_procedures.md`.
- Monitor system performance, detection accuracy, and battery life.
- Collect performance data for system optimization.

---

## Performance Highlights

| Capability                     | Specification                |
|---------------------------------|------------------------------|
| Leak Detection Minimum          | 0.1 GPM                      |
| Location Accuracy               | ±5 meters                    |
| Detection Range                 | 200–500 meters               |
| False Positive Rate             | <5%                          |
| Battery Life                    | 5+ years                     |
| Network Range                   | 10+ km (LoRaWAN)             |
| FFT Processing Time             | <10ms                        |
| ML Inference Time               | <100ms                       |
| Uptime                          | 99.5%                        |
| Waterproof Rating               | IP68                         |
| Operating Temperature           | -40°C to +85°C               |

---

## Project Structure

- `/docs` — Hardware specs, software architecture, test plans, market analysis
- `/firmware` — Embedded software stack (FreeRTOS, signal processing, ML)
- `/hardware` — Schematics, PCB layouts, mechanical design files
- `/cloud` — Analytics, dashboard, and alerting scripts
- `/tools` — Utilities for deployment and diagnostics

---

## Contributing

We welcome collaboration! If you're helping with this project:

1. **Review `/docs/README_collab.md` for team guidelines.**
2. **Open issues for improvements, bugs, or suggestions.**
3. **Submit pull requests with clear descriptions and test results.**

---

## License

This project is for academic and internal development use only. For commercial deployment, please contact the project team.

---

## Contact

- **Project Lead:** Raman Gandewar
- **Email:** ramangandewar@gmail.com
- **Advisors:** [List academic/industry mentors]

---

*For more details, see project docs and appendices. This README provides a high-level orientation for contributors and stakeholders.*
