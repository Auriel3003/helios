---
author: Helios
pubDatetime: 2023-05-07T15:57:52.737Z
title: Transistor Transistor Logic
postSlug: ttl-logic
featured: false
ogImage: https://user-images.githubusercontent.com/53733092/215771435-25408246-2309-4f8b-a781-1f3d93bdf0ec.png
tags:
  - CASE-STUDY
description: nothing and everything 
---

## Transistor-transistor logic(TTL)

Transistor-transistor logic(TTL) is a class of digital circuits built from bipolar junction transistors (BJT) and resistors. It is called transistor–transistor logic because of its dependence on transistors alone to perform basic logic operations. It is the most popular logic family and it is also the most widely used digital IC family.

There are various subfamilies in transistor-transistor logic, which includes standard TTL, Low power TTL, Schottky TTL, Advanced Schottky TTL, High power TTL, fast TTL. etc.

## Performance Characteristics of a TTL

The transistor-transistor logic (TTL) type integrated circuits offer excellent performance due to the following characteristics:

- Their speed is very high
- It has a low price
- Their Fan-in and fan — out is quite good
- Their interfacing with other digital circuits is quite easy
- Their noise margin is high

## TTL With Nand Gate

![image](https://user-images.githubusercontent.com/103866475/236673272-0264bc14-f9e2-4a05-82e5-c0ee363b896f.png)

![image](https://user-images.githubusercontent.com/103866475/236673278-36ac307b-d509-4ef3-8300-e993109a9b70.png)


### When Both Inputs Are High -

If both inputs A and B are high (logic 1), the emitter–base (E/B) junction of Q1 transistor becomes reverse biased, due to which no emitter current passes through the emitter. Thus, in such a situation, Q1 turns OFF. However, its collector–base (C/B) junction is forward-biased, due to which transistor’s base Q2 receives base current via R1 from +VCC. As a result, transistor Q2, fully turns ON (i.e. Q2 gets saturated). When Q2 is ON, zero voltage are received on point N. Therefore, in case both inputs are high, a low output is received (i.e. output logic is at zero) .

### When Both Inputs or Either Input is low -

When both or any one of the two inputs is low (i.e. it is at logic zero), the associated emitter–base (E / B) junction (or the junction with low input) becomes forward-biased. Thus, transistor Q1 turns fully ON. thet value of R1 is selected in such a manner that Q1 could fully get ON). In case Q1 is saturated or ON, the voltage at point M becomes zero. Resultantly, the base current of transistor Q2 also becomes zero. As a result of the zero-base current of Q2, this transistor turns OFF. Thus, high voltage equal to +VCC on point N are received. In other words, high output results on point N (that’s output is at logic 1).

    TTL NAND Gate with Totem Pole Output:
 
 ![image](https://user-images.githubusercontent.com/103866475/236673304-f594be43-3425-466c-b35f-091bb16a5e61.png)
    

In the circuit, the input transistor Q1 is a multiple-emitter transistor, and transistor Q2 is a phase splitter. Transistor Q3 sits above Q4 and therefore Q3 and Q4 make a totem pole arrangement.

Diode D1 and D2 protect Q1 from damage by the negative spikes of voltages at the input. when negative spikes appears at input terminals, the diode conduct and bypass the spikes to the ground, and Diode D ensures that Q3 and Q4 do not conduct simultaneously. Transistor Q3 act as an emitter follower.

1. When the both A and B inputs are HIGH(5v),both the base emitter junctions of Q1 are reverse biased. So no current flows through the emitter of Q1.However base collector junction of Q1 is forward biased so current flows through R1 to the base of Q2 and Q2 turns on. Current from Q2 flows into the base of Q4 through emitter so Q4 turn on. The collector current flows through R2 and so produces drop across it thereby reducing voltage at collector of Q2. Therefore Q3 is off. Since Q4 is on ,Y(output) is as its low level VCE(sat). so output is logic 0(LOW).
2. When either A or B or both are LOW, BE junction of Q1 is forward biased and BC junction is reverse biased so current flows to the ground through the emitters of Q1, therefore, base is at 0.7V. which cannot forward biases the BE junction of Q2 so Q2 is off. So with Q2 off Q4 does not get base current so Q4 will be off. Transistor Q3 gets enough base drive because Q2 is off and therefore Q3 is on. So output voltage is which is logic 1(HIGH).

### Advantages of totem pole output:

1. Even though circuit can work with removing of Q3 and D and R4 connected to the collector of Q4,so there is no current through R4 in the output LOW state. So the inclusion of Q3 and D keeps the circuit power dissipation low.
2. In the output HIGH state,Q3 acts as a emitter follower with its associated low output impedance. This low output impedance provides a small time constant for charging up any capacitive load on the output. This action is referred as active pull up and provides very fast rise time waveforms at TTL output.

### Disadvantages of Totem pole:

1. During transition of output from LOW to HIGH,Q4 turns off more slowly than Q3 turns on and so there is a period of few nanoseconds during which both Q3 and Q4 are conducting and therefore relatively large currents will be drawn from the supply so TTL circuits suffer from internally generated currents spikes because of totem pole connection.

    
## TTL NOR & OR Gate

![image](https://user-images.githubusercontent.com/103866475/236673365-2b795d57-6049-4941-80c0-8f652ce4b272.png)


Transistors Q1 and Q2 are both arranged in the same manner that we’ve seen for transistor Q1 in all the other TTL circuits. Rather than functioning as amplifiers, Q1 and Q2 are both being used as two-diode “steering” networks. We may replace Q1 and Q2 with diode sets to help illustrate:

## TTL NOR and OR gates — 1

If input A is left floating (or connected to Vcc), current will go through the base of transistor Q3, saturating it. If input A is grounded, that current is diverted away from Q3‘s base through the left steering diode of “Q1,” thus forcing Q3 into cutoff. The same can be said for input B and transistor Q4: the logic level of input B determines Q4‘s conduction: either saturated or cutoff.

Notice how transistors Q3 and Q4 are paralleled at their collector and emitter terminals. In essence, these two transistors are acting as paralleled switches, allowing current through resistors R3 and R4 according to the logic levels of inputs A and B.

If any input is at a “high” (1) level, then at least one of the two transistors (Q3 and/or Q4) will be saturated, allowing current through resistors R3 and R4, and turning on the final output transistor Q5 for a “low” (0) logic level output. The only way the output of this circuit can ever assume a “high” (1) state is if both Q3 and Q4 are cut off, which means both inputs would have to be grounded, or “low” (0).

![image](https://user-images.githubusercontent.com/103866475/236673387-2e9fadb3-5bff-40fe-847f-12b7fc59cb4d.png)


n order to turn this NOR gate circuit into an OR gate, we would have to invert the output logic level with another transistor stage, just like we did with the NAND-to-AND gate example:

![image](https://user-images.githubusercontent.com/103866475/236673394-6fd55a7b-3166-4a43-bada-3c6d0e5f1269.png)


The truth table and equivalent gate circuit (an inverted-output NOR gate) are shown here:

![image](https://user-images.githubusercontent.com/103866475/236673398-38118edb-ed44-4dc1-a620-15f1126f083e.png)

Advantages:

    Power dissipation is less compared to DTL and RTL
    Less expensive
    Noise Margin and Fan out are better

Disadvantages:

    It cannot be used in high performance processors
    It is not used in high end electronic devices.

Applications:

    TTL or Transistor-Transistor Logic is used in Mini Computer Processors.
    TTL is used Controller circuits, Display Driver Circuits.
    TTL is used in low-end programming devices such as remote controls, light controllers.
    TTL method is used in the microprocessor and microcontroller also.
    Smaller and low power electronic devices use TTL logic method
