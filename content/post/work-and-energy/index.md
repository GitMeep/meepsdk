---
title: Work and energy
description: What is energy? How does it work?
slug: work-and-energy
date: 2022-01-04
image: 
categories: []
links:
  - title: "Energy: Wikipedia"
    website: https://en.wikipedia.org/wiki/Energy
  - title: "Work: Wikipedia"
    website: https://en.wikipedia.org/wiki/Work_(physics)
tags:
    - Physics
    - Fundamentals
---

To understand this article, you will need at least a basic understanding of the following concepts:

- Force
- Vectors
- Gravity

## Throwing tennis balls

Imagine a tennis court in outer space. You and your friend are standing at opposite ends of the court (with magnetic shoes or something… don’t think too much about it). You have a tennis ball in your hand, you don’t have any rackets for some reason, so you throw it directly towards your friend. The court doesn’t have a net either, so the ball just flies in a straight line. Your friend stretches out their arm and catches the ball. You threw the ball with such speed that it pushes your friends hand backwards a fair distance!

Your friend complains about how hard you threw and returns the ball. After apologizing, you throw it again, but not as hard this time. Your friend catches the ball and stops it with the same force as before, but this time their hand doesn’t move as far.

You have probably heard about energy before, but for many it is a very abstract concept. The purpose of this somewhat bizarre story is to give some background to why energy is useful and what it actually means.

We’ll get to energy in just a second, but first we define something called work. Work is force times displacement, as expressed in this equation:

$$
W = \vec{F} \cdot \vec{s}
$$

Work is something done on things. When pushing something with a certain force over a certain distance, you do a certain amount of work on it. The harder you have to push (larger force) and the further you have to push (larger displacement), the larger the work you do is. You could imagine pushing a large drawer over the floor vs sliding a plate over a table.

This equation is actually a dot product between two vectors. This means that the work only depends on the force along the displacement. For example: you are pulling a train along its tracks with a rope, but you are walking beside the tracks to not get run over if the train starts going downhill. The force you exert on the train through the rope is therefore not entirely in the direction that the train is moving. The component of the force in the sideways direction won’t contribute to the work.
This can also be expressed with the magnitudes of the forces and the angle between them:

$$
W = F \cdot s \cdot cos(\theta)
$$

When you threw the ball to your friend, you did a certain amount of work on it. Ignoring units for a moment, let’s say you pushed the ball with a force of 2 over a distance of 10. You could imagine that to stop the ball, your friend would have to also apply a force of 2 over a distance of 10, but in the opposite direction. Let’s say your friend is five times stronger than you, and can stop the ball with a force of 10. Can you guess how much distance they would need? The answer is 2! The amount of work you and your friend does on the ball is the same, but because your friend can apply more force, they need less distance to stop the ball.

When you do work on the ball, something is transferred to it. The ball then carries this something to your friend and they need to remove it to stop the ball. What is this something? It’s energy! In this case, it is kinetic energy.

This gives us an idea of what work does: it transfers energy!
Now you might have heard that there are different types of energy and that energy is always conserved. We will get to that, but let’s first build some more intuition of what energy is.

## Force fields

Force fields might sound like science fiction, but it is actually not. In fact, you are most likely inside one right now: gravity!

A field is a concept from mathematics that assigns a value to each point in space. An example would be the temperature in your room: each point in your room has a temperature assigned to it. It could also be the pressure in the atmosphere: you might have heard about low and high pressure zones. Fields can also be more advanced with each point in space having both a direction and magnitude, for example representing which direction the wind blows and how fast it is.
The first kind of field is called a scalar field, because each point is associated with a scalar value. The second is called a vector field. There also exists tensor fields which for example are used to represent the stresses in a steel bar.

Gravity is an example of a vector field (if you ask Newton, that is. Einstein would probably say something different), with the vector at each position describing how much force a certain mass at that point will experience due to gravity. The vector “arrows” point towards the center of the earth (or whichever planet you are on) and their size determine how strong the gravity is.

Now getting to the point. When you lift something against gravity, you do a certain amount of work on it. You do positive work on the ball, because the force and the displacement is in the same direction, but gravity is also exerting a force on it while the ball is moving. This gravitational force is in the opposite direction of movement, so the work done by it is negative. Remember, when doing positive work on something you transfer energy to it, so when doing negative energy on something, it is reasonable to say that energy is transferred to you. This means that, by lifting the ball, you transfer energy to the gravitational field (really the system of the ball and the planet). When letting go of the ball again, the gravitational field then gives back the energy to the ball and it falls down. If you associate this energy with the ball instead, you could say that by moving against the gravitational field the ball is gaining some kind of energy other than kinetic energy: this is what potential energy is!

Just as gravitational fields and mass give you gravitational potential energy, electric fields and charges give you electrical potential energy (also known as voltage). With any potential energy, it is important to remember that it is relative. Just like saying “this point is 5 meters” doesn’t make sense, it doesn’t make sense to say that “this ball has 5 Joules of potential energy” or “this point in the circuit has 5 volts”, it is always relative to something! “This ball is 5 meters above the ground”, “this ball has 5 joules of potential energy relative to this other point”, “there is 5 volts across this resistor”.

## Kinetic and potential energy

Where potential energy is energy associated with a displacement in a force field, kinetic energy is the energy associated with movement. I would like to elaborate a little more on kinetic energy.

Normally when talking about forces and acceleration, time is the interesting dimension. When applying a force to an object, its speed will increase over time, that is acceleration. But the whole point of energy is that we are interested in space, and not time. When your friend catches the ball, we weren’t interested in much time it took for them to slow the ball down, but how far it traveled in that time.

The equation for the kinetic energy of an object is as follows:

$$
E_{kin} = \frac{1}{2} m v^2
$$

You can see that it only depends on the mass and speed of the object. I won’t derive the equation here (this requires some calculus and also explains where the $\frac{1}{2}$ comes from), but here is some intuition as to why the speed is squared:

Stopping the ball will take a certain time, which depends on the mass, force and velocity (not squared in this case). Let’s look at a small moment of time right when we begin slowing the ball: it is traveling fast, so before being slowed down a little, it traverses a large distance. In the next moment after, the ball is slower, so it doesn’t traverse as big of a distance. These distances add up until the ball is stationary. The larger the initial speed is, the larger all these distances are and the more of them there will be, as the ball takes longer to slow down: the speed affects both the time, and the distance traveled in that time. This should give you some intuition as to why the speed is squared in the equation.

## Forms of energy and conservation

Now you might already have an idea of why energy would be conserved. As we discussed, work is transfer of energy, so no energy disappears in that process. Neither is there a way to destroy energy as this would involve either slowing down an object without exerting a force on it or somehow teleporting objects around a force field. Energy might leave a system, but never disappear from the grand scheme of things.

As a last thing, you might have heard about different forms of energy. Other than kinetic energy, these are often just specific cases of potential and kinetic energy. For example:

- Chemical energy is the potential energy stored in the bonds between atoms. When a chemical reaction releases energy, it is because the total energy in the bonds of the products is less than the reactants. This comes down to electrical potential energy.
- Thermal energy (heat) is kinetic energy at the molecular scale.

## Further reading

See the links below
