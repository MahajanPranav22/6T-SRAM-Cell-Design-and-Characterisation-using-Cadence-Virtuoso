<img width="1366" height="768" alt="6tsram_dc_circuit" src="https://github.com/user-attachments/assets/7bf9b5cc-53ac-428d-86b0-d1788303da62" />

# Image 1: 6T-SRAM Core Cell Schematic

## Overview
This image shows the complete schematic of the 6-transistor SRAM cell designed in Cadence Virtuoso Schematic Editor. The design implements a standard CMOS 6T-SRAM cell with cross-coupled inverters for data storage.

---

## Circuit Description

### Circuit Topology
The 6T-SRAM cell consists of:
1. **Two Cross-Coupled CMOS Inverters** (Storage Element)
2. **Two NMOS Access Transistors** (Read/Write Access)

### Detailed Component Breakdown

#### **Left Inverter (Stores q̄, outputs q)**
- **M1 (PMOS)**: Pull-up transistor
  - Source: VDD
  - Gate: q (feedback from right inverter)
  - Drain: qbar
  - Purpose: Pulls qbar to VDD when q is low

- **M3 (NMOS)**: Pull-down transistor
  - Source: GND
  - Gate: q (feedback from right inverter)
  - Drain: qbar
  - Purpose: Pulls qbar to GND when q is high

#### **Right Inverter (Stores q, outputs q̄)**
- **M5 (PMOS)**: Pull-up transistor
  - Source: VDD
  - Gate: qbar (feedback from left inverter)
  - Drain: q
  - Purpose: Pulls q to VDD when qbar is low

- **M6 (NMOS)**: Pull-down transistor
  - Source: GND
  - Gate: qbar (feedback from left inverter)
  - Drain: q
  - Purpose: Pulls q to GND when qbar is high

#### **Access Transistors**
- **M2 (NMOS Left)**: 
  - Source/Drain: BL (Bitline) ↔ qbar
  - Gate: WL (Wordline)
  - Purpose: Connects BL to qbar when WL is high

- **M4 (NMOS Right)**:
  - Source/Drain: BLB (Bitline Bar) ↔ q
  - Gate: WL (Wordline)
  - Purpose: Connects BLB to q when WL is high

---

## Pin Configuration

| Pin Name | Type | Description |
|----------|------|-------------|
| **VDD** | Input | Power supply (typically 1.8V) |
| **GND** | Input | Ground reference (0V) |
| **WL** | Input | Wordline - enables access to cell |
| **BL** | I/O | Bitline - data input/output |
| **BLB** | I/O | Bitline bar - complementary data |
| **q** | Internal | Storage node (data bit) |
| **qbar** | Internal | Complementary storage node |

---

## Transistor Sizing (Visible in Schematic)

Based on the schematic annotations:

```
Access Transistors (M2, M4):
- Width (W): ~1.45μm
- Length (L): Standard minimum length
- Purpose: Sized for adequate read/write access

Pull-down NMOS (M3, M6):
- Width (W): Larger than access transistors
- Purpose: Ensures read stability (prevents data flip during read)

Pull-up PMOS (M1, M5):
- Width (W): ~1.2μm (visible as "w=120n" in image)
- Purpose: Sized smaller than pull-down for write-ability
```

### Design Ratios (Standard 6T-SRAM)
```
Cell Ratio (CR) = (W/L)pull-down / (W/L)access ≈ 1.5-2.0
Pull-up Ratio (PR) = (W/L)pull-up / (W/L)access ≈ 1.0-1.2
```

---

## Circuit Operation

### **1. HOLD Operation (WL = 0)**
- Access transistors M2 and M4 are OFF
- Cross-coupled inverters maintain stored data
- Positive feedback ensures bistability
- No power consumption (except leakage)

**Example**: If q = 1, qbar = 0:
- M5 is ON (gate=0), M6 is OFF → q stays at VDD
- M1 is OFF (gate=1), M3 is ON → qbar stays at GND

### **2. WRITE Operation (WL = 1)**
- Access transistors turn ON
- Bitlines driven by write circuitry:
  - To write '1': BL = VDD, BLB = 0
  - To write '0': BL = 0, BLB = VDD
- Bitlines overpower internal nodes
- Cell flips to a new state

