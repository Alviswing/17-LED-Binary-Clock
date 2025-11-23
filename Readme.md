# Presentation

Here is a quick overview of the design of my binary clock.

I wanted to create a minimalistic clock and learn to plan a electronic circuit by making this project andto avoid as much as possible printed circuit chip and staying as close as possible to transistors and other basic component.

However due to reduce the overall size and to simplify the overall design I decided to partition the Blueprints in sub-modules.

This repository aim to present the different modules of my clock alongside explanations. Let's dive into it !


## The power supply :

For this project to be as simple as possible, I looked first at simplifying the power source using AA-Batteries.

They offer many properties that makes it easier to work with compared to other generators :

#### They produce DC current :
I find it easier to work with DC current, lacking an oscilloscope, I cannot see the signal from AC power source at will. I wanted to avoid as much as possible making filters and other contraptions to rectify the electric signal.

#### They emit a known voltage :
AA-Bateries produce a simple 1.5V of electric voltage per cell. Therefore it simplify the addition of the voltage of each power cell to get an appropriated voltage for my contraption.

#### They are inexpensive :
I wanted to avoid making a clock too costly and I wanted to keep the cost down as much as possible when designing the project.


## Turning a DC Current to a 1 Hz signal :
Looking into oscilating circuit I learned about the **Astable Multivibrator** :

<img width="250" height="202" alt="image" src="https://github.com/user-attachments/assets/e2e561e5-8b96-4d36-bc93-a16649e9ba5b" />

This circuit oscilate beween 2 state. It produce a square signal oscilating between high and low voltage.

The frequence of this circuit is given by the following Equation : 

$$
f = \frac{1}{(R_2C_1 + R_3C_2)*ln(2)}
$$

All resistors and capacitors in the clock are the same so the equation can be rewritten as such :

$$
f = \frac{1}{2RC * ln(2)} = 1Hz
$$

Then to obtain the component specifications I just need to balance the equation. Nothing too hard when you can choose yourself the variables !

Here I chose the capacitor : **C = 10 nF**

Now to solve for R :

$$
R = \frac{1}{2C * ln(2)} = 72 135 k \Omega
$$

Of course such a resistor doesn't exist but since resistor can add up if wired in series so therefore any combination of resistor adding up to such a value is good to go !

## A quick word on logic gates :
In this project I chose to use logic gates as I am working on 6 bit adder and having to draw each transistor in a single adder for each "XOR" and each "AND" and each "NOT" gates was unsustainable, added lots of unnecessary complexity, and would have been fastly unreadable.

I plan to add another repository explaining logic gates as a whole giving example and others logic table eventually somewhere around here. Maybe even see to fork the repository of someone else but else I won't get much more into details.

Just know I deemed it unfeasable to work with all the individual transistor and keep the project readable so I chose to limit myself to working with Logic gates instead of individual transistors.

## A six bit adder ?
I know 6 bits may seems a little short compared to the 17 LED of the whole clock however the logic really isn't far fetched.

[Add here the 6 bit adder]

Yes it is simply 6 basic half adder. No need to add unnecessary complexity where it isn't needed :)

The Idea is that every clock cycle it emit a signal. The clock signal each time is interpretted as a "+1". A system relying on flip flop prevent the adder to forget the count and another logic gate system wait for the adder to reach 60 before reseting the adder.

I chose 6 bit as it is the smallest number of byte capable to reach 60.

I am using it to count both seconds and minutes !

To count hours since we only need to go up to 12 hours I'll use a smaller 4 bit adder :

[Add here the 4 bit adder]

Please note a 5 bit adder would have been around the same however I chose to stop counting at 12 hours and use a AM/PM LED and not 24 hours.
