![image](images/microchip.jpg) 

## EPC9151 300W 16th Brick Non-Isolated Step Up/Step Down Converter Bi-Directional Average Current Mode Control Firmware
**Bidirectional 2-Phase Synchronous Buck/Boost Converter**

<table style="border:0px dotted white; align:center; width:100%">
<tr>
 <td style="align:center;">
 <td style="text-align:center; vertical-align: bottom; height:230px; width:300px;"> <img src="images/EPC9151-top.png" alt="EPC9151 Top View" width="300"> </td>
 <td style="align:center; width:10px"> &nbsp; </td>
 <td style="text-align:center; vertical-align: bottom; height:230px; width:300px"> <img src="images/EPC9151-bottom.png" alt="EPC9151 Bottom View" width="288"> </td>
 <td style="align:center;">
</tr>
<tr>
 <td style="align:center;">
 <td align=center> <b>Top View</b> </td>
 <td style="align:center;"> &nbsp; </td>
 <td align=center> <b>Bottom View</b></td>
 <td style="align:center;">
</tr>
</table>

## Summary
This code example demonstrates a closed loop Average Current Mode Control implementation for dsPIC33CK. It has specifically been developed for the EPC9151 Rev1.0 1/16 brick converter.

The board supports step-down as well as step-up operation. In step-down mode the conversion direction goes from 48 V to 12 V while in step-up mode the conversion direction from 12 V to 48 V. If not other stated, the 48 V side is named 'input' and the 12 V side is named 'output' in this document.

The board starts up the power converter automatically when power is applied to the board, providing a regulated output voltage. The startup procedure is controlled and executed by the power controller state machine and includes an configurable startup procedure with power-on delay, ramp up period and power good delay before dropping into constant regulation mode.
An additional fault handler routine continuously monitors incoming ADC data and peripheral status bits and shuts down the power supply if the input voltage is outside the defined range (UVLO/OVLO) or if the output voltage is more than 0.5 V out of regulation for more than 10 milliseconds.

A mutli-loop type II (2P2Z) average mode controller is used to balance phase currents in both phases of this interleaved converter. (see details below)

#### Product Features:
  - Input Voltage: 18 V to 61 V (48 V side)
  - Output Voltage: 5 ... 15 V DC (12 V side)
  - Switching Frequency: 500 kHz
  - Control Frequency: 500 kHz
  - Cross-Over Frequency: ~5 kHz 
  - Phase Margin: ~ 60??
  - Gain Margin: ~ 11 dB

## Related Documentation
##### Firmware Documentation
  - EPC9151 Online Firmware Documentation (coming soon)

