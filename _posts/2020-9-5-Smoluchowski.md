---
layout: post
title: The Smoluchowski Coagulation Equation
---

## Introduction

  In this post I want to go through a detailed discussion of the Smoluchowski coagulation equation (SCE), a beautifully complicated partial differential equation (PDE) used to model clumping dynamics in solutions of microscopic particles. I have divided this post into several sections. First we will briefly discuss some history and the processes the equation is intended to model. Then we will discuss all the parts of the equation and see whether it indeed serves as a plausible model of coagulation. We will then turn to discussing various analytical solutions to the equation as well as possible numerical solution methods. Finally, we will consider possible extensions and modifications of the original PDE, and some interesting applications these extensions might have.

## History

![_config.yml]({{ site.baseurl }}/images/marian_smoluchowski_original.jpg)

  Marian Smoluchowski (1872-1917) was a polish physicist, and is probably best remembered for his explanation for the Brownian motion, which he derived independently of Einstein in 1906. He worked primarily in the fields of kinetic theory and statistical mechanics. In 1916, he derived his celebrated coagulation equation, which is the subject of this post.

## Motivation

  The SCE can be used to model clumping dynamics in colloids. A colloid is any system where large molecules, droplets, or particles are dispersed through some other bulk medium. Examples include milk, blood, mayonnaise, shaving cream, smoke, and polymeric and micellar solutions. The suspended particles will exert forces on each other, which may be attractive, leading to clumping. For example, consider a solution of proteins disolved in water. The proteins may be charged and thus experience coulombic forces. Even in the absence of charges, depletion forces may be at work and cause the particles to attract. 
  
  How might we study the evolution of such a system? We could take a very detailed, granular view, perhaps using molecular dynamics software, and obtain trajectories of the particles from the forces involved. For a large enough system simulated over a long enough time we might be able to observe clumping. This is a computationally expensive approach though and will become very difficult for large numbers of particles and long simulation timescales.
  
  Is there another way? We could take the opposite approach, sweep the details of the molecular forces and trajectories away, and zoom out to examine the system on a much larger scale. Here we would not worry about what one particle is doing at some moment in time. In fact that sort of information would be completely inaccessible to us. This is not a problem though if we are only interested in the macroscopic properties of the system, such as the distribution of clump sizes. This is the approach we take with the SCE.

## Constructing the Equation

### Comment on Derivations

  Before we begin I want to make a few comments about the title and intention of this section. I say we are "constructing" the SCE because, as with many famous differential equations in science, there is no mathematically rigourous derivation. The equation is constructed in a way that makes physical or intuitive sense. In the Feynmann Lectures, Feynmann says, refering to the Schrodinger Equation, "Where did we get that from? Nowhere. It’s not possible to derive it from anything you know. It came out of the mind of Schrödinger, invented in his struggle to find an understanding of the experimental observations of the real world." In his book *The Meaning of Quantum Theory*, Jim Baggot gives an informal derivation of the Schrodinger equation, which follows what Schrodinger did in his private notebooks. It starts with the classical wave equation and only takes about five lines of simple math. But it is not a derivation in the rigorous sense that a mathematician would want, and is not grounded in some deeper, more fundimental theory or picture of nature. So far no-one has provided such a derivation. But the Schrodinger equation does have an intuitive, informal derivation which makes sense, and the predictions that come from its application agree excellently with experiment and observation. This is the ultimate criteria in science, but it would be nice to see the equation emerge logically from some set of axioms or first principles. This is an active (and very interesting and difficult) area of research. 
  
  It is in this same spirit that we should take the "derivation" of the SCE. That is why "constructing" might be a better, more accurate word for what we will do. Smoluchowski probably had good reason for writing his equation the way he did, and we will try to understand them. The important point is that they were based in physical intuition, rather than mathematical rigor. Hopefully one day there will exist proofs, part of more general theories, that shows why the differential equations we use are the only ones that can model our world. 

