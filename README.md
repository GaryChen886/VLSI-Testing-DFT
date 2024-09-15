# VLSI Testing Assignments


## Assignment 0:

### Assignment Description:

(100 pts) Get yourself familiar with the data structure of the PODEM test generation package (though we do not use the test generation part yet). Please use the circuit parser to read benchmark circuits and then output the following attributes of a circuit. Choose benchmark circuits according to different criteria, including combinational, sequential, optimized, and non-optimized, larger or small circuits, etc.

#### Attributes to Output:
- Number of inputs
- Number of outputs
- Total number of gates, including inverter, OR, NOR, AND, NAND
- Number of gates for each type
- Number of flip-flops (if available)
- Total number of signal nets:
  - A net is any wire connecting between (PI, PPI, gate outputs) to (PO, PPO, and gate inputs). Note that a gate connecting to different gates will be counted as different nets.
  - For example, if the output of gate A branches out to gates C and D, then there are two branch nets: A->C and A->D, and one stem net A, adding up to three nets in total.
- Number of branch nets
- Number of stem nets
- Average number of fanouts of each gate (all types)

#### Attention:
The required command format is as follows (so you are required to enroll a new option in `main.cc`) :
#### Example:
`./atpg -ass0 [circuit_name]`


---

## Assignment 1:

### Assignment Description:

(100 pts) Given a benchmark, one primary input (PI) and a primary output (PO), please list and count all possible paths connecting the given PI and PO.

The test circuit will only be combinational circuits, so there's no Flip-Flop (DFF) nor loop in the circuit. A path is a list of connected gates, and all listed paths have the same PI and PO gates.

#### Grading:
- Correctness: 60%
- Performance: 30%
- Report: 10%

#### Attention:
The required command format is as follows:
`./atpg -path -start [PI] -end [PO] [circuit_name]`

### Example:
#### Input:
`./atpg -path -start G3 -end PO_G16 c17.bench`
#### Output:
G3 net17 G16 PO_G16
G3 net14 net18 G16 PO_G16
The paths from G3 to PO_G16: 2

