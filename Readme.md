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

