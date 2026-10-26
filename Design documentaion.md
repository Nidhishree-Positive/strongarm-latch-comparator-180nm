
# Design and Analysis of StrongARM Latch Comparator

## 1. Abstract

Comparators are fundamental building blocks in analog and mixed-signal integrated circuits. They are widely used in Analog-to-Digital Converters (ADCs), data converters, sensing circuits, and communication systems.

This project focuses on the design and analysis of a StrongARM latch comparator implemented using 180 nm CMOS technology. The comparator uses regenerative positive feedback to achieve fast decision-making during the evaluation phase. Its dynamic operation helps minimize static power dissipation.

The circuit was designed and simulated using Cadence Virtuoso with a supply voltage of 1.8 V. Transient response, propagation delay, and power consumption were analyzed. Physical layout design was performed, followed by Design Rule Check (DRC), Layout Versus Schematic (LVS) verification, and post-layout simulation with parasitic extraction.

## 2. Introduction

A comparator compares two input voltages and produces an output indicating which input is larger. Comparators are essential components in analog and mixed-signal systems such as ADCs, sensing circuits, memory circuits, and communication systems.

The StrongARM latch comparator is a dynamic regenerative comparator that operates in two clock-controlled phases: reset and evaluation.

During reset, the output nodes are precharged toward the supply voltage. During evaluation, the differential input signal initiates an imbalance between the output nodes. Regenerative positive feedback amplifies this imbalance and drives the outputs toward opposite logic states.

### Key Advantages

- High-speed operation
- Low dynamic power consumption
- No idealized static current path during the hold/reset condition
- Regenerative positive feedback
- Compact transistor-level architecture
- Suitability for high-speed ADC applications

## 3. Applications

StrongARM comparators are used in several analog and mixed-signal applications.

### 3.1 Flash ADC

Flash ADCs use multiple comparators to compare an input voltage against different reference levels. Fast comparator decisions support high-speed conversion.

### 3.2 Successive Approximation Register (SAR) ADC

A comparator determines whether the sampled input voltage is greater or smaller than the DAC output during the conversion process.

### 3.3 Sense Amplifiers

Regenerative sensing circuits can detect small voltage differences in memory and other sensing applications.

### 3.4 High-Speed Communication Receivers

Comparators support signal detection and related high-speed receiver functions.

### 3.5 Data Converters and Clock/Data Recovery

Comparators are important in analog-to-digital conversion and can also be used in timing and data-recovery circuits.

## 4. Design Specifications

| Parameter | Specification |
|---|---|
| Comparator architecture | StrongARM latch |
| CMOS technology | 180 nm |
| Supply voltage (VDD) | 1.8 V |
| Reference voltage | 900 mV |
| Simulation environment | Cadence Virtuoso |
| Input stimulus | Sinusoidal input centered around 900 mV |
| Main analyses | Transient, delay, power and post-layout |
| Physical verification | DRC and LVS |

## 5. Comparator Architecture

The StrongARM comparator consists of differential input transistors, latch transistors, reset transistors, and a clock-controlled tail transistor.

<img width="705" height="663" alt="Screenshot 2026-10-26 202334" src="https://github.com/user-attachments/assets/6f27aa4a-882c-400d-91f9-3536eb004cb6" />


### 5.1 Transistor Functions

According to the implemented circuit:

- **M1:** Tail transistor controlled by the clock signal.
- **M2 and M2′:** Differential input pair that senses the input voltage difference.
- **M3 and M3′:** NMOS latch transistors responsible for regenerative action.
- **M4 and M4′:** PMOS reset transistors used to precharge the output nodes.
- **M5 and M5′:** Cross-coupled PMOS latch transistors that provide positive feedback.

### 5.2 Transistor Sizing

The transistor dimensions used in the design are listed below.

| Transistor | Width / Length | Number of fingers |
|---|---|---:|
| M1 | 4 µm / 180 nm | 2 |
| M2 | 4 µm / 180 nm | 2 |
| M2′ | 4 µm / 180 nm | 2 |
| M3 | 2 µm / 180 nm | 1 |
| M3′ | 2 µm / 180 nm | 1 |
| M4 | 4 µm / 180 nm | 2 |
| M4′ | 4 µm / 180 nm | 2 |
| M5 | 4 µm / 180 nm | 2 |
| M5′ | 4 µm / 180 nm | 2 |

