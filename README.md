# Custom-RISC-V-SoC-with-On-Chip-Neural-Network-Accelerator

A custom System-on-Chip (SoC) integrating a RISC-V processor with a dedicated hardware Neural Network Accelerator (NPU), designed to explore hardware-software co-design, parallel neural network computation, and efficient AI inference at the edge.

The project aims to develop a programmable RISC-V-based computing platform capable of executing general-purpose applications while accelerating computationally intensive neural network workloads through a dedicated hardware accelerator.

## Project Overview

The proposed SoC combines a RISC-V processor core, on-chip memory, a system interconnect, and a custom neural network accelerator into a unified architecture.

The RISC-V processor acts as the main control and execution unit, managing program execution, memory operations, peripheral communication, and accelerator configuration.

The Neural Network Accelerator offloads computationally intensive operations such as:

* Matrix multiplication

* Multiply-Accumulate (MAC) operations

* Convolution

* Activation functions

* Neural network inference

The accelerator communicates with the processor through a memory-mapped control interface and a high-bandwidth data interface.

## Key Features

* Custom RISC-V processor-based SoC architecture

* On-chip Neural Network Processing Unit (NPU)

* Hardware-accelerated matrix multiplication

* Parallel Multiply-Accumulate (MAC) datapath

* Convolution computation support

* Configurable neural network accelerator

* Memory-mapped accelerator control registers

* AXI4 / AXI4-Lite-based communication architecture

* On-chip SRAM and shared memory architecture

* Hardware-software co-design

* Modular RTL implementation using Verilog/SystemVerilog

* Functional verification using SystemVerilog testbenches

* FPGA prototyping and testing

* Open-source RTL synthesis and physical design flow

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
```

Component            Description

RISC-V CPU           Executes software instructions and controls the SoC

System Interconnect  Enables communication between processing units and peripherals

NPU                  Performs hardware-accelerated neural network operations

MAC Array            Executes parallel multiplication and accumulation

Convolution Unit     Performs convolution operations

Activation Unit      Supports ReLU and other activation functions

On-Chip SRAM         Stores instructions, weights, inputs, and intermediate results

Control Registers    Configure accelerator operations

Peripheral Interface Supports external communication and debugging

```

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


## Hardware-Software Co-Design

The system uses a software-controlled hardware acceleration model.

### Execution Flow

The RISC-V processor boots and executes the application.

Input data is loaded into on-chip memory.

Neural network weights are stored in accelerator-accessible memory.

The CPU configures the accelerator through memory-mapped registers.

The CPU issues a start command.

The NPU performs parallel MAC and convolution operations.

The accelerator stores computation results in memory.

The accelerator signals completion through a status register or interrupt.

The RISC-V processor retrieves and processes the results.

### Software Stack

The software component can include:

C/C++ application code

Neural network model preprocessing

Accelerator driver

Memory-mapped register access

Input and weight loading routines

Inference result evaluation

Python can be used for:

Training neural network models

Quantization and preprocessing

Generating hardware-compatible weights

Comparing software and hardware inference results

Performance analysis

## Verification Methodology

The SoC should be verified at individual module level and system level.

### Module-Level Verification
```
Module                        Verification Focus

RISC-V CPU                    Instruction execution and architectural correctness

MAC Array                     Multiplication and accumulation accuracy

Convolution Unit             Convolution output correctness

Activation Unit              Activation function correctness

Memory Controller            Read/write operations

System Interconnect          Transaction and arbitration behavior

NPU Controller               Control and status functionality
```

### System-Level Verification      

* CPU-to-NPU communication

* Memory access and data integrity

* Accelerator initialization

* Neural network inference execution

* Interrupt handling

* Reset and recovery

* Back-to-back accelerator operations

### Verification Tools

* SystemVerilog

* Verilator

* GTKWave

* QuestaSim / ModelSim (optional)

* Python-based reference models

## FPGA Development Tools

* AMD Xilinx Vivado

* Verilog / SystemVerilog

* Xilinx FPGA development boards

* Integrated Logic Analyzer (ILA)

### FPGA Evaluation

* The implementation can be evaluated using:

* Maximum operating frequency

* LUT utilization

* Flip-flop utilization

* BRAM utilization

* DSP utilization

* Inference latency

* Accelerator throughput

* Power consumption (where supported)

## Physical Design Stages

* RTL Design

* RTL Simulation

* Lint Analysis

* Logic Synthesis

* Floorplanning

* Power Planning

* Placement

* Clock Tree Synthesis

* Routing

* Static Timing Analysis

* Design Rule Checking

## TOOLS USED
```
### Category                        Technologies

HDL                             Verilog, SystemVerilog

Processor Architecture          RISC-V

Bus Protocol                    AXI4, AXI4-Lite

Verification                    SystemVerilog, Python

Programming                     C, C++, Python

Simulation                      Verilator, GTKWave

FPGA                            AMD Xilinx Vivado

Synthesis                       Yosys

Physical Design                 OpenROAD, OpenLane

Layout                          Magic VLSI, KLayout

Version Control                Git, GitHub

Operating System               Linux
```
## Repository Structure
``` 
Custom-RISC-V-SoC-with-On-Chip-Neural-Network-Accelerator/
│
├── README.md
├── LICENSE
├── .gitignore
├── Makefile
│
├── docs/
│   ├── architecture/
│   │   ├── soc_block_diagram.png
│   │   ├── risc_v_architecture.png
│   │   ├── npu_architecture.png
│   │   └── memory_architecture.png
│   │
│   ├── design/
│   │   ├── design_specification.md
│   │   ├── interface_specification.md
│   │   └── memory_map.md
│   │
│   └── reports/
│       ├── synthesis_report.md
│       ├── timing_report.md
│       └── verification_report.md
│
├── rtl/
│   ├── cpu/
│   │   ├── riscv_core.sv
│   │   ├── program_counter.sv
│   │   ├── instruction_decoder.sv
│   │   ├── register_file.sv
│   │   ├── alu.sv
│   │   └── control_unit.sv
│   │
│   ├── npu/
│   │   ├── npu_top.sv
│   │   ├── npu_controller.sv
│   │   ├── mac_unit.sv
│   │   ├── mac_array.sv
│   │   ├── convolution_engine.sv
│   │   ├── activation_unit.sv
│   │   └── pooling_unit.sv
│   │
│   ├── interconnect/
│   │   ├── axi_interconnect.sv
│   │   ├── axi_lite_slave.sv
│   │   └── bus_arbiter.sv
│   │
│   ├── memory/
│   │   ├── instruction_memory.sv
│   │   ├── data_memory.sv
│   │   ├── npu_memory.sv
│   │   └── memory_controller.sv
│   │
│   ├── peripherals/
│   │   ├── gpio.sv
│   │   ├── uart.sv
│   │   └── timer.sv
│   │
│   └── soc_top.sv
│
├── verification/
│   ├── cpu_tb/
│   ├── npu_tb/
│   ├── mac_tb/
│   ├── convolution_tb/
│   ├── memory_tb/
│   └── soc_tb/
│
├── software/
│   ├── firmware/
│   │   ├── main.c
│   │   ├── npu_driver.c
│   │   └── npu_driver.h
│   │
│   ├── applications/
│   │   └── neural_network_inference/
│   │
│   └── linker/
│       └── linker.ld
│
├── python/
│   ├── model_training/
│   ├── model_quantization/
│   ├── weight_converter/
│   ├── reference_model/
│   └── performance_analysis/
│
├── fpga/
│   ├── constraints/
│   ├── scripts/
│   └── vivado_project/
│
├── physical_design/
│   ├── synthesis/
│   ├── floorplan/
│   ├── placement/
│   ├── routing/
│   └── timing_analysis/
│
├── simulation/
│   ├── scripts/
│   ├── waveforms/
│   └── logs/
│
└── results/
    ├── simulation/
    ├── synthesis/
    ├── fpga/
    └── performance/
```
## Applications

* Edge AI computing

* Embedded artificial intelligence

* Smart sensors

* Image classification

* Industrial automation

* IoT devices

* Low-power AI inference

* Autonomous embedded systems
