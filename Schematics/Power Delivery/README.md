# Power Delivery Schematic

The main component for the power delivery system will be the voltage regulator. The one we will be using is the AZ1117IH-3.3TRG1 Voltage Regulator. The following is the circuit diagram for the voltage regulator.

<p align="center">

  <img src="https://github.com/chen4578/Micromouse/blob/428269de9dd53fe1c834034befea06aa6b4b9214/assets/Screenshot%202025-10-12%20195810.png" width="500">

</p>

As seen in the circuit, we also need a 10 and 22 uF capacitor. Specifically, we decided to use a MLCC (multilayer ceramic capacitor) with a package/case of 0603 for compactness and to simplify soldering for both capacitors.

In order to connect the batteries to the PCB and the breakout board, we need two JST connectors. We use B2B-PH-K-S JST connectors because they connect well to the batteries.

Below is the completed schematic:

<p align="center">

  <img src="https://github.com/chen4578/Micromouse/blob/0d55c0cc4b256a2351a45386ed9b3b7f1dc8eed2/assets/Screenshot%202025-10-12%20201238.png" width="500">

</p>

# H-Bridge Schematic

To control the motors, we will use an H-Bridge. For our project, we will be using a L293DD H-Bridge. The integrated has two H-Bridges so that each motor has an H-Bridge. It has 2 input and output pins per motor as well as two enable pins, which take 3.3V to turn on the H-Bridge.

Below is the H-Bridge pinout:

<p align="center">

  <img src="https://github.com/chen4578/Micromouse/blob/a5d60f13ace7b01a16527bdbbfb77dd2d47d164b/assets/image20-bc8fe0a03ac82416e98b3f803fc83a6a.png" width="300">

</p>

The schematic for connecting the H-Bridge is as follows:

<p align="center">

  <img src="https://github.com/chen4578/Micromouse/blob/a749545df172289264b095bd9e55daf5308178a2/assets/Screenshot%202025-10-13%20021959.png" width="700">