**Write '1' Example** (q = 0 → 1):
1. Initially: q = 0, qbar = 1
2. Drive: BL = 0, BLB = VDD
3. M4 pulls q toward VDD
4. When q crosses the threshold, the right inverter switches
5. Positive feedback completes the flip
6. Final: q = 1, qbar = 0

### **3. READ Operation (WL = 1)**
- Bitlines precharged to VDD
- Access transistors turn ON
- Cell discharges one bitline slightly
- Sense amplifier detects voltage difference
- Cell must NOT flip during read (ensured by proper sizing)

**Read '1' Example** (q = 1):
1. Precharge: BL = BLB = VDD
2. WL = 1 activates access transistors
3. M2 conducts, BL discharges slightly through M3
4. Voltage difference: BLB > BL
5. The sense amplifier detects and amplifies the difference

---

## Critical Design Considerations

### **1. Read Stability**
- **Issue**: During read, BL discharge can lower qbar voltage
- **Solution**: Make pull-down (M3, M6) stronger than access (M2, M4)
- **Metric**: Read Static Noise Margin (SNM)

### **2. Write Ability**
- **Issue**: Cell must flip when bitlines drive it
- **Solution**: Make pull-up (M1, M5) weaker than access (M2, M4)
- **Metric**: Write Margin (WM)

### **3. Power Consumption**
- **Static Power**: Minimal (only leakage in HOLD)
- **Dynamic Power**: During read/write switching
- **Optimisation**: Minimise capacitances, optimise sizing

---

## Property Editor Information (Bottom Left)

```
Library: santosh_m
Cell: 6t-sram
View: schematic
Mode: editable
Last Saved: Thu Mar 20...
Units: inch
```

---

## Navigator Panel (Left Side)

```
OBJECTS:
├── All
├── Instances: 15
├── Nets: 7
├── Pins: 6
└── Nets and Pins

GROUPS:
├── Cells
└── Types
```

**Instance Count**: 15 instances include:
- 6 transistors (M1-M6)
- Power/ground connections
- Pin instances
- Wire connections

**Nets Count**: 7 nets are:
1. VDD
2. GND
3. WL
4. BL
5. BLB
6. q
7. qbar

---

## Key Features Visible in Schematic

✅ **Color Coding**:
- Red circles: Pin connections
- Cyan boxes: MOSFET symbols
- Green dots: Node connections
- Orange/yellow text: Component labels

✅ **Annotations**:
- Transistor names (M1-M6)
- Pin labels (VDD, GND, WL, BL, BLB, q, qbar)
- Width parameters visible (w=120n, etc.)

✅ **Symmetric Layout**:
- Left and right inverters are mirror images
- Balanced design for equal rise/fall times

---

## Copy-Paste Content for Reports

### Circuit Description (Formal)
```
The 6T-SRAM cell implements a bistable storage element using two cross-coupled 
CMOS inverters (M1-M3 and M5-M6) and two NMOS access transistors (M2, M4). 
The cross-coupled configuration creates a positive feedback loop that maintains 
one of two stable states: q=1/qbar=0 or q=0/qbar=1. Access transistors M2 and 
M4, controlled by the wordline (WL), enable read and write operations by 
connecting the storage nodes to bitlines (BL, BLB). The design employs ratioed 
transistor sizing to ensure read stability (cell ratio) and writeability 
(pull-up ratio).
```

### Component List
```
M1: PMOS pull-up (left inverter)
M2: NMOS access (left side)
M3: NMOS pull-down (left inverter)
M4: NMOS access (right side)
M5: PMOS pull-up (right inverter)
M6: NMOS pull-down (right inverter)
```

---

## Technical Specifications

| Parameter | Specification |
|-----------|--------------|
| **Transistor Count** | 6 (4 storage + 2 access) |
| **Storage Nodes** | 2 (q, qbar - complementary) |
| **Control Lines** | 1 (WL) |
| **Data Lines** | 2 (BL, BLB - differential) |
| **Power Rails** | 2 (VDD, GND) |
| **Stability** | Bistable (two stable states) |
| **Operation Modes** | Hold, Read, Write |

---

## Next Steps

1. ✅ Complete DC analysis for SNM calculation → See IMAGE_2
2. ✅ Perform transient simulation for read/write → See IMAGE_4, 7, 8
3. ✅ Create physical layout → See IMAGE_3
4. ✅ Verify with DRC/LVS

---



