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

## INTRODUCTION –

In recent times there has been tremendous growth in the number of mobile computing and embedded platforms. Devices such as laptop computers, mobile phones, camcorders, and PDAs have become very common and popular. Unfortunately, there lies a fundamental trade-off between performance and energy consumption in these devices. In order to handle more complex tasks they need more powerful microprocessors which in turn demand more energy and drastically reduce battery life. Of late a lot of effort has been made into Dynamic Voltage Scaling (DVS) to find a solution to the trade-off problem. It is also known as low — power circuit design technique. DVS addresses this problem by taking into account that most processors use CMOS technology which implies:

- They consume energy only during switching from one state to another.

- This switching energy is proportional to the square of the voltage applied whereas the maximum operating frequency is directly proportional to the voltage applied.

In simple words “The DVS scheme reduces the supply voltage dynamically to the lowest possible state where proper operation is still possible but the required performance of the system, device, sensor, or what have you is lower than the maximum possible performance.”

The speed of a circuit depends linearly on the supply voltage. The idea in dynamic voltage scaling is that during times when the circuit is not needing high performance, both its clock frequency and the supply voltage can be scaled down. Because dynamic power dissipation depends on the square of the supply voltage and linearly on the frequency , if both the supply voltage and frequency are scaled down, there is a cubic reduction in power consumption.

## Dynamic Voltage and Frequency Scaling

Dynamic voltage and frequency scaling (DVFS) is a technique that aims at reducing dynamic power consumption by dynamically adjusting the voltage and frequency of a CPU. This technique exploits the fact that CPUs have discrete frequency and voltage settings as previously described. These frequency/voltage settings depend on the CPU and it is common to have ten or fewer clock frequencies available as operating points. Changing the CPU to a frequency-voltage pair (also known as a CPU frequency/voltage state) is accomplished by sequentially stepping up or down through each adjacent pair. It is not common to allow a processor to make transitions between any two nonadjacent frequency/voltage pairs.

Where Is DVS Used?

* DVS is typically used in battery-operated devices where power savings and battery run times are paramount.
* DVS is also used in large systems with multiple processors/DSPs where power savings is required for thermal reasons.
* DVS is implemented extensively in:

– Cell phones
– PDAs
– MP3 players
– Microcontroller-based battery-operated devices

### How DVS works?

How a dynamic voltage-scaling scheme works. On the basis of the workload, the system requests a frequency change. First, the frequency is reduced, which takes on the order of hundreds of picoseconds, and then the voltage is ramped down, which takes on the order of hundreds of microseconds. Later, when switching back to high frequency, the voltage is first scaled back up to the normal voltage level, and then the frequency is raised back up.

### Application-

Dynamic voltage scaling has been implemented in several commercial embedded microprocessors including the Transmeta Crusoe [Transmeta 2002], Intel Xscale [Intel 2003], and ARM IEM [ARM 2007]. When the processor is lightly loaded, the frequency and supply voltage is scaled down to save power, and when it is heavily executed, it is run at full frequency and voltage.

Some other applications, TPS65023x Power Management IC it has also DVS feature.

### Conclusion -

Dynamic voltage scaling is a highly efficient way of reducing power consumption while still preserving functionality and meeting user expectations. It has been widely deployed.
