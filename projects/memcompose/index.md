# Introduction
MemCompose was made as part of the final project of CSE 211. This tool is a memory synthesis compiler that automates the memory synthesis for ASIC backend.
Since this project is more hardware oriented a brief background is presented to be able to comprehend what problem is being solved.
# Background
The traditional hardware design flow roughly follows the following diagram:

![background](./images/background.png)

The hardware logic is usually written in a hardware description language named Verilog. This logic modeled in Verilog is generally called Register-Transfer Level (RTL). Like any other software project, once the hardware is modeled it is verified using testbenches to make sure it performs its intended behavior. After verification, the RTL is provided to a synthesizer to transform higher level constructs written in Verilog to actual gates and flip-flops. It is the job of the synthesizer to take a higher abstraction of logic and transform it to low-level Verilog with only gates also known as gate-level netlis. In the above diagram a tool called Yosys is mentioned which is an open-source synthesis tool. The gate-level netlist is then passed on to either FPGA based Electronic Design Automation (EDA) tools or ASIC based EDA tools depending upon the backend target.

Most of the hardware design requires some kind of memories to store certain data. In Verilog memories are generally declared as 2-D register arrays like:

```verilog
reg [15:0] RAM [1023:0];
```
The above syntax indicates a memory with 16 bit word size and 1024 depth. 
