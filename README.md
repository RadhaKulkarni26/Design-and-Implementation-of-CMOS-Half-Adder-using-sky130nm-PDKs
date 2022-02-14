# DESIGN AND IMPLEMENTATION OF HALF ADDER USING CMOS AND SKY130nm PDK

- The purpose of this project is to design a CMOS Half ADDER using an Opensource EDA Tool called **eSim**, an Opensource Spice Simulator called **ngspice** and **Sky130 PDK**.
- To explore the project, you can git clone using the command: git clone https://github.com/RadhaKulkarni26/Design-and-Implementation-of-CMOS-Half-Adder-using-sky130nm-PDKs.git
## Table of Contents:

1. INTRODUCTION
2. INSTALLATION OF TOOLS
3. CIRCUIT DESIGN
   1. REFERENCE CIRCUIT DIAGRAM
   2. REFERENCE CIRCUIT WAVEFORM
5. IMPLEMENTATION
6. REFERENCE

### 1. INTRODUCTION
***
In this project, I am going to Design and Implement **Half ADDER** using **CMOS** Technology and I will also implement it using sky130nm technology. Design and Implementation will be done using esim and ngspice software. HALF Adder is the digital circuit which will add 2 inputs and give 2 outputs. 2 inputs are A, B and outputs are SUM, CARRY. Half Adder will do binary addition of A and B and will give the sum of 2 inputs at SUM output and carry bit at CARRY output.We can verify the output using Circuit Waveforms. This complete design and implementation is done using VLSI technology which has features such as high speed, low power, low cost, and small size.

### 2. INSTALLATION OF TOOLS
***
#### esim:
esim is an open-source EDA tool used for circuit design and simulation. Using esim we can draw circuit using Kicad, generate netlist and simulate using Ngspice.

For more information: <https://esim.fossee.in/home>

#### Ngspice:

ngspice is the open-source spice simulator for electric and electronic circuits. We can design circuits using JFET, MOSFET and passive elements like resistors, capacitors, etc.

For more information: <http://ngspice.sourceforge.net>

#### Sky130nm PDK:

The SkyWater Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open source Process Design Kit and related resources, which can be used to create manufacturable designs at SkyWater’s facility. 

For more information: <https://www.layouteditor.org/schematiceditor/libraries/skywater>

The Download links for above software are:

#### esim: <https://esim.fossee.in/downloads>

#### Ngspice: <https://sourceforge.net/projects/ngspice/files/>

#### Sky130 pdk: <https://static.fossee.in/esim/installation-files/sky130_fd_pr.zip>

Follow these steps for Sky130 download and implementaion:

1. Download sky130 from this link mentioned above and unzip it.
1. Save the .cir.out file in the sky\_fd\_pr folder as .cir file.
1. Open with notepad and add the path .lib "models/sky130.lib.spice" tt at the top.
1. Replace with CMOSP, mos\_p with sky130\_fd\_pr\_pfet\_01v8 and CMOSN, mos\_n with  sky130\_fd\_pr\_nfet\_01v8.
1. To replace inductor, capacitor, resistor do it this way, for Ex: L1 out gnd 1m by x1 out gnd mid 0 sky130\_fd\_pr\_\_ind\_03\_90.

**Note**: For more details go to the cells folder in sky\_fd\_pr. 

Open the specific component folder which you want to use. 

Then open the test folder and check the SPICE file. 

The SPICE file is an example of implementation of that component. 

You will get to know how to use the component in your ckt.

6. Now Run the circuit with ngspice.

To Run the ckt using ngspice:

1. Right click on .cir file.
1. Click on Open With.
1. Browse for the ngspice.
1. If ngspice not present scroll down click on More Apps.
1. Go to the FOSSEE folder search for Ngspice and Run it.

### 3. CIRCUIT DESIGN
***
**Half Adder** is a digital circuit which will add 2 binary inputs and will give 2 outputs namely SUM and CARRY. The 2 inputs are **A**, **B** and outputs are **SUM** and **CARRY**. As we have 2 inputs we will have 4 input combinations.Using circuit design rules of CMOS we will design the circuit in such a way that addition of 2 inputs will occur at SUM output and carry bit will occur at CARRY output. While designing we have used total 16 Transistors. Half Adder using CMOS will be designed using 2 parts: PMOS (pull-up lattice) and NMOS (pull-down lattice). PMOS circuit is connected to supply voltage VDD and NMOS circuit is connected to ground GND. We will implement this circuit design using sky130nm technology. In the Circuit Waveform, we will verify the above implementation using clock pulse. In the output we will give different input combinations through clock pulse and verify the logic using output waveform.  

