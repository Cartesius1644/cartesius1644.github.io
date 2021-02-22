---
layout: post
title: The Cluster Expansion Method
---

## Introduction

In this presentation we give an explanation of the cluster expansion method (CEM), a theoretical technique for studying the properties of fluids. The CEM is quite powerful and allows us to calculate the properties of simple fluids, with results closely matching those of molecular dynamics and Monte Carlo simulation techniques. Though the CEM has been replaced since the 50s by the computational techniques mentioned for studying simple fluids [1,2], developing similar methods for more complex fluid systems is still an active area of theoretical research.

The CEM is an example of a graphical technique, where calculations are made more manageable by representing mathematical terms as graphs or small, simple pictures, whose form represents the same physical meaning as the corresponding terms. This allows us to generate series solutions to problems in equilibrium statistical mechanics. We will need to break down the equations involved and explain what every term does and how it fits into the whole. Here is an outline of this presentation:

 The problem
 Hamiltonian, configuration integral, and Mayer Function
 Turning integrals into graphs
 Properties of graphs
 Conclusion


## Review of Ensembles and Partition Functions

## The Problem at Hand

 We want to use the CEM, or any other analytical or computational technique, to calculate the equation of state. The CEM is just one way to do this, and we will focus more on the CEM than the results it gives.

 Recall this is some expression that relates the macroscopic variables P, V, N, T, S.

 This expression tells us how the system will respond to various changes in the macrostate, allowing us to construct a phase diagram.

 The equation of state ultimately originates from the microscopic nature of the system, which is expressed in the Hamiltonian. In the canonical ensemble, the Helmholtz free energy serves as the intermediary:

## Motivation

## Constructing the Equation

## Conclusion

<img src="https://render.githubusercontent.com/render/math?math=3.\quad \frac{\partial n(x,t)}{\partial t} = \frac{1}{2} \int_{0}^{x} K(x-y,y)n(x-y,t)n(y,t)dy - \int_{0}^{\infty} K(x,y)n(x,t)n(y,t)dy">

![_config.yml]({{ site.baseurl }}/images/marian_smoluchowski_original.jpg)
