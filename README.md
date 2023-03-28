# Introduction 
This document is a report for the design of a regulated DC power supply that can deliver 2 mA current at 20 V<sub>o</sub>. It is created to be easy to build and customize for your particular project needs. Along with objective of giving a basic knowledge of how a DC regulated power supplies work. 

DC power supply is an essential part of any power 
supply unit used by all electronics devices to convert AC signal into a steady DC signal.This is done with the use of many intertwined components. Obvious examples that can 
be listed are mobile and laptop chargers, TV, . . . etc. The practical devices are mainly manufactured on a PBC inside large factories but 
in in this project, as per the instruction of my instructor a simulated version of the actual 
circuit will be constructed using LTSpice software. 

The working principle of DC supply designed here is first to convert the AC signal 
input to a lower peak voltage to be used by the diode bridge rectifier with step down 
transformer. Then the diode bridge rectifier is used to convert both halves of each wave 
form cycle into pulsating DC signal using four rectification diodes. This signal obviously 
will not generate a stable DC supply and contains large ripple voltages because the 
diode mainly flips the negative part of our signal. It will not regulate it or filter it in any 
way.  

After this to decrease of voltage difference of the ripple signals, we will use a filter 
(a smoothing capacitor) across the bridge rectifier, which with a high level of 
capacitance ripple voltages can be decreased significantly. 
The last part of our design will be a Zener regulator (which is a special type of 
diode that also works in a reverse biased conditions). When the Zener diode is reverse 
biased current through increased dramatically to maximum value, which remains 
constant over a wide range of reverse voltages. 
This is just a recap of the full description. In
 the rest of the document a detailed 
description of component and their type will be discussed. Any mistakes observed on 
this document will be the responsibility of the compiler, and we hope more explanation 
and correction will be given by my instructor.


# Objective
The main objective of this project is to design a regulated DC power supply that can deliver 2mA (IC) at 20V (VCC) to bias an NPN BJT amplifier when a resister load (RC) is connected (Assuming RC is constant). As shown in the figure below. 

 <div align = "middle" >
 <img  width = 50%  src = "images/npn-transistor.png" alt = "NPN BJT Amplifier" title = "NPN BJT Amplifier">
</div>

To get the necessary components in our project use considered the outputs 
indicated in the project’s description, then we worked our way up with calculations. we 
first started with the regulator then the filter, lastly the transformer. All the parts were 
designed in such a way that our output requirements were met.

<br>
<hr>  
Here is a table of the components that were used for the completion of this project. 

<br>
<div align = "middle" >

| Component Type | Name    | Numbers | Value(respectively) |
| -------------- | ----    | ------- | ------------------- |
| Capacitor | C<sub>f</sub>| 1       | 0.302 mF | 
| Inductor | L1, L2        | 2       | 155.9 $\mu$F | 
| Resistor | R<sub>c</sub> | 1       | 733 $\Omega$ | 
| Diode | 1N4148           | 4       | V<sub>forward</sub> = 0.75 V | 
| Zener Diode | BZX384B20  | 1       | V<sub>reverse</sub> = 20 V | 
| Voltage Source | V<sub>input</sub> | 1 | V<sub>rms</sub> = 220 V | 
||
</div>

<br>

# The Regulator

 Voltage regulator are one of the most important and commonly used electrical component in electrical engineering. Voltage regulators are responsible for maintaining a steady voltage across an electronic system. 
 
 Voltage fluctuations may result in undesirable effect on an electronic system, so to maintaining a steady constant voltage 
is necessary according to the voltage requirement of a system. 
         
The working principle of the Zener diode is same as ordinary diode in forward biased conditions but when it counters reverse biased conditions and the reverse voltage reaches the predetermined Zener break down value the diode begins to conduct 
electricity in the reverse region. 

This is very useful to maintain low ripple output with a 
varying load current. The next part of our discussion will be then the calculation of the value that make up the shunt resistance of the regulator. and also, value of the 
capacitor. 

We know that form our given preconditions that current through the load was 2mA and the voltage across the load is 20V so we can conclude that the load resistance has a value of 10kΩ by ohms law. 
If V<sub>zener</sub> = 20 V then V<sub>in</sub> that is set to the Zener diode must be configured in such a way that it’s value to be greater than Zener’s voltage so to find the voltage across the 
Zener diode we will find Thevenin voltage equivalent across the Zener diode’s terminal for a given input and check if our result from the capacitor meets our requirements. Then by voltage division assuming ƨﾨm to be input voltage on the regulator we know that the Thevenin equivalent will be.

<div align = middle>

V<sub>Th</sub> =  $\frac{Rl*Vin}{ Rl + Rs}$

</div>
If V<sub>Th</sub> > 20 V . . . . . .  must be satisfied to turn on the zener diode.