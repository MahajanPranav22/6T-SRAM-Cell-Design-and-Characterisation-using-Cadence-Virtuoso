<img width="1366" height="768" alt="6tsram_test_circuit" src="https://github.com/user-attachments/assets/855de4de-ab69-404e-ac6f-13e51ddc1ace" />

# Image 6: Testbench Schematic for SRAM Simulation

## Overview
This image shows the testbench schematic (6t-sram_tets) used to simulate and verify the 6T-SRAM cell. The testbench provides all necessary stimulus signals including voltage sources for WL (wordline), BL (bitline), BLB (complementary bitline), VDD (power), and GND (ground), connected to the SRAM cell instance for comprehensive transient and DC analysis.

---

## Window Information

### **Tool**: Virtuoso® Analog Design Environment L (ADE L)
- **Title**: "Editing: santosh_m 6t-sram_tets schematic"
- **Timestamp**: Thu 10:54
- **Library**: santosh_m
- **Cell Name**: 6t-sram_tets (testbench cell)
- **View**: schematic
- **Mode**: editable
- **Environment**: ADE L (Analog Design Environment)

### **Toolbar Indicators**:
- **ADE L dropdown**: Active (simulation environment)
- **Sim Time indicator**: Visible
- **Run controls**: Play, Stop buttons visible
- **Analysis setup**: Configured

---

## Testbench Architecture

### **Main Components Overview**

The testbench consists of:
1. **DUT (Device Under Test)**: 6T-SRAM cell instance
2. **Stimulus Sources**: Voltage sources for all inputs
3. **Power Supplies**: VDD and GND
4. **Measurement Points**: Output probes for observation

---

## Component Details

### **1. SRAM Cell Under Test (Centre-Right)**



**Visible Pins:**
- **Top Pin**: vdd (power supply input)
- **Left Pins**: 
  - wl (wordline control)
  - bl (bitline data)
  - (blb implied on opposite side)
- **Right Pins**:
  - qbar (complementary output - visible label)
  - q (storage node output)
- **Bottom Pin**: gnd (ground reference)

**Symbol Representation:**
- Green rectangular block with pin labels
- Hierarchical symbol representing a complete 6T cell
- Colour coding: Cyan/green for active instance

---

### **2. Voltage Sources (Stimulus Generation)**

#### **VDD Power Source (Top)**
```
Instance: vcs=d5 (visible label)
Type: DC voltage source
Symbol: Circle with + marking
Value: 1.8V (typical CMOS supply)
Purpose: Provides power to the SRAM cell
Connection: Directly to vdd pin of SRAM
Terminals: 
  - Positive: Connected to vdd net
  - Negative: Connected to ground
```

#### **Wordline (WL) Pulse Source (Left)**
```
Instance: wl
Type: Pulse voltage source (VPULSE)
Symbol: Circle with waveform indication
Parameters visible:
  - ic=1.8 (initial condition)
  - Additional pulse parameters
Purpose: Generates an access control signal
Waveform: Digital pulse (0V to 1.5V/1.8V)
Connection: To wl pin of SRAM

Typical Configuration:
  V1 (Low): 0V
  V2 (High): 1.5V
  Delay (TD): 5ns
  Rise Time (TR): <100ps
  Fall Time (TF): <100ps
  Pulse Width (PW): 2-5ns
  Period (PER): 10ns
```

#### **Bitline Sources (Left Side)**
```
Instance 1: bl source
Type: Voltage source (DC or PWL)
Parameters visible:
  - ic=1.8 (visible)
  - wl, vl settings
Purpose: Provides bitline voltage for write/read
Configuration:
  Write-1: BL=0V, BLB=VDD
  Write-0: BL=VDD, BLB=0V
  Read: BL=VDD, BLB=VDD (precharged)

Instance 2: (implied blb source)
Type: Complementary bitline source
Purpose: Differential bitline configuration
```

#### **Additional Sources Visible**
```
Multiple voltage source symbols visible on the left:
  - Pulse generators
  - DC sources
  - PWL (piecewise linear) sources
  
Labels visible:
  - "wl" with ic=1.8
  - Parameters: w1, vl, vh
  - Ground connections (gnd symbols)
```

---

### **3. Ground Reference (Bottom and Throughout)**

```
Symbol: Standard ground symbol (⏚)
Instances: Multiple throughout the schematic
Purpose: Common reference point (0V)
Connections:
  - All voltage source negative terminals
  - SRAM gnd pin
  - Reference for all voltage measurements
```

---

