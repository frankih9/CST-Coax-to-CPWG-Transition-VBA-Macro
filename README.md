# CST-Coax-to-CPWG-Transition-VBA-Macro
Hopefully CST will not use VBA/Macro as the basis of its scripting in future releases.

The purpose of this VBA/Macro is to automate the consturction of a multilayer PCB, via placements, and a vertical coaxial connector.  The resulting structure contains parameters which can be used in a swept simulation for connector to CPWG transition optimization.  After the .mcs file is loaded and invoked, a PCB stack up info file is prompted.

## PCB stack up file format  
An example of a PCB stack up file with 6 layers of metal is provided in *6_layer_PCB_stack_info.txt*.  
Each line in the .txt file defines either a metal or dielectric layer.  
The descriptions of the 6 parameters of each line are listed below:
1. Name of layer - Mx and Dx are used for metal and dielectric layers.
2. Thickness
3. Material name - For now, if the 4th parameter or the dielectric constant is 0, PEC is assumed.  
4. Dielectric constant - For metal layers, use 0.
5. Place clearance - If 1, a clearance is created.  Width of clearance is defined by the "TLine_GND_Dist" and "Tline_Width" variables.
6. Place transmission line - If 1, a transmission line is placed.  

Here is the result of *Coplanar WG on Multilayer PCB Study V1.mcs* with  *6_layer_PCB_stack_info.txt* 
<img src="Coplanar WG on Multilayer PCB Study V1.jpg" alt="alt text" >

## Differences between V1 and V2
If a transmission line is in one of the middle layers, the clearance will be filled with resin of the prepreg.  Script files ending with V2 model this resin fill with dielectric constant of the prepreg.  V1 scripts ignore the resin fill.  Which is more correct?

...
