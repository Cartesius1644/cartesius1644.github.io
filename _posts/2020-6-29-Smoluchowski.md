---
layout: post
title: The Smoluchowski Coagulation Equation
---

  In this post I want to go through a detailed discussion of the Smoluchowski coagulation equation, a beautifully complicated partial differential equation (PDE) used to model clumping dynamics in solutions of microscopic particles. I have divided this post into several sections. First we will briefly discuss some history and processes the equation is intended to model. Then we will discuss all the parts of the equation and see whether it indeed serves as a plausible model. We will then turn to discuss various analytical solutions to the equation. Finally, we will consider numerical solution methods and possible extensions and modification of the original PDE.

<img src="https://render.githubusercontent.com/render/math?math=\frac{\partial n(x_i,t)}{\partial t}= \frac{1}{2} \sum_{j=0}^{i-1}K(x_i-x_j,x_j)n(x_i-x_j,t)n(x_j,t) - \sum_{j=1}^{\infty}K(x_i,x_j)n(x_i,t)n(x_j,t)">




![_config.yml]({{ site.baseurl }}/images/coagulation.gif)