### **4. Output Probes (Right Side)**

```
Instance: qbar (visible label on right)
Type: Output pin/probe
Symbol: Pin symbol with label
Purpose: Monitor the complementary storage node
Usage: Connect to the waveform viewer
Colour: Red label indicating output

Additional probe: q (storage node)
Location: Also connected but may not be labelled
Purpose: Monitor primary storage node
```

---

## Navigator Panel (Left Side)

### **Objects Count**:
```
OBJECTS:
├── All
├── Instances: 10
├── Nets: 7
├── Pins: 3
└── Nets and Pins

GROUPS:
├── Cells
└── Types
```

**10 Instances Breakdown:**
1. SRAM cell (1 instance)
2. VDD source (1 instance)
3. GND symbols (multiple)
4. WL pulse source (1)
5. BL source (1)
6. BLB source (1)
7. Additional voltage sources
8. Output probes/pins

**7 Nets:**
1. vdd (power net)
2. gnd (ground net)
3. wl (wordline net)
4. bl (bitline net)
5. blb (bitline bar net)
6. q (storage node net)
7. qbar (complementary storage node net)

**3 Pins:**
- Output observation points (q, qbar, possibly others)

---

## Simulation Control (Top Toolbar)

### **ADE L (Analog Design Environment) Controls**

**Dropdown Menu**: "ADE L"
```
Functions:
- Analysis setup (Transient, DC, AC)
- Variable definitions
- Model file selection
- Simulation options
- Results management
```

**Control Buttons Visible:**
```
▶ Play Button: Run simulation
⬛ Stop Button: Halt simulation
📊 Results: View waveforms
⚙️ Setup: Configure analysis
📁 Files: Manage simulation files
```



---

## Status Bar (Bottom)

```
Left Side:
  Mode: schSingleSelect(Pt)
  Context: M: schZoomFit(1.0 0.9)
  
Right Side:
  Pin name: 'qbar'
  Temperature: T=27°C (visible)
  Commands: Cmd: Sel: 0
  Status: Ready
  Simulation: T=27 °C
```

**Temperature Setting:**
- **T = 27°C** (300K)
- Indicates room temperature simulation
- Standard nominal corner
- Can be varied for corner analysis

---

## Net Connectivity Diagram

```
Testbench Connectivity:
─────────────────────────

VDD Source (+1.8V)
    │
    └──> vdd net ──> SRAM vdd pin
                            │
WL Pulse (0→1.5V)          SRAM
    │                    6t-sram
    └──> wl net ──> SRAM wl pin   Cell
                            │
BL Source (0V or VDD)       │
    │                       │
    └──> bl net ──> SRAM bl pin
                            │
BLB Source (VDD or 0V)      │
    │                       │
    └──> blb net ──> SRAM blb pin
                            │
SRAM qbar pin ──> qbar net ──> Output Probe
                            │
SRAM q pin ──> q net ──> Measurement
                            │
SRAM gnd pin ──> gnd net <── Ground Symbol
    │
    └─── All source grounds
```

---

## Stimulus Configuration

### **WL (Wordline) Pulse Parameters**

**Visible in Schematic:**
```
ic = 1.8 (initial condition parameter visible)
```

**Standard Configuration** (for simulations shown in other images):
```
VPULSE Parameters:
  V1 (Initial/Low): 0V
  V2 (Pulsed/High): 1.5V
  TD (Delay): 5ns
  TR (Rise Time): 50ps-100ps
  TF (Fall Time): 50ps-100ps
  PW (Pulse Width): 5ns
  PER (Period): 10ns or longer

Result: Square pulse at t=5ns
Purpose: Enable access transistors
```

---

### **BL/BLB (Bitline) Configuration**

**For Write '1' Operation:**
```
BL Voltage: 0V (or GND)
BLB Voltage: VDD (1.8V)
Purpose: Drive q high, qbar low
Result: Write logic '1' to q
```

**For Write '0' Operation:**
```
BL Voltage: VDD (1.8V)
BLB Voltage: 0V (or GND)
Purpose: Drive q low, qbar high
Result: Write logic '0' to q
```

**For Read Operation:**
```
BL Voltage: VDD (precharged)
BLB Voltage: VDD (precharged)
Purpose: Sense stored data
Result: Small differential develops
Note: The Sense amplifier detects the difference
```

---

## Analysis Types Supported

