---
layout: post
title: The Smoluchowski Coagulation Equation
---
## Introduction

  In this post I want to go through a detailed discussion of the Smoluchowski coagulation equation (SCE), a beautifully complicated partial differential equation (PDE) used to model clumping dynamics in solutions of microscopic particles. I have divided this post into several sections. First we will briefly discuss some history and processes the equation is intended to model. Then we will discuss all the parts of the equation and see whether it indeed serves as a plausible model. We will then turn to discuss various analytical solutions to the equation as well as possible numerical solution methods. Finally, we will consider possible extensions and modifications of the original PDE, and some interesting applications these extensions might have.

## History

  Marian Smoluchowski (1872-1917) was a polish physicist, and is probably best remembered for his explanation for the Brownian motion, which he derived independently of Einstein in 1906. He worked primarily in the fields of kinetic theory and statistical mechanics. In 1916, he derived his celebrated coagulation equation, which is the subject of this post.

## Motivation

  The SCE can be used to model clumping dynamics in colloidal systems. A colloid is any system where large molecules, droplets, or particles dispersed through some other bulk medium. Examples include milk, blood, mayonnaise, shaving cream, smoke, and polymeric and micellar solutions. The suspended particles will exert forces on each other, which may be attractive. For example, consider a solution of proteins disolved in water. The proteins may be charged and thus experience coulombic forces. Even in the absence of charges, depletion forces may be at work, and cause the particles to attract. 
  
  How might we study the evolution of such a system? We could take very detailed, granualar view, perhaps using molecular dynamics software and obtain trajectories of the particles from the forces involved. Perhaps for a large enough system simulated over a long enough time we might be able to observe clumping. This is a computationally expensive approach, and will become very difficult for large numbers of particles and long simulation time lengths.
  
  Is there another way? We could take the opposite approach, sweep the details of the molecular forces and trajectories away, and zoom out to examine the system on a much larger scale. Here we would not worry about what one particle is doing at some moment in time. In fact, that sort of information would be completely inaccessible to us. This is not a problem though, if we are only interested in the macroscopic properties of the system, such as the distribution of clump sizes. This is the approach we take with the SCE.

## Constructing the Equation

<img src="https://render.githubusercontent.com/render/math?math=\frac{\partial n(x_i,t)}{\partial t}= \frac{1}{2} \sum_{j=0}^{i-1}K(x_i-x_j,x_j)n(x_i-x_j,t)n(x_j,t) - \sum_{j=1}^{\infty}K(x_i,x_j)n(x_i,t)n(x_j,t)">

![_config.yml]({{ site.baseurl }}/images/coagulation.gif)

I say "constructing" because, as with many famous differential equations in science, there is no mathematically rigourous derivation. The equation is constructed in a way that makes physical or intuitive sense. ???? Give example a la Feynman, Schodinger equation, Baggott, first principles,etc..????


## Analytical Solutions, Numerical Methods
## Extensions, and further Applications
  