#### 3.1 REFERENCE CIRCUIT DIAGRAM
 ![Reference Circuit Diagram](https://user-images.githubusercontent.com/70748543/153883732-332c147a-7019-4109-8533-df8d4e1d3905.jpeg)


#### 3.2 REFERENCE CIRCUIT WAVEFORM
 ![Reference Circuit Waveform](https://user-images.githubusercontent.com/70748543/153886608-08acf62a-1a73-4bf5-9713-23b78c1bef4b.JPG)


### 4. IMPLEMENTATION
***
Now, we will design the complete circuit using our reference circuit diagram with PMOS logic above and NMOS logic below.
After connecting the complete we will get a circuit like below:
![Final Circuit Diagram](https://user-images.githubusercontent.com/70748543/153883926-3046cf96-059b-43c1-9142-ceb11487ad62.JPG)


Label each and every component and port and check electrical rule checking and generate netlist file using spice and make changes in netlist to add sky130 models.
**The netlist generated initially is as shown below:**

* C:\SPB_Data\eSim-Workspace\Half_Adder\abc.cir

* EESchema Netlist Version 1.1 (Spice format) creation date: 2/14/2022 7:54:22 PM

* To exclude a component from the Spice Netlist add [Spice_Netlist_Enabled] user FIELD set to: N

* To reorder the component spice node sequence add [Spice_Node_Sequence] user FIELD and define sequence: 2,1,0

* Sheet Name: /

M7  Net-_M10-Pad3_ /A /VDD /VDD mosfet_p		

M9  Net-_M10-Pad3_ /B /VDD /VDD mosfet_p		

M8  /SUM /A0 Net-_M10-Pad3_ /VDD mosfet_p		

M10  /SUM /B0 Net-_M10-Pad3_ /VDD mosfet_p		

M5  /SUM /A Net-_M5-Pad3_ GND mosfet_n		

M11  /SUM /A0 Net-_M11-Pad3_ GND mosfet_n		

M12  Net-_M11-Pad3_ /B0 GND GND mosfet_n		

M6  Net-_M5-Pad3_ /B GND GND mosfet_n		

M13  /CARRY /A0 GND GND mosfet_n		

M16  /CARRY /B0 GND GND mosfet_n		

M14  Net-_M14-Pad1_ /A0 /VDD /VDD mosfet_p		

M15  /CARRY /B0 Net-_M14-Pad1_ /VDD mosfet_p		

M3  /A0 /A /VDD /VDD mosfet_p		

M1  /A0 /A GND GND mosfet_n		

M4  /VDD /B /B0 /VDD mosfet_p		

M2  /B0 /B GND GND mosfet_n		

U1  /A /B /VDD /SUM /CARRY PORT		

.end


**The netlist after making sky130 models syntax changes is as shown below:**

* c:\spb_data\esim-workspace\half_adder\half_adder.cir

.lib "sky130_fd_pr/models/sky130.lib.spice" tt

xm7  net-_m10-pad3_ a vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm9  net-_m10-pad3_ b vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm8  sum a0 net-_m10-pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm10  sum b0 net-_m10-pad3_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm5  sum a net-_m5-pad3_ gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm11  sum a0 net-_m11-pad3_ gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm12  net-_m11-pad3_ b0 gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm6  net-_m5-pad3_ b gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm13  carry a0 gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm16  carry b0 gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm14  net-_m14-pad1_ a0 vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm15  carry b0 net-_m14-pad1_ vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm3  a0 a vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm1  a0 a gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

xm4  vdd b b0 vdd sky130_fd_pr__pfet_01v8 w=1 l=0.5

xm2  b0 b gnd gnd sky130_fd_pr__nfet_01v8 w=0.42 l=0.5

Vdd vdd 0 3.3

Vd0 a 0 pulse(0 2.2 0us 0s 0s 20us 40us)

Vd1 b 0 pulse(0 2.2 0us 0s 0s 10us 20us)

* u1  /a /b /vdd /sum /carry port

.tran 0.1us 60us

* Control Statements 

.control

run

plot V(carry) V(sum) +4 V(b) +12 V(a)+15

print allv > plot_data_v.txt

print alli > plot_data_i.txt

.endc

.end

**Note**: sky130\_fr\_pd file for sky130 model must be present on the same file as .cir.out.

**Truth Table for Half Adder using CMOS is as shown below**:

![Truth Table](https://user-images.githubusercontent.com/70748543/153886707-ab1249d5-ac5e-475d-be08-cfd1366ec252.JPG)


Now, run the .cir.out file using ngspice and we will get the circuit waveforms as follows:
![Final Output Waveform](https://user-images.githubusercontent.com/70748543/153884038-fc11fac5-5e4d-4029-b5dd-af98603ad6ae.JPG)

From the above waveform we can verify the truth table for Half Adder using CMOS. 

### 5. REFERENCES:
***
[1]N. Zhuang and H. Wu, "A new design of the CMOS full adder," IEEE Journal of Solid-State Circuits, vol. 27, No. 5, pp. 840-844, May 1992.

[2]N. H. E. Weste and K. Eshraghian, "Principles of CMOS VLSI design," Addison Wesley, 1993.