### **1. Transient Analysis** ✅
```
Type: Time-domain simulation
Duration: 0-10ns (typical)
Purpose: Dynamic behaviour observation
Outputs: 
  - Waveforms of q, qbar, wl
  - Timing measurements
  - Write/read operation verification
Results: See Images 7, 8 (provided images)
```

### **2. DC Analysis** ✅
```
Type: DC sweep
Sweep Variable: Internal node voltages
Purpose: Static characteristics
Output:
  - Butterfly curve
  - SNM calculation
  - VTC curves
Results: See Image 2 (from earlier set)
```

### **3. AC Analysis** (if configured)
```
Type: Small-signal frequency response
Sweep: Frequency (Hz)
Purpose: Bandwidth, stability
Output: Bode plots
```

---

## Simulation Setup Procedure

### **Step-by-Step Workflow:**

#### **1. Testbench Creation** ✅ (This Image)
```
a. Create new cell (6t-sram_tets)
b. Instantiate DUT (6t-sram)
c. Add voltage sources (VDD, GND, WL, BL, BLB)
d. Connect all nets
e. Add output probes
f. Save schematic
```

#### **2. ADE L Configuration**
```
a. Launch ADE L (Tools → Analog Environment)
b. Setup → Simulator/Directory/Host
c. Choose simulator: Spectre
d. Select design: 6t-sram_tets
```

#### **3. Analysis Setup**
```
a. Analysis → Choose Analysis
b. Select: Transient
c. Set stop time: 10ns
d. Set step: Auto
e. Enable: Moderate accuracy
```

#### **4. Define Outputs**
```
a. Outputs → To be plotted → Select on Schematic
b. Click on nets: q, qbar, wl
c. Or add manually: /q, /qbar, /wl
```

#### **5. Run Simulation**
```
a. Simulation → Netlist and Run
b. Monitor output window
c. Check for convergence
d. View results automatically

```

---

## Measurement Points and Probes

### **Critical Signals to Monitor:**

**1. Storage Nodes (q, qbar):**
```
Purpose: Verify data storage
Expected: Complementary voltages
Metrics: 
  - Voltage levels
  - Stability
  - Switching time
```

**2. Wordline (wl):**
```
Purpose: Verify timing control
Expected: Clean pulse
Metrics:
  - Edge timing
  - Voltage levels
  - Pulse width
```

**3. Bitlines (bl, blb):**
```
Purpose: Verify data transfer
Expected: Driven or precharged
Metrics:
  - Voltage levels
  - Slew rates
  - Differential
```

**4. Supply Current (VDD):**
```
Purpose: Power consumption
Method: Measure VDD source current
Metrics:
  - Static current (leakage)
  - Dynamic current (switching)
  - Peak current
```

---

## Design Verification Checklist

### **What This Testbench Verifies:**

✅ **Functional Tests:**
- Write operation (change cell state)
- Read operation (sense cell state)
- Hold operation (maintain data)
- State flip verification

✅ **Parametric Tests:**
- Static Noise Margin (DC analysis)
- Access time (transient)
- Write time (transient)
- Hold time
- Setup/hold margins

✅ **Power Analysis:**
- Static power (leakage during hold)
- Dynamic power (during switching)
- Peak current draw
- Average power consumption

✅ **Timing Analysis:**
- Wordline-to-data delay
- Data valid window
- Minimum WL pulse width
- Recovery time

---

## Testbench Variables (Typical)

```
Design Variables (can be defined in ADE L):

VDD = 1.8          // Supply voltage
TEMP = 27          // Temperature (°C)
VWL_HIGH = 1.5     // WL high voltage
VWL_LOW = 0        // WL low voltage
T_DELAY = 5n       // WL pulse delay
T_RISE = 50p       // WL rise time
T_FALL = 50p       // WL fall time
T_WIDTH = 5n       // WL pulse width
VBL_WRITE1 = 0     // BL for write-1
VBLB_WRITE1 = 1.8  // BLB for write-1
```

---

## Copy-Paste Content for Reports

### **Testbench Description (Formal):**
```
A comprehensive testbench schematic (6t-sram_tets) was developed to verify the 
functionality and performance of the 6T-SRAM cell. The testbench instantiates 
the SRAM cell as the device under test (DUT) and provides all necessary stimulus 
through configurable voltage sources. A DC voltage source supplies 1.8V to the 
vdd pin, while pulse generators drive the wordline (WL) and bitlines (BL, BLB) 
with appropriate test waveforms. The ground reference is established through 
multiple ground symbols, ensuring proper connectivity. Output probes monitor the 
storage nodes (q, qbar) for waveform capture and analysis. The testbench supports 
both DC analysis for Static Noise Margin calculation and transient analysis for 
read/write operation characterisation. Simulations are configured for 27°C nominal 
temperature using the Cadence Spectre simulator through the Analog Design Environment 
(ADE L) interface.
```

