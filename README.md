# OVERVIEW_OF_VLSI_TRAINING
VIDEO:
https://drive.google.com/file/d/1mN84BGHExR-eal7gJ1Es0U1S6XU51ilc/view?usp=drivesdk




This repository documents my learning and practical work in Very Large Scale Integration (VLSI) design, covering the complete digital design flow from Register Transfer Level (RTL) coding and functional verification to synthesis, physical design, and Static Timing Analysis (STA).

The training was carried out in a Linux-based environment using Oracle VirtualBox. It includes Verilog coding exercises, simulation waveforms, synthesized netlists, physical-design results, and timing-analysis reports.

The primary objective was to understand how a digital design progresses from RTL description to physical implementation while maintaining functional correctness and meeting timing constraints.

## Objectives

* Understand digital design using Verilog HDL.
* Develop and verify combinational and sequential circuits.
* Learn RTL simulation and waveform analysis.
* Understand synthesis and technology mapping.
* Study standard-cell libraries and flip-flop behavior.
* Compare RTL simulation with Gate-Level Simulation (GLS).
* Design and verify a Sequence Detector.
* Explore the BabySoC simulation and synthesis flow.
* Learn floorplanning, placement, clock-tree synthesis, and routing.
* Understand CMOS inverter layout and electrical characterization.
* Analyze setup timing, hold timing, and timing slack.
* Explore Static Timing Analysis across process, voltage, and temperature (PVT) corners.


## Topics Covered

### 1. Working Environment

The projects were organized and executed in a Linux environment running inside Oracle VirtualBox. Linux commands were used to manage files, navigate directories, execute design tools, and inspect simulation outputs and reports.

This environment provided practical exposure to command-line workflows and project organization for digital-design and physical-design tasks.

### 2. RTL Design and Simulation

Register Transfer Level (RTL) design describes digital hardware using Verilog HDL. It represents combinational logic, sequential logic, data transfers, and control behavior.

The training covered basic circuits such as a two-to-one multiplexer, Verilog modules, testbench development, simulation, and waveform verification.

A two-to-one multiplexer selects one of two inputs based on a select signal:



RTL simulation was used to apply test inputs and verify whether the circuit produced the expected outputs.

**Key learning:** Verilog coding, testbench creation, functional simulation, and waveform analysis.

### 3. Synthesis and Technology Libraries

Synthesis converts RTL code into a gate-level netlist by analyzing and optimizing the design. Technology mapping selects suitable standard cells from a target technology library.

The training covered standard-cell libraries, Liberty (`.lib`) files, hierarchical synthesis, flattened synthesis, synthesis statistics, and netlist inspection.

Liberty files provide cell information such as functionality, timing characteristics, area, and input capacitance.

**Key learning:** RTL-to-netlist conversion, technology mapping, logic optimization, and synthesis-report analysis.

### 4. Flip-Flops and Sequential Circuits

Sequential circuits store information and update their state according to clock and control signals. Flip-flops are fundamental elements used in registers, counters, and finite-state machines.

The training covered D flip-flops, synchronous and asynchronous resets, set behavior, and synthesis optimization.

* **Synchronous reset:** Takes effect at the applicable active clock edge.
* **Asynchronous reset:** Can take effect independently of the active clock edge.
* **Constant propagation:** Simplifies logic when signal values are known.

**Key learning:** Sequential logic, clocked behavior, reset semantics, and hardware inference.

### 5. Verilog Coding Practices

Verilog coding practices influence the hardware inferred by synthesis tools.

The topics included blocking and non-blocking assignments, conditional statements, loops, combinational and sequential procedural blocks, and complete signal assignments.

Incomplete assignments in combinational logic can infer latches because the circuit must preserve a previous value on some execution paths.

Digital circuit examples included multiplexers, demultiplexers, full adders, and ripple-carry adders.

**Key learning:** Coding style, procedural semantics, latch inference, and reliable RTL design.

### 6. Gate-Level Simulation (GLS)

