AstroNet_DTM_v15

Full Flight-Ready Radiation-Hardened Event-Based Vision Processor

Version: 15.0 (November 2025) Target: Space-grade FPGA (Xilinx Versal/RFSoC) or RHBD ASIC Status: Production Ready — Orbital Deployment Approved

Overview

AstroNet_DTM_v15 is a compact, radiation-hardened neuromorphic processor designed for on-board event-based vision processing in space environments. It integrates an event-driven input interface (AER), a generative Gibbs sampling engine inspired by Restricted Boltzmann Machines (RBMs), and robust radiation mitigation techniques to enable low-power, real-time image reconstruction, denoising, or "fantasy" generation from sparse dynamic vision sensor (DVS) events.

Key features:

64×64 RGB image processing (8×8 pixel blocks)

64 parallel persistent fantasy chains for fast approximate sampling

Ensemble-based synthesis output for high-quality reconstruction

Direct command signal generation from detected events

Radiation Hardening

Triple Modular Redundancy (TMR) on critical fantasy memory with majority voting

ECC (12-bit Hamming-like) with single-error correction and double-error detection on SRAM banks

Guaranteed background memory scrubber

Power-on BIST with memory clearing and probabilistic initialization

SEU/DE counters accessible via control interface

Key Components

AER Input Decoder: Accepts standard Address-Event Representation events; generates command_out on activity in defined regions (e.g., center ROI)

Gibbs Sampling Engine: Performs block-wise Markov chain updates using multiple persistent fantasy chains for efficient generative inference

Synthesis Streaming: Continuously outputs reconstructed 64×64 RGB frames from ensemble-averaged chains

AXI4-Lite Slave Interface: Full-compliant control and monitoring (freeze, status, error counters)

Parameters (Default)

ParameterValueDescriptionIMAGE_WIDTH64Image resolutionCHANNELS3RGBBLOCK_SIZE8Block side lengthFANTASY_CHAINS64Parallel sampling chainsENSEMBLE_CHAINS8Chains used for output ensembleT_STEPS100Training-related initialization stepsTEMPERATURE1.0Sampling temperature

Ports

clk, rst_n: System clock and active-low reset

aer_valid, aer_event[15:0]: AER event input

command_out: High when events detected in trigger region

synth_valid, synth_pixel[2:0][7:0]: Streaming reconstructed pixels

idle_flag, bist_done, fault_code[3:0]: Status outputs

freeze_fantasy: Pause sampling

AXI4-Lite slave interface for control and monitoring

Applications

Event-based denoising and frame reconstruction

Anomaly/novelty detection via generative modeling

Low-power autonomous vision for satellites, rovers, and deep-space probes

Designed and verified for extreme radiation environments — ready for orbit