### **Component Summary Table:**
```
| Component | Instance | Type | Value/Config | Purpose |
|-----------|----------|------|--------------|---------|
| DUT | 6t—SRAM | Hierarchical | 6-transistor cell | Device under test |
| VDD | vcs=d5 | DC Source | 1.8V | Power supply |
| WL | wl | Pulse | 0→1.5V @ 5ns | Access control |
| BL | bl | Voltage | Variable | Bitline data |
| BLB | blb | Voltage | Variable | Comp. bitline |
| GND | Multiple | Ground | 0V | Reference |
| Probe | qbar | Output | Monitor | Measurement |
| Probe | q | Output | Monitor | Measurement |
```

### **Simulation Configuration:**
```
Testbench Cell: 6t-sram_tets
DUT Cell: 6t-sram (6 transistors)
Environment: ADE L (Analog Design Environment)
Simulator: Spectre (Cadence)
Temperature: 27°C (300K, nominal)
Supply Voltage: 1.8V (VDD)
Analysis Types: Transient (time-domain), DC (sweep)
Transient Duration: 10ns typical
Time Resolution: Adaptive (automatic)
Accuracy: Moderate (standard)
Output Format: PSF (Parametric Simulation Format)
Results Path: /home/cadence/simulation/6t-sram_tets/spectre/schematic/psf
```

---

## Stimulus Timing Diagram

### **Typical Test Sequence:**

```
Time (ns)  | WL    | BL      | BLB     | Operation
-----------|-------|---------|---------|------------------
0.0-5.0    | 0V    | Float   | Float   | HOLD (initial)
5.0        | ↑1.5V | Set     | Set     | Enable access
5.0-6.0    | 1.5V  | Driven  | Driven  | WRITE/READ active
6.0-10.0   | 1.5V  | Hold    | Hold    | Maintain/Settle

Example Write-1:
5.0-10.0   | 1.5V  | 0V      | VDD     | Write '1' to q

Example Read:
5.0-10.0   | 1.5V  | VDD     | VDD     | Read stored data
```

---

## Advanced Testbench Features

### **Parametric Sweeps** (Can Be Added):
```
VDD Sweep: 1.6V to 2.0V (voltage scaling study)
Temperature Sweep: -40°C to 125°C (corner analysis)
Process Corners: FF, TT, SS, FS, SF
Monte Carlo: Statistical variation analysis
```

### **Measurement Commands** (In Spectre):
```
.meas tran t_access WHEN v(q)=0.9*VDD RISE=1
.meas tran t_write TRIG v(wl) VAL=0.9 RISE=1 TARG v(q) VAL=0.9*VDD RISE=1
.meas tran i_avg AVG i(V_VDD) FROM=0 TO=10n
.meas dc snm PARAM='...'
```

---

## Troubleshooting Tips

### **Common Issues:**

**1. Convergence Failure:**
```
Problem: Simulation doesn't converge
Solutions:
  - Check initial conditions (ic parameter)
  - Increase reltol/abstol
  - Add capacitors to floating nodes
  - Check for missing connections
```

**2. Incorrect Waveforms:**
```
Problem: Unexpected signal behaviour
Solutions:
  - Verify source connections
  - Check pulse parameters (delays, widths)
  - Confirm VDD/GND connectivity
  - Review cell pin mapping
```

**3. Missing Outputs:**
```
Problem: Signals not appearing in results
Solutions:
  - Verify output selection in ADE L
  - Check net names (case-sensitive)
  - Ensure probes are connected
  - Re-run simulation
```

---

## Relationship to Other Images

### **This Testbench Generates:**
- **Image 7** (New Image 2): Transient response with solid lines
- **Image 8** (New Image 3): Transient response with dotted lines
- **Previous Images**: Write operation (Image 4), Read operation (earlier)

### **This Testbench Tests:**
- **Core Cell**: 6T-SRAM schematic (Image 1, 5)
- **Layout**: Physical implementation (Image 3)
- **DC Behaviour**: Butterfly curve analysis (Image 2)

---

**Temperature**: 27°C (300K)  
**Previous**: [Simplified Schematic](IMAGE_5_EXPLANATION.md)  
**Next**: [Transient Response - Solid Lines](../simulations/IMAGE_7_EXPLANATION.md)
