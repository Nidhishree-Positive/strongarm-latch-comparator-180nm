
# StrongARM Latch Comparator — 180 nm CMOS

## Overview

This project presents the design and analysis of a StrongARM latch comparator implemented using 180 nm CMOS technology in Cadence Virtuoso.

The comparator uses a clock-controlled dynamic architecture and regenerative positive feedback to resolve the differential input voltage into a digital output.

## Project Objectives

- Understand the operating principle of a StrongARM latch comparator.
- Design and simulate the comparator using Cadence Virtuoso.
- Analyze transient response, propagation delay, and average power.
- Implement the transistor-level circuit layout.
- Verify the layout using Design Rule Check (DRC) and Layout Versus Schematic (LVS).
- Evaluate circuit operation after parasitic extraction.

## Design Specifications

| Parameter | Value |
|---|---|
| CMOS technology | 180 nm |
| Supply voltage | 1.8 V |
| Reference voltage | 900 mV |
| Comparator architecture | StrongARM latch |
| Design and simulation tool | Cadence Virtuoso |

## Performance Results

| Parameter | Reported result |
|---|---:|
| Pre-layout propagation delay | 87.99 ps |
| Pre-layout average current | 10.302 µA |
| Pre-layout average power | 18.5 µW |
| DRC | Zero reported violations |
| LVS | Successful match |

*Results are taken from the project report. The post-layout delay will be confirmed against the original simulation data before final publication.*

## Circuit Operation

### Reset Phase

When the clock is low, the tail transistor is off and the output nodes are precharged toward the supply voltage.

### Evaluation Phase

When the clock is high, the differential input pair develops a voltage difference. Regenerative positive feedback amplifies this difference, driving the output nodes toward opposite logic states.

## Design and Verification Flow

1. Transistor-level schematic design
2. Transient response simulation
3. Propagation delay analysis
4. Average power analysis
5. Physical layout implementation
6. DRC and LVS verification
7. Parasitic extraction and post-layout simulation

## Project Documentation

The final project report and supporting design evidence will be added to this repository after checking publication permissions.

## Tools and Technology

- Cadence Virtuoso
- 180 nm CMOS technology
- Transient and performance analysis
- CMOS layout and physical verification

## Contributors

- Nidhishree
- Pooja K N

This project was completed as part of the Principles of Digital VLSI course at The National Institute of Engineering, Mysuru.

## Disclaimer

This repository documents an academic project. Results are specific to the design, simulation conditions, and technology environment used. They should not be interpreted as silicon measurement results.