##### Hardware Documentation
- [EPC9151 300W 1/16th brick Power Module Reference Design Product Website](https://www.microchip.com/DevelopmentTools/ProductDetails/PartNO/EPC9151)
  - [EPC9151 Reference Design Quick Start Guide (QSG)](https://epc-co.com/epc/documents/guides/EPC9151_qsg.pdf)
  - [EPC9151 Reference Design Schematics](https://epc-co.com/epc/documents/schematics/EPC9151_Schematic.pdf)
  - [EPC9531 Test Fixture Quick Start Guide (QSG)](https://epc-co.com/epc/documents/guides/EPC9531_qsg.pdf)
  - [EPC9531 Test Fixture Schematics](https://epc-co.com/epc/documents/schematics/EPC9531_Schematic.pdf)

##### Device Support
*Featured Microchip Technology Products:*
- [dsPIC33CK32MP102 Product Website](https://www.microchip.com/dsPIC33CK32MP102)
  - [dsPIC33CKxxMP10x Device Family Data Sheet](https://www.microchip.com/DS70005363)
  - [dsPIC33CKxxMP10x Device Family Silicon Errata and Data Sheet Clarification](https://www.microchip.com/DS80000809)
- [MCP6C02 Shunt Amplifier Product Website](https://www.microchip.com/MCP6C02)
  - [MCP6C02 Zero-Drift, High-Side Current Sense Amplifier](https://www.microchip.com/DS20006129)

*Featured Efficient Power Conversion (EPC) Products:*
- [EPC2152 70 V, 12.5 A ePower??? Stage](https://epc-co.com/epc/Products/eGaNFETsandICs/EPC2152.aspx)
  - [EPC2152 Data Sheet](https://epc-co.com/epc/documents/datasheets/EPC2152x_datasheet.pdf)

## Development Tools 

##### MPLAB?? X Integrated Development Environment (IDE)
  - [Requires MPLAB?? X IDE, Version v5.40 or later](https://www.microchip.com/mplabx)
    - [Download latest version of MPLAB?? X IDE for Windows](https://www.microchip.com/mplabx-ide-windows-installer)
    - [Download latest version of MPLAB?? X IDE for Linux](https://www.microchip.com/mplabx-ide-linux-installer)
    - [Download latest version of MPLAB?? X IDE for MAC OS](https://www.microchip.com/mplabx-ide-osx-installer)

##### MPLAB?? XC16 C-Compiler
  - [Requires MPLAB?? XC16 Compiler, Version v1.50 or later](https://www.microchip.com/xc16)
    - [Download latest version of MPLAB?? XC16 Compiler for Windows](https://www.microchip.com/mplabxc16windows)
    - [Download latest version of MPLAB?? XC16 Compiler for Linux](https://www.microchip.com/mplabxc16linux)
    - [Download latest version of MPLAB?? XC16 Compiler for MAC OS](https://www.microchip.com/mplabxc16osx)

##### MPLAB?? X PowerSmart??? Digital Control Library Designer
  - [Optional: PowerSmart&trade; - Digital Control Library Designer, v0.9.12.642 or later (Pre-Release Version)](https://areiter128.github.io/DCLD/)
    - [Download latest version of PowerSmart&trade; - DCLD for Windows](https://github.com/areiter128/DCLD/archive/release.zip)

## Hardware Used
The EPC9151 1/16th brick power module is best tested when plugged into EPC9531 test fixture. This test fixture also provides all required interfaces to program and debug the dsPIC33CK32MP102 DSC as well as test points and banana jack connectors for easy and safe handling of the kit during bench tests. The EPC9531 QSG provides detailed operating procedure instructions.

  - EPC9151: EPC9151 16th Brick Non-Isolated Step Down Converter, Revision 1.0
  - EPC9531: EPC9531 test fixture for EPC9151 16th brick reference design

<p>
  <center>
    <img src="images/EPC9531-top.png" alt="EPC9151 mounted on EPC9531 Test Fixture" width="500">
  </center>
</p>

## Setup
The board comes programmed and ready to be used when unpacked. No reprogramming of the target device is required to operate the board unless features or settings such as the nominal output voltage or start-up timing need to be modified. 

<p>
  <center>
    <img src="images/9531_9151_setup.png" alt="EPC9531 Test Fixture Connections - Top View" width="700">
    <br>
    EPC9531 Test Fixture Connections - Top View
  </center>
</p>

<p>
  <center>
    <img src="images/9531_bottom.png" alt="EPC9531 Test Fixture Connections - Bottom View" width="620">
    <br>
    EPC9531 Test Fixture Connections - Bottom View
  </center>
</p>


In case firmware based features need to be changed, the Microchip dsPIC33CK controller can be re-programmed using the in-circuit serial programming port (ICSP) available on the RJ-11 programming interface as well as the 5-pin header provided by the EPC9531 test fixture. These interfaces support all of Microchip???s in-circuit programmers/debuggers, such as MPLAB?? ICD4, MPLAB?? REAL ICE or MPLAB?? PICkit4 and previous derivatives. See [EPC9531 Quick Start Guide](https://epc-co.com/epc/documents/guides/EPC9531_qsg.pdf) for details.


## Operation
The converter is starting up automatically when more than 8.5 V DC are applied across the output terminals resp. 18 V across the input terminals of the EPC9531 test fixture. It is not recommended to operate the EPC9151 reference design without proper decoupling capacitance at either input or output. The EPC9531 test fixture provides the best test environment for the converter. Please read the [EPC9531 Quick Start Guide](https://epc-co.com/epc/documents/guides/EPC9531_qsg.pdf) to get detailed information about the requirements for setup and operation of this reference design.

## Firmware Quick-Start Guide

##### 1) Buck Converter State Machine

The state machine goes through the following steps in chronological order:

a) Initialization

In this step the control loop parameters are reset to their defaults, PWM outputs are turned off but the PWM is still running, continuously triggering the ADC to keep sampling input and output voltage as well as board temperature.

b) Reset
This is the 'fall-back' state from which the buck converter will be restarted once it has been started successfully and has been shut down due to a fault condition (e.g. input under/over voltage or over temperature condition)

c) Standby
After RESET, the state machine waits for all fault flags to be cleared and the enable and GO bits to be set.

d) Power-On Delay (POD)
Once the buck converter has been cleared the state machine will execute the startup procedure starting with the Power On Delay. This is just a simple delay during which the converter will remain inactive but the fault handler will observe the values generated by the ADC for occurring fault conditions.

e) Launch Voltage Ramp
After the Power-On delay has expired, input and output voltage will be measured. In case the converter output is pre-biased (voltage = non-zero), the power controller will be 'pre-charged' with an artificial control history and PWM output to softly ramp up the output voltage from its most recent level. 

f) Voltage Ramp-Up
Now the digital feedback loop and PWM are enabled and the closed loop system reference value is incremented with every execution of the state machine (100 ??sec interval). The control loop has been adjusted to operate with a cross-over frequency of >10 kHz matching the maximum perturbation frequency allowed to keep the control system stable.  

g) Power Good Delay
After the reference voltage has been increased to the pre-defined nominal level, the state machine switches over into the Power Good Delay period. This is another, simple delay where the control loop is in steady state waiting for the delay period to expire.

h) Online
After the Power Good Delay has expired, the converter drops into nominal operation. In this condition it continuously observes the reference value for changes. Should any other part of the firmware change the controller reference, the state machine will softly tune into the new level instead of hard-switching the reference. 

i) Suspend/Error
If the power controller is shut down and reset by external commands (e.g. fault handler detecting a fault condition or through user-interaction), the state machine is switching into the SUSPEND state, which disables the PWM outputs and control loop execution, clears the control histories and resets the state machine back to RESET

##### 2) Cycle-by-Cycle Average Current Mode Control Loop

The bi-directional control system of EPC9151 is based on the conventional Average Current Mode Control (ACMC). An outer voltage loop regulates the output voltage by comparing the most recent feedback value against an internal reference. The deviation is processed by a discrete type II (2P2Z) compensation filter. The output of the voltage loop sets the reference for the two inner current loops. Each phase current controller processes the deviation between the given dynamic current reference and the individual most recent current feedback. Each current control loop output adjusts the individual duty cycle or phase resulting in tightly balanced phase currents. This control scheme is applied to both, 48 V to 12 V downstream buck as well as to 12 V to 48 V upstream boost operation.

When powered from a single DC source from either side of the converter, the output voltage will be kept constant up to the maximum output current of 25 A buck respectively. 5.5 A in boost operation, at which stage the converter switches into the constant current mode, effectively disables the voltage regulation.

This firmware serves as the fundamental building block of battery charger front-end systems by implementing a chemistry-specific charging profile or as balancing converter between two battery powered bus rails.

<p>
  <center>
    <img src="images/2-phase-acmc.png" alt="EPC9151 type II Mutli-Loop Average Current Mode Control Loop" width="800">
    <br>
    EPC9151 Type IV Controller - Advanced Voltage Control Loop
  </center>
</p>

This control loop can be turned on/off by using the ENABLE bit in the STATUS word of the cNPNZ_t controller data structure. The adaptive loop gain modulation is permanently active as soon as the control loop is enabled.

##### 3) Digital Controller Design

The control loop source code is configured and generated by the PowerSmart&trade; - Digital Control Library Designer (DCLD) software.

This additional design software is available for download on Github Pages:

  - [PowerSmart&trade; Digital Control Library Designer Github Page](https://areiter128.github.io/DCLD)

Once installed, the controller configuration can be modified. The most recent configuration can be opened from within the MPLAB X?? IDE by right-clicking on the file 'DPSK3_VMC.dcld' located in the Important Files folder of the Project Manager. When right-clicked, select 'Open In System' to open the configuration in PowerSmart&trade; DCLD. 

Please refer to the user guide of PowerSmart&trade; DCLD which is included in the software and can be opened from the help menu of the application.

##### 1) User Control

No user control interface has been added to the firmware. Any change to the firmware and fundamental operation of the reference design, including reprogramming of the nominal output voltage can be done by editing the hardware-specific values in the hardware description header file 'epc9151_r10_hwdescr.h' located in 'Project Manager => Header Files/Config'

Converter settings in this file are defined as physical values such as Volt, Ampere, Ohm, etc. Each defined value is converted into binary numbers by so-called macros, at compile time. Thus, users do not have to convert values manually.

##### Example:
To program the converter to provide a nominal output voltage different from the 12 V DC set by default, follow these steps:

  - Open the project in MPLAB X?? IDE
  - Navigate to 'Header Files/Config/epc9151_r10_hwdescr.h' using the Project Manager on the left of the main window
  - Go to line #325 (see below)
  - Change the give settings as desired
  - Build the program
  - Remove power from the input of the EPC9531 test fixture
  - Connect a valid ICSP programming device (e.g. MPLAB ICD4, MPLAB PICkit4) to the PC and the EPC9531 test fixture (see [EPC9531 Quick Start Guide](https://epc-co.com/epc/documents/guides/EPC9531_qsg.pdf) for details)
  - Program the device with the target device being powered by the debugger/programmer
  - Disconnect the ICSP programming device from the EPC9531 test fixture
  - Apply valid input voltage across the input terminals of EPC9531 and observe the output of the EPC9151 reference design

The setting for the nominal output voltage is found in lines #324 through #326.

    #define BUCK_VOUT_NOMINAL           (float)12.000  // Nominal output voltage
    #define BUCK_VOUT_TOLERANCE_MAX     (float)0.500   // Output voltage tolerance [+/-]
    #define BUCK_VOUT_TOLERANCE_MIN     (float)0.100   // Output voltage tolerance [+/-]

###### Please note:
The tolerance settings above include the transient response at a maximum load step. The value for maximum output voltage tolerance 'BUCK_VOUT_TOLERANCE_MAX' is observed by the fault handler. Should the output voltage reading divert from the most recent reference voltage value by more than the given range, the converter will be shut down and a REGULATION ERROR will be indicated. The power supply will automatically recover as soon as the fault condition has been cleared and the recover delay period specified by BUCK_REGERR_RECOVERY_DELAY in line #527 of the EPC9151 hardware description header file has expired.

(line numbers given may be subject to change)

##### 5) Power Plant Measurement Support

This code examples includes an alternative, proportional control loop which is commonly used during measurements of the frequency response of the power plant. When the following define is set to TRUE, the common main control loop is replaced by the proportional controller.

    app_power_control.c, line 33:   #define PLANT_MEASUREMENT   false


###### PLEASE NOTE:
PROPORTIONAL CONTROLLERS ARE BY DEFAULT UNSTABLE AND NOT SUITED TO REGULATE THE OUTPUT OF A POWER SUPPLY UNDER NORMAL OPERATING CONDITIONS. DURING A PLANT MEASUREMENT IT IS MANDATORY THAT INPUT VOLTAGE AND LOAD REMAIN STABLE AND DO NOT CHANGE. 

FOR MORE INFORMATION ABOUT HOW TO CONDUCT A POWER PLANT MEASUREMENT, PLEASE READ THE SECTIONS IN THE PowerSmart&trade; DCLD USER GUIDE.


_________________________________________________
(c) 2020, Microchip Technology Inc.