Gate-Level Simulation verifies the synthesized netlist rather than the original RTL code. It helps determine whether the synthesized circuit behaves as expected for the applied test inputs.

RTL simulation focuses on the intended functional description, whereas GLS evaluates the gate-level representation. Depending on the simulation setup, GLS can use idealized cell models or timing annotations.

RTL and GLS waveforms can be compared to identify differences in output behavior and simulation timing.

**Key learning:** Post-synthesis verification, netlist simulation, waveform comparison, and functional checking.

### 7. Sequence Detector

A Sequence Detector is a digital circuit that recognizes a specified pattern in a serial input stream. It can be implemented using a Finite State Machine (FSM), where each state represents progress toward detecting the target sequence.

The project involved RTL implementation, testbench development, waveform analysis, synthesis using Yosys, inspection of the synthesized netlist, and Gate-Level Simulation.

The input sequence and detection output were examined to verify the behavior of the FSM. The exact detection cycle depends on the implemented state transitions and output logic.

**Key learning:** FSM design, state transitions, sequence recognition, synthesis, and RTL-versus-GLS verification.

### 8. BabySoC Simulation and Synthesis

A System-on-Chip (SoC) integrates multiple functional components into a larger design. The BabySoC exercises provided exposure to design hierarchy, simulation, synthesis, and netlist verification.

The workflow included examining design files, running simulations, synthesizing the design, inspecting available synthesis statistics, and comparing pre-synthesis and post-synthesis behavior.

**Key learning:** Design hierarchy, SoC verification, synthesis statistics, and post-synthesis checking.

### 9. Physical Design and RTL-to-GDSII Flow

Physical design transforms a synthesized netlist into a physical layout for integrated-circuit implementation.

The training introduced OpenLane, OpenROAD, and the SKY130 Process Design Kit (PDK).

A typical physical-design flow includes:

1. RTL design and verification.
2. Synthesis and technology mapping.
3. Floorplanning and power planning.
4. Standard-cell placement.
5. Clock-tree synthesis.
6. Routing.
7. Parasitic extraction.
8. Static Timing Analysis.
9. Physical verification and final layout generation.

**Key learning:** The relationship between RTL, synthesized logic, physical layout, and timing constraints.

### 10. Floorplanning and Placement

Floorplanning defines the physical organization of the design, including core and die dimensions, input/output locations, and power distribution planning.

Important concepts include core utilization, aspect ratio, placement space, and routing resources.

Placement assigns physical locations to standard cells. Placement optimization attempts to improve timing, manage congestion, and reduce estimated interconnect costs.

Supporting images in the repository include:

* `floorplan.jpeg`
* `placement.jpeg`

**Key learning:** Physical area planning, standard-cell placement, utilization, and congestion awareness.

### 11. CMOS Inverter Layout and Characterization

A CMOS inverter uses PMOS and NMOS transistors to produce the logical complement of its input.

* When the input is LOW, the output is driven HIGH.
* When the input is HIGH, the output is driven LOW.

The training covered transistor-level operation, layout design, physical layers, SPICE netlists, circuit simulation using ngspice, layout inspection using Magic, and design rule checking.

Electrical characterization involves analyzing switching behavior, propagation delay, rise time, and fall time.

Supporting images include:

* `inv layout.jpeg`
* `inv_waveform.jpeg`

**Key learning:** CMOS operation, transistor-level design, layout inspection, circuit simulation, and electrical characterization.

### 12. Clock-Tree Synthesis (CTS)

Clock-tree synthesis builds a clock distribution network to deliver clock signals to sequential elements across a design.

Clock buffers and other clock-tree cells may be used to manage loading, insertion delay, transition time, and clock arrival differences.

Important concepts include:

* **Clock insertion delay:** The propagation time from a clock reference point to a destination.
* **Clock skew:** The difference in clock arrival time between two points.
* **Clock transition:** The time taken for a clock signal to change between logic levels.

CTS affects setup and hold timing, so timing analysis is important after clock-tree implementation.

