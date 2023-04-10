---
title: The Ideal Gas Law
description: Exploring the ideal gas law
slug: ideal-gas-law
date: 2022-01-06
image: 
categories: []
links:
  - title: "Ideal gas law: Wikipedia"
    website: https://en.wikipedia.org/wiki/Ideal_gas_law
  - title: "Equation of State: NASA"
    website: https://www.grc.nasa.gov/www/k-12/airplane/eqstat.html
  - title: "Absolute Temperature: Wikipedia"
    website: https://simple.wikipedia.org/wiki/Absolute_temperature
tags:
    - Physics
    - Thermodynamics
    - Rockets
---

This article is part of a series on compressible flow. The goal of the series is that anyone with an interest can go from just a basic understanding of algebra, everyday physics and a bit of calculus to understanding how internal compressible flow works, with the goal of being able to analyze and design rocket nozzles and supersonic wind tunnels. I’m writing the series as I learn about these things myself so please correct me if I make any mistakes. I will leave the resources I used and further reading at the bottom of each article.

To understand this article, you will need at least a basic understanding of the following concepts:

- Amount of substance (moles)
- Basic algebra (equations)
- Energy
- Pressure
- Volume

## Relating quantities

When working with gases, there is one relationship that is essential to know, that is, the ideal gas law.
The ideal gas law relates the volume, pressure, temperature and amount of gas with each other and can be written as an equation like this:

$$
PV=nRT
$$

Where \
$P$ is the pressure in the system. \
$V$ is the volume of the system. \
$n$ is the amount of gas. \
$R$ is the universal gas constant. \
$T$ is the absolute temperature of the gas.

According this law, the product of the pressure and volume of a gas depends on the amount of gas and the temperature of the gas. To get a feel for what this means, let’s try playing with the quantities a bit.

### Example 1

Say we have a cylinder of gas which we heat up. The temperature rises. The cylinder is closed, so the volume cannot increase and the amount of gas stays constant. What happens? Take a look at the equation and try to figure it out before continuing.

The answer is: the pressure rises!

Adding heat caused the molecules in the gas to go faster, thereby hitting the walls of the container harder which means the pressure is larger. We will look closer at this and what the meaning of $R$ is, when we look at the Kinetic Theory of Gases in a later article.

### Example 2

Let’s try another example.
We have a cylinder of gas with a piston in one end which we draw out, increasing the volume. Doing this will actually cool the gas, so to keep the temperature constant we wait for it to warm up again. We will take a look at why doing this cools the gas in a later article on Adiabatic Processes. For now we have a gas with a larger volume, but the same amount of gas and the same temperature. What happens to the gas?

Answer: the pressure decreases!
We have the same amount of gas with the same temperature (which means that the molecules are moving at the same speed), but the volume is bigger. This means that the molecules pump into stuff less often, as there is more free space, and the pressure is lower.

### Example 3

Okay, one last example.
We now have two cylinders. They both have the same volume and temperature, but the pressure in one is lower. What else would be different between them?

Answer: the one with the lower pressure also has a lower amount of gas!
If the pressure is lower but everything else is the same, it must mean that there are fewer molecules such collisions occur less frequently, causing the lower pressure.

## A practical example and absolute temperature

Now let’s see a more practical example with some actual numbers. We will work out how much volume a mole of gas takes up at the standard atmospheric pressure of $101325 Pa$ and $20^\circ C$. We first solve the equation for $V$:

$$
V=\frac{nRT}{P}
$$

Then plug the values in:

$$
V=\frac{1mol \cdot 8.3145 \frac{J}{mol \cdot K} \cdot T}{101325 Pa}
$$

Now we left the temperature for a reason. Back in the day, our temperature scales were defined more or less arbitrarily. Famously, Celsius has 0 and 100 at the freezing and boiling point of water. But even when water is frozen, the molecules are still jiggling about with thermal energy. As we learned earlier, temperature has to do with how much energy the molecules have, so it would make sense to make a scale where 0 temperature means 0 energy and doubling the temperature means doubling the energy. That is what absolute temperature is.

The “Celsius equivalent” in absolute temperature is Kelvin (Fahrenheit has its own one called Rankine). The size of one degree Celsius is the same as one degree Kelvin, but their zero-points are shifted. 0 Kelvin is equivalent to -273.15 Celsius (Fahrenheit and Rankine act the same way, but 0 Rankine is -459.7 Fahrenheit).

We need our $20^\circ C$ in Kelvin, so we add 273.15:

$$
T=(20+273.15)K = 293.15K
$$

Now we can complete the equation and calculate the volume:

$$
V=\frac{1mol \cdot 8.3145 \frac{J}{mol \cdot K} \cdot 293.15 K}{101325 Pa} = 24.055L
$$

1 mole of gas at $ 20^\circ C $ and atmospheric pressure is going to take up 24 liters of volume. Quite a lot.

Please play around with the equation yourself and try to do some thought experiments (or “gedankenexperiment” as Einstein would say). Try to solve for different quantities and see what you get. What happens when you change different things? Also try to do some more worked examples yourself. The only way to really learn something is to use it a lot.

## Other forms of the equation

Now sometimes you might want to look at a single point in a flow of gas which doesn’t exactly have a volume, so you need the molar concentration of the gas, the density or the specific volume. Maybe you are more interested in how much mass you have, instead of amount? By doing a little algebra and substituting quantities, some other useful forms of the ideal gas law can be derived:

### Molar concentration

$$
c=\frac{P}{RT}
$$

### Mass instead of amount of substance

$$
PV=\frac{mRT}{M}
$$

$R$ and $M$ are often combined to be the specific gas constant which is $R_{specific} = \frac{R}{M}$. This specific gas constant of course changes depending on the gas. This simplifies the above equation to:

$$
PV=mR_{specific} \cdot T
$$

### Density

$$
P = \rho \cdot R_{specific} \cdot T
$$

### Specific volume

You might sometimes see a lowercase $v$. This isn’t because someone forgot that volume needs to be uppercase, but another quantity called specific volume which is the inverse of density:

$$
v = \frac{1}{\rho} = \frac{V}{m}
$$

Names of quantities with a “specific” prefix mean that it is per unit mass and their symbols are usually lowercase versions of their non-specific counterparts. Other examples include specific heat capacity, specific impulse and specific energy. The specific gas constant is an exception though. Anyways, this specific volume lets us write yet another form of the equation:

$$
Pv=R_{specific}T
$$

## One last note

In some contexts the universal gas constant is written as $\bar{R}$ instead, so the specific gas constant can be written as just $R$. Remember to not get caught up in the symbols, and read the text next to the equations as well!

Pressure might also be written as a lowercase $p$. This doesn’t mean that it’s “specific pressure” though, and it shouldn’t be confused with $\rho$ (density) either.

I know this is a lot of information, and you don’t need to know every single equation here by heart. The most important thing is that you know they exist and have a feeling for what they mean, then you can always reference back to here. Though it’s a good idea to remember the normal form of the Ideal Gas Law: $PV = nRT$.

## What’s next?

If you understood everything, you can move on to the next article on the first law of thermodynamics. If not, I suggest you take a break and think about what you read for a day or two, then come back and read the article again. That usually works for me. You can also continue with the series and come back later, you often learn a thing or two more when going back to the basics after having learned some more advanced topics.

## Further reading

See the links below
