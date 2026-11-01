# Custom-RISC-V-SoC-with-On-Chip-Neural-Network-Accelerator

A custom System-on-Chip (SoC) integrating a RISC-V processor with a dedicated hardware Neural Network Accelerator (NPU), designed to explore hardware-software co-design, parallel neural network computation, and efficient AI inference at the edge.

The project aims to develop a programmable RISC-V-based computing platform capable of executing general-purpose applications while accelerating computationally intensive neural network workloads through a dedicated hardware accelerator.

## Project Overview

The proposed SoC combines a RISC-V processor core, on-chip memory, a system interconnect, and a custom neural network accelerator into a unified architecture.

The RISC-V processor acts as the main control and execution unit, managing program execution, memory operations, peripheral communication, and accelerator configuration.

The Neural Network Accelerator offloads computationally intensive operations such as:

Matrix multiplication

Multiply-Accumulate (MAC) operations

Convolution

Activation functions

Neural network inference

The accelerator communicates with the processor through a memory-mapped control interface and a high-bandwidth data interface.