## 6. Working Principle

The comparator operates in two phases: reset and evaluation.

### 6.1 Reset Phase

When the clock signal is LOW:

- The tail transistor M1 remains OFF.
- The PMOS reset transistors M4 and M4′ turn ON.
- Both output nodes are precharged close to VDD.
- The differential evaluation path is disabled by the OFF tail transistor.

The output nodes are therefore prepared for the next comparison cycle.

**Reset phase conditions:**

- CLK = 0 V
- M1 = OFF
- M4 and M4′ = ON
- Vout+ and Vout− are approximately 1.8 V

**[Insert Figure 3: Reset phase waveform]**

### 6.2 Evaluation Phase

When the clock signal becomes HIGH:

- M1 turns ON.
- M4 and M4′ turn OFF.
- The differential input pair begins discharging the internal/output nodes.
- The input voltage difference creates an imbalance between the two branches.
- Cross-coupled regenerative feedback amplifies the imbalance.
- The output nodes move toward opposite logic states.

For the input condition Vin+ > Vin−, the differential pair initiates an imbalance that is amplified by the latch. The final output polarity depends on the circuit's input/output connections.

**Evaluation phase conditions:**

- CLK = 1.8 V
- M1 = ON
- M4 and M4′ = OFF
- Regenerative feedback is active


## 7. Simulation and Performance Analysis

<img width="707" height="502" alt="Screenshot 2026-10-26 203006" src="https://github.com/user-attachments/assets/d4a53ff6-5bf7-4e29-b046-3af32d9d0e55" />


The circuit was simulated in Cadence Virtuoso to evaluate its dynamic behavior and performance.

### 7.1 Transient Analysis

<img width="710" height="416" alt="Screenshot 2026-10-26 203208" src="https://github.com/user-attachments/assets/172d8c30-c734-4b69-9d13-5dac30254799" />


Transient analysis was performed to verify the comparator's operation.

The simulation used a 1.8 V supply and a reference voltage of 900 mV. A sinusoidal input signal centered around 900 mV was used to observe the output response.

During the reset phase, both output nodes were precharged close to 1.8 V. During evaluation, the output state changed according to the input voltage relative to the reference.

The report records the following input conditions:

- Vin = 901.7768 mV and 909.9954 mV, both greater than Vref = 900 mV.
- Vin = 890.015 mV, less than Vref = 900 mV.

The corresponding output transitions were reported to confirm comparison around the reference level.


### 7.2 Propagation Delay Analysis

<img width="599" height="214" alt="image" src="https://github.com/user-attachments/assets/b917ea54-18ce-4934-a884-ecd95afe7177" />


Propagation delay was evaluated to measure the time taken by the comparator to resolve the input and produce a valid output.

The delay was measured using the `delay()` function in the Cadence Calculator. The trigger was selected at the 50% rising edge of the clock signal, corresponding to 0.9 V for a 1.8 V clock swing. The target was the 50% transition point of the output waveform.

**Reported pre-layout propagation delay: 87.99 ps**


### 7.3 Power Analysis

The supply current drawn from the VDD source was monitored during transient simulation. The average current was calculated using the `average()` function in the Cadence Calculator.

The report gives the following pre-layout values:
<img width="599" height="214" alt="image" src="https://github.com/user-attachments/assets/b917ea54-18ce-4934-a884-ecd95afe7177" />
- Average supply current: 10.302 µA
- Supply voltage: 1.8 V
- Average power consumption: approximately 18.5 µW

The reported power was calculated using:

P = VDD × Iavg

The average power depends on the applied input stimulus, clock activity, and simulation interval.


## 8. Physical Layout Design
<img width="675" height="614" alt="Screenshot 2026-10-26 203338" src="https://github.com/user-attachments/assets/7d2eaefe-8332-4cd5-840a-bee8856c9a29" />

The comparator layout was implemented using Cadence Virtuoso following standard CMOS layout practices.

The layout considerations documented in the project include:

- PMOS devices placed near the VDD rail and NMOS devices near the VSS rail.
- Multi-finger transistor structures used for compact implementation.
- Routing arranged to connect the differential pair, latch stage, and output nodes.
- Wider metal power rails provided for VDD and VSS.

Symmetric placement and routing are important considerations for matching the differential branches.



## 9. Physical Verification

### 9.1 Design Rule Check (DRC)

DRC verification was performed after completing the layout. The design was checked against the applicable 180 nm CMOS layout rules, including width, spacing, enclosure, and overlap constraints.

The report records **zero DRC violations**.

<img width="616" height="395" alt="Screenshot 2026-10-26 203551" src="https://github.com/user-attachments/assets/4af2a2ce-df82-4304-9a06-da239966603f" />


### 9.2 Layout Versus Schematic (LVS)

LVS verification was performed to compare the physical layout against the schematic netlist. The verification checks device correspondence and circuit connectivity.

The report records a **successful LVS match**.
<img width="593" height="526" alt="Screenshot 2026-10-26 203612" src="https://github.com/user-attachments/assets/adfb996a-9efe-4ad2-a6e6-84c71b149048" />


## 10. Post-Layout Analysis

Parasitic extraction was performed after layout completion to account for interconnect resistance and capacitance. Simulation using the extracted view was then compared with schematic-level results.

The report states that the comparator continued to operate correctly after extraction.

### 10.1 Pre-Layout and Post-Layout Comparison

| Parameter | Pre-layout | Post-layout |
|---|---:|---:|
| Propagation delay | 87.99 ps | To be confirmed |
| Average current | 10.302 µA | 10.44 µA |
| Average power | 18.5 µW | 18.6 µW |

**Note:** The original report contains inconsistent post-layout delay values: 87.2 ps in the discussion and 88.2 ps in the comparison table. The correct value must be confirmed from the original simulation results before final publication.

The reported average current and power increase slightly after parasitic extraction. Such differences may arise from the additional resistance and capacitance introduced by the physical implementation.
<img width="714" height="466" alt="image" src="https://github.com/user-attachments/assets/02b083ae-d3a9-4d9d-bea4-ccbfd0c26869" />


<img width="670" height="276" alt="image" src="https://github.com/user-attachments/assets/becd893a-aef9-4136-bcf9-0fb056d9cceb" />


## 11. Results Summary

| Specification | Reported result |
|---|---|
| Technology node | 180 nm CMOS |
| Architecture | StrongARM latch comparator |
| Supply voltage | 1.8 V |
| Reference voltage | 900 mV |
| Input signal | Sinusoidal |
| Pre-layout propagation delay | 87.99 ps |
| Pre-layout average current | 10.302 µA |
| Pre-layout average power | 18.5 µW |
| DRC status | Passed; zero reported violations |
| LVS status | Successful match |
| Post-layout verification | Reported successful |

These values are simulation results reported for this particular design and testbench. They are not silicon measurement results.

## 12. Conclusion

A StrongARM latch comparator was designed and analyzed using 180 nm CMOS technology in Cadence Virtuoso.

The design was evaluated through transient response, propagation delay, and average power analysis. Physical layout was completed and the report records successful DRC and LVS verification. Post-layout simulation was also performed after parasitic extraction.

The reported pre-layout results include a propagation delay of 87.99 ps, average current consumption of 10.302 µA, and average power consumption of approximately 18.5 µW.

The project provided practical experience in transistor-level CMOS design, dynamic comparator operation, circuit simulation, physical layout, verification, and post-layout analysis.

## 13. References

1. Behzad Razavi, *Design of Analog CMOS Integrated Circuits*, 2nd Edition, McGraw-Hill Education, 2016.
2. R. Jacob Baker, *CMOS Circuit Design, Layout, and Simulation*, 4th Edition, Wiley-IEEE Press, 2019.
3. Cadence Design Systems, *Cadence Virtuoso Analog Design Environment User Guide*.
4. B. Razavi, “The StrongARM Latch Comparator,” *IEEE Solid-State Circuits Magazine*, Vol. 7, No. 2, pp. 12–17, 2015.

## Contributors

- Nidhishree
- Pooja K N

Academic project completed for the Principles of Digital VLSI course at The National Institute of Engineering, Mysuru.