### Assumptions and Justification

  Now to business. We need to make some assumptions and definitions before constructing the SCE. In the case of the discrete SCE, we assume our system consists of a large number of fundamental particles dissolved in a fluid medium.They are fundamental in the sense that for the model we ignore any possibility that they can be broken down or built up of smaller particles. For the model they serve as the "Lego bricks" out of which larger particles or "clumps" form through coagulation. Of course, if the fundimental particles are proteins or polymers then they are not actually fundimental, but the idea is that we are ignoring there internal parts and internal degrees of freedom (the monomers or atoms they are made out of). Clumps of various sizes (or massses) <img src="https://render.githubusercontent.com/render/math?math=x_i"> form through aggregation of smaller clumps or fundamental particles. <img src="https://render.githubusercontent.com/render/math?math=x_i"> could be the diameter of a clump or its mass. Alternatively, it could also be the length of a polymer. Finally we assume that aggregation is irreversible: clumps only get bigger, they never fragment or shed particles. However, we can easily modify the SCE to account for both aggregation and fragmentation. We will come back to this.
 
<img src="https://render.githubusercontent.com/render/math?math=1.\quad frac{\partial n(x_i,t)}{\partial t}= \frac{1}{2} \sum_{j=0}^{i-1}K(x_i-x_j,x_j)n(x_i-x_j,t)n(x_j,t) - \sum_{j=1}^{\infty}K(x_i,x_j)n(x_i,t)n(x_j,t)">

  Above is the SCE in all its glory. What do we notice first about its overall structure? What is the biggest picture view or broadest statement we can make about it? Examining the left hand side, we see it is a partial differential equation (PDE) with respect to time, defining some unknown scalar function <img src="https://render.githubusercontent.com/render/math?math=n(x_i,t)">. Here, <img src="https://render.githubusercontent.com/render/math?math=n(x,t)=\frac{N(x,t)}{V}"> where <img src="https://render.githubusercontent.com/render/math?math=N(x,t)"> is the total number of clumps of size <img src="https://render.githubusercontent.com/render/math?math=x"> in the system at time <img src="https://render.githubusercontent.com/render/math?math=t">, and <img src="https://render.githubusercontent.com/render/math?math=V"> is the volume of the system. This means <img src="https://render.githubusercontent.com/render/math?math=n(x,t)"> is the number of clumps of size <img src="https://render.githubusercontent.com/render/math?math=x"> at time <img src="https://render.githubusercontent.com/render/math?math=t"> per unit volume, that is the number density of clumps. We can imaging <img src="https://render.githubusercontent.com/render/math?math=V"> to be the volume of a container, such as a test tube in which we have prepared our system. Because our clumps our so numerous it is more convenient to deal with density rather than total numbers. In the model, because the clumps are so small compared to the container, the container can be treated as essentially infinite. Thus the number of clumps (and fundimental particles) is essentially infinite as well. This makes the use of density functions necessary, since we cannot deal with infinite quantities.
  
  Now consider the chemical equation <img src="https://render.githubusercontent.com/render/math?math=X %2B Y \rightarrow Z">, where <img src="https://render.githubusercontent.com/render/math?math=X"> and <img src="https://render.githubusercontent.com/render/math?math=Y"> are the reactants and <img src="https://render.githubusercontent.com/render/math?math=Z"> is the product. Using some basic knowledge of chemical kinetics we can write a corrisponding rate equation 
  
<img src="https://render.githubusercontent.com/render/math?math=2.\quad \frac{\partial n(z,t)}{\partial t}=K(x,y)n(x,t)n(y,t)">

  This is an example of the Law of Mass Action. The rate of change of the concentration of a chemical <img src="https://render.githubusercontent.com/render/math?math=Z"> is proportional to the product of the concentration of chemical <img src="https://render.githubusercontent.com/render/math?math=X"> and the concentration of chemical <img src="https://render.githubusercontent.com/render/math?math=Y">. <img src="https://render.githubusercontent.com/render/math?math=K(x,y)"> is the reaction rate and models the likelyhood that a reaction between <img src="https://render.githubusercontent.com/render/math?math=X"> and <img src="https://render.githubusercontent.com/render/math?math=Y"> will occur to produce <img src="https://render.githubusercontent.com/render/math?math=Z">. It measures the number of encounters between molecules of <img src="https://render.githubusercontent.com/render/math?math=X"> and molecules <img src="https://render.githubusercontent.com/render/math?math=Y"> per unit volume per unit time. As an interesting asside, this is identical to an assumption made in the Lotka Volterra equations, an ecological model of predator prey interactions: "The rate of predation upon the prey is assumed to be proportional to the rate at which the predators and the prey meet".

![_config.yml]({{ site.baseurl }}/images/coagulation_loop.gif)



## Analytical Solutions, Numerical Methods
## Extensions, and further Applications
  


