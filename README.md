# 6T-SRAM Cell Design and Characterisation using Cadence Virtuoso

## Project Overview

**Unleash the Power of Custom IC Design with My 6T-SRAM Cell Implementation**

Dive into the world of cutting-edge IC design with my comprehensive project on a 6-Transistor Static Random Access Memory (6T-SRAM) cell. Utilising the robust Cadence Virtuoso Design Suite, I've navigated through the intricate design flow, from schematic entry to physical layout, showcasing my expertise in full-custom IC design. This project is a testament to my ability to drive innovation in semiconductor technology.

**Author**: Arya P 
**Tools Used**: Cadence Virtuoso Schematic Editor, Virtuoso Visualization & Analysis XL, Layout Suite XL

---

## Table of Contents

1. [Project Structure](#project-structure)
2. [Design Files](#design-files)
3. [Simulation Results](#simulation-results)
4. [Key Metrics](#key-metrics)
5. [How to Use](#how-to-use)
6. [References](#references)

---

## Project Structure

```
6T-SRAM-Design/
├── README.md                          # Main documentation
├── schematics/
│   ├── IMAGE_1_EXPLANATION.md        # 6T-SRAM Core Schematic
│   ├── IMAGE_5_EXPLANATION.md        # Simplified SRAM Schematic
│   └── IMAGE_6_EXPLANATION.md        # Test Bench Schematic
├── simulations/
│   ├── IMAGE_2_EXPLANATION.md        # DC Analysis & Butterfly Curve
│   ├── IMAGE_4_EXPLANATION.md        # Write Operation Transient
│   ├── IMAGE_7_EXPLANATION.md        # Read Operation Transient
│   └── IMAGE_8_EXPLANATION.md        # Full Transient Response
├── layout/
│   └── IMAGE_3_EXPLANATION.md        # Physical Layout & DRC

```

---

## Design Files

### Schematic Designs
- **6t-sram (Core Cell)**: A meticulously designed 6-transistor SRAM cell featuring cross-coupled inverters.
- **6t-sram_tets (Testbench)**: A simulation testbench equipped with stimulus sources for comprehensive verification.

### Simulation Setup
- **DC Analysis**: A detailed butterfly curve analysis for Static Noise Margin (SNM) calculation.
- **Transient Analysis**: In-depth verification of read/write operations.
- **Technology**: Generic CMOS, adaptable to specific PDKs for versatile applications.

---

## Key Features

✅ **Complete 6T-SRAM Cell Design**
- A robust design featuring a cross-coupled inverter pair for reliable data storage.
- Access transistors strategically placed for efficient read/write operations.
- Transistor sizing optimised for maximum stability and performance.

✅ **Comprehensive Simulations**
- DC sweep analysis for Static Noise Margin (SNM) to ensure design robustness.
- Transient analysis to verify the functionality of read/write operations.
- Timing characterisation for precise performance metrics.

✅ **Physical Layout**
- A DRC-clean layout ensuring manufacturability without errors.
- A compact cell design that maximises space efficiency.
- All layers are properly defined for a seamless integration process.

✅ **Full Documentation**
- A detailed explanation for each design phase, making it accessible for newcomers.
- Annotated screenshots with component labels for clear understanding.
- Ready-to-use documentation perfect for academic presentations and beyond.

---

## Simulation Results Summary

| Parameter | Value | Notes |
|-----------|-------|-------|
| **Supply Voltage (VDD)** | 1.8V | Standard CMOS voltage |
| **Static Noise Margin** | Calculated from butterfly | See DC Analysis |
| **Write Time** | ~5ns | Optimized for speed |
| **Read Access Time** | < 1ns | Fast and efficient read operation |
| **Cell Area** | Optimized | DRC clean layout for space efficiency |



---

## Detailed Documentation

Each image has a dedicated markdown file with:
- **High-resolution annotated screenshot**
- **Component identification**
- **Circuit operation explanation**
- **Key observations and measurements**
- **Copy-paste friendly content for reports**

Navigate to the respective directories for detailed explanations:
- [Schematics Documentation](./schematics/)
- [Simulation Results](./simulations/)
- [Layout Documentation](./layout/)

---

**Citation Format**:
```
[Your Name], "6T-SRAM Cell Design and Characterisation using Cadence Virtuoso,"
VLSI Design Project, [University Name], 2025.
```

---



## License

This project is open-source for academic and educational purposes.  
Please provide appropriate attribution when using this work.
