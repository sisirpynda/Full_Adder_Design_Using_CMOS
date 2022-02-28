# Full_Adder_Design_Using_CMOS
This repository presents the Design and Simulation of Full Adder Circuit Implemented using CMOS on Synopsis Custom Compiler in 28 nm technology node

## Table Of Contents :

* Abstract
* Introduction
* Tool Used
* Full Adder Implementation Using CMOS Logic
* Symbol
* Testbench
* Simulation Results
* Transistor Count for each Block
* Netlist
* Author
* Acknowledgements
* References

## Abstract
The conventional Full Adder Circuit consists of 2 blocks one for sun calculation and other for carry calculation, the output of the carry operation is used as an input for the sum block.

## Introduction
The Full Adder Circuit is 3 input circuit which computes the binary addition result of the three inputs, it is sub part of many circuits like Ripple Carry Adders where an array of 
Full Adders is used to compute a n bit value result. Other common circuits that use Full adders are ALU, Multipliers.

## Tool Used


1. Synopsys Custom Compiler:  The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

2. Synopsys Primewave:  PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

3. Synopsys 28nm PDK:  The Synopsys 28nm Process Design Kit(PDK) was used in creation and simulation of the above designed circuit.


## Full Adder Implementation Using CMOS Logic
![full_adder_scematic](https://user-images.githubusercontent.com/50233470/156015228-8f340724-ed3b-4fa4-8cc8-40557113d23e.png)

The Full Adder Circuit is Intended to find the result of binary addition of 3 bits, the output appears as Sum and Carry this can be used to add multi bit numbers(eg. 8 bit adders, etc.) where carry propagates from LSB to MSB as it finds the sum result, the inputs can be given as 2s complement to the adder inn order to compute the subtraction result.

In the image above is the Conventional Full Adder Circuit consisting of 28 MOSFETS, it consists of 2 blocks namely SUM and Carry, to calculate the carry result we need 12 MOSFETS, for calculating sum result we need 16 MOSFETS, one some of whose inputs include carry. We can observe that the sum path is longer than carry path ans is thus delayed. 

### We ca arrive at this Circuit in an intuitive manner:

if we take a look at the ***truth table*** of the full adder circuit 

![image](https://user-images.githubusercontent.com/50233470/156029748-a28d1729-b5c4-40a1-97bb-6181dfa00bfe.png)

We find out that the carry to be 1 atleat 2 inputs are needed which are 1, we can write *Carry = AB +BC +CA* which can again be rewritten as *Carry = AB + C(A + B)* by taking C common, this is what we implement for carry output in our DUT.

we can also see that whenevr the cout is 1 the sum is 0 except for the last case(111), but we cannot tale the cout as determining factor for sum as in case of (000) sum is 0, so we take these 2 cases and arrive at  *Sum = ABC + (A + B + C)Cout* 

These are the 2 equations implemented as 2 sections in the above image connected together in order to obtain the addition outputs.

## Symbol
![full_adder_symbol](https://user-images.githubusercontent.com/50233470/156025682-f8ff6499-9178-4df8-b8ed-952c7367abc1.png)

## Testbench
![full_adder_testbench](https://user-images.githubusercontent.com/50233470/156025725-b473ec37-785f-45b9-af22-2d3b7161b924.png)

## Primewave Window
![test_suite](https://user-images.githubusercontent.com/50233470/156032468-3ebb85c8-820e-449c-b164-7c3f33b34c08.png)

## Simulation Results
![Final_waveform](https://user-images.githubusercontent.com/50233470/156025759-2c3f3d94-7e12-4db6-af58-b36c12927e45.png)

## Transistor Count for each Block
## Netlist
## Author
## Acknowledgements
## References
