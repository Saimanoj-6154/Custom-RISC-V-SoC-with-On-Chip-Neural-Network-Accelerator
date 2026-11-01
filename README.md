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

## Key Features

Custom RISC-V processor-based SoC architecture

On-chip Neural Network Processing Unit (NPU)

Hardware-accelerated matrix multiplication

Parallel Multiply-Accumulate (MAC) datapath

Convolution computation support

Configurable neural network accelerator

Memory-mapped accelerator control registers

AXI4 / AXI4-Lite-based communication architecture

On-chip SRAM and shared memory architecture

Hardware-software co-design

Modular RTL implementation using Verilog/SystemVerilog

Functional verification using SystemVerilog testbenches

FPGA prototyping and testing

Open-source RTL synthesis and physical design flow

## System Architecture
```

                  CUSTOM RISC-V SoC
+------------------------------------------------------+
|                                                      |
|  +-------------------+                               |
|  |   RISC-V CPU      |                               |
|  |                   |                               |
|  | Fetch / Decode    |                               |
|  | Execute / Memory  |                               |
|  | Writeback         |                               |
|  +---------+---------+                               |
|            |                                         |
|            |                                         |
|  +---------v--------------------------------------+  |
|  |             System Interconnect                |  |
|  |              AXI / AHB Bus                     |  |
|  +------+---------------------------+-------------+  |
|         |                           |                |
|  +------v------+             +------v-------------+  |
|  | On-Chip RAM |             | Neural Network     |  |
|  | / SRAM      |             | Accelerator (NPU)  |  |
|  +-------------+             +------+-------------+  |
|                                       |              |
|                              +--------v---------+    |
|                              | MAC Array        |    |
|                              | Convolution Unit |    |
|                              | Activation Unit  |    |
|                              | Control Unit     |    |
|                              +------------------+    |
|                                                      |
|  +-------------------+                               |
|  | Peripheral        |                               |
|  | Interface         |                               |
|  +-------------------+                               |
|                                                      |
+------------------------------------------------------+
```
## Major Components

Component

Description

RISC-V CPU

Executes software instructions and controls the SoC

System Interconnect

Enables communication between processing units and peripherals

NPU

Performs hardware-accelerated neural network operations

MAC Array

Executes parallel multiplication and accumulation

Convolution Unit

Performs convolution operations

Activation Unit

Supports ReLU and other activation functions

On-Chip SRAM

Stores instructions, weights, inputs, and intermediate results

Control Registers

Configure accelerator operations

Peripheral Interface

Supports external communication and debugging



## Hardware Architecture

## 1. RISC-V Processor Core

The RISC-V processor serves as the primary processing unit.

The processor is responsible for:

Instruction fetching and decoding

Arithmetic and logical operations

Memory access

Accelerator configuration

Interrupt handling

Data transfer between memory and accelerator

The initial implementation can use a basic RV32I-compatible processor architecture.

Potential extensions include:

RV32IM instruction set

Custom accelerator instructions

Custom control and status registers

## 2. Neural Network Accelerator (NPU)

The NPU is a dedicated hardware unit designed to accelerate neural network inference.

Instead of executing every neural network operation sequentially on the CPU, the accelerator processes multiple arithmetic operations in parallel.

Its architecture consists of:

MAC Processing Array

Performs parallel multiplication and accumulation operations.



### Convolution Engine

Performs convolution operations using input feature maps and trained neural network weights.

Activation Unit

Supports activation functions such as:

ReLU

Sigmoid (optional)

Tanh (optional)

### Control Unit

Manages accelerator operation, including:

Start and stop control

Operation selection

Data loading

Computation scheduling

Completion status

Interrupt generation

### 3. Memory Architecture

The SoC uses an on-chip memory subsystem to minimize data transfer overhead.

Memory stores:

CPU instructions

Input feature maps

Neural network weights

Intermediate feature maps

Final inference results

The architecture can use separate instruction and data memories or a shared memory subsystem.