Supporting images include `cts.jpeg` and `cts2.jpeg`.

**Key learning:** Clock distribution, clock buffers, insertion delay, skew, and timing implications.

### 13. Routing and Timing Analysis

Routing creates physical electrical connections between cells using metal layers and vias.

* **Global routing:** Plans approximate routes and allocates routing resources.
* **Detailed routing:** Creates precise interconnect geometry while satisfying routing and design rules.

Physical wires introduce resistance and capacitance, known as parasitic effects. These affect signal delay and are important in post-route timing analysis.

Static Timing Analysis (STA) checks timing paths without requiring exhaustive functional simulation.

**Setup timing** checks whether data arrives sufficiently early before the capture clock edge.

**Hold timing** checks whether data remains stable for the required interval after the capture clock edge.

**Timing slack** indicates the margin between the required and actual timing:

* Positive slack generally indicates that the requirement is met.
* Zero slack indicates that the requirement is met with no margin.
* Negative slack indicates a timing violation.

Supporting images include `routingg.jpeg`, `setup.jpeg`, and `hold.jpeg`.

**Key learning:** Routing, parasitic effects, setup and hold checks, timing slack, and timing-report interpretation.

### 14. Multi-Corner Static Timing Analysis

Process, voltage, and temperature (PVT) conditions affect cell and circuit delays. Multi-corner Static Timing Analysis evaluates timing across selected operating conditions to help determine whether the design meets its timing constraints.

Timing reports provide information about path startpoints and endpoints, arrival times, required times, and slack. These metrics help identify critical paths and potential timing violations.

The `STA_Report_All_Corners` directory contains reference material for studying multi-corner timing reports. Reference reports should be distinguished from results independently generated for a particular design.

**Key learning:** PVT corners, critical-path analysis, timing reports, and multi-corner timing concepts.

## Tools and Technologies

| Tool or Technology | Purpose                                      |
| ------------------ | -------------------------------------------- |
| Verilog HDL        | RTL description of digital circuits          |
| Icarus Verilog     | Verilog compilation and simulation           |
| GTKWave            | Simulation waveform visualization            |
| Yosys              | RTL synthesis and netlist generation         |
| OpenLane           | Digital physical-design flow                 |
| OpenROAD           | Physical-design implementation               |
| SKY130 PDK         | Technology libraries and design rules        |
| Magic              | IC layout editing and inspection             |
| ngspice            | Circuit-level SPICE simulation               |
| Linux              | Command-line environment and file management |
| Oracle VirtualBox  | Virtual-machine environment                  |
| Git and GitHub     | Version control and project documentation    |

*Tool usage may vary across individual exercises.*

## Overall Learning Outcomes

Through this training, I developed an understanding of the digital VLSI implementation flow, from RTL coding and functional verification to synthesis, physical implementation, and timing analysis.

The main learning outcomes include:

* Verilog coding and testbench development.
* Simulation and waveform analysis.
* Logic synthesis and technology mapping.
* Sequential circuits and FSM design.
* Gate-Level Simulation and netlist verification.
* Exposure to SoC design workflows.
* Floorplanning, placement, and clock-tree synthesis.
* CMOS inverter layout and electrical characterization.
* Routing and parasitic-aware timing analysis.
* Setup, hold, and multi-corner timing concepts.
* Linux-based design-tool workflows and technical documentation.

## Conclusion

This repository represents my learning journey through the RTL-to-GDSII VLSI design flow. The exercises helped me understand how functional design, synthesis, standard-cell implementation, physical layout, and timing verification work together in digital integrated-circuit development.

I plan to continue strengthening my skills in RTL design, physical implementation, timing closure, and verification through additional projects and practical exercises.

## Acknowledgments

I acknowledge the training resources, tool documentation, and reference materials that supported my learning. External reports and reference images should be attributed to their original sources where applicable.

## Author

**P.HARSHA VARDHAN REDDY**
**24EG104B20**
Electronics and Communication Engineering
Anurag University

---

