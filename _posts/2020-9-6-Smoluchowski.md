---
layout: post
title: The Smoluchowski Coagulation Equation
---

## Introduction

  In this post I want to go through a discussion of the Smoluchowski coagulation equation (SCE), a beautifully complicated partial differential equation (PDE) used to model clumping dynamics in solutions of microscopic particles. I have divided this post into several sections. First we will briefly discuss some history and the processes the equation is intended to model. Then we will discuss all the parts of the equation and see whether it indeed serves as a plausible model of coagulation. Finally, we will briefly discuss an example of an analytical solution to the SCE and consider possible extensions and modifications of the original PDE, as well as some interesting applications these extensions might have.

## History

![_config.yml]({{ site.baseurl }}/images/marian_smoluchowski_original.jpg)

  Marian Smoluchowski (1872-1917) was a polish physicist, and is probably best remembered for his explanation for the Brownian motion, which he derived independently of Einstein in 1906. He worked primarily in the fields of kinetic theory and statistical mechanics. In 1916, he derived his celebrated coagulation equation, which is the subject of this post.

## Motivation

  The SCE can be used to model clumping dynamics in colloids. A colloid is any system where large molecules, droplets, or particles are dispersed through some other bulk medium. Examples include milk, blood, mayonnaise, shaving cream, smoke, and polymeric and micellar solutions. The suspended particles will exert forces on each other, which may be attractive, leading to clumping. For example, consider a solution of proteins disolved in water. The proteins may be charged and thus experience coulombic forces. Even in the absence of charges, depletion forces may be at work and cause the particles to attract. 
  
  How might we study the evolution of such a system? We could take a very detailed, granular view, perhaps using molecular dynamics software, and obtain trajectories of the particles from the forces involved. For a large enough system simulated over a long enough time we might be able to observe clumping. This is a computationally expensive approach though and will become very difficult for large numbers of particles and long simulation timescales.
  
  Is there another way? We could take the opposite approach, sweep the details of the molecular forces and trajectories away, and zoom out to examine the system on a much larger scale. Here we would not worry about what one particle is doing at some moment in time. In fact that sort of information would be completely inaccessible to us. This is not a problem though if we are only interested in the macroscopic properties of the system, such as the distribution of cluster sizes. This is the approach we take with the SCE.

## Constructing the Equation

### Comment on Derivations

  Before we begin I want to make a few comments about the title and intention of this section. I say we are "constructing" the SCE because, as with many famous differential equations in science, there is no mathematically rigourous derivation. The equation is constructed in a way that makes physical or intuitive sense. In the Feynmann Lectures, Feynmann says, refering to the Schrodinger Equation, "Where did we get that from? Nowhere. It’s not possible to derive it from anything you know. It came out of the mind of Schrödinger, invented in his struggle to find an understanding of the experimental observations of the real world." In his book *The Meaning of Quantum Theory*, Jim Baggot gives an informal derivation of the Schrodinger equation, which follows what Schrodinger did in his private notebooks. It starts with the classical wave equation and only takes about five lines of simple math. But it is not a derivation in the rigorous sense that a mathematician would want, and is not grounded in some deeper, more fundimental theory or picture of nature. So far no-one has provided such a derivation. But the Schrodinger equation does have an intuitive, informal derivation which makes sense, and the predictions that come from its application agree excellently with experiment and observation. This is the ultimate criteria in science, but it would be nice to see the equation emerge logically from some set of axioms or first principles. This is an active (and very interesting and difficult) area of research. 
  
  It is in this same spirit that we should take the "derivation" of the SCE. That is why "constructing" might be a better, more accurate word for what we will do. Smoluchowski probably had good reasons for writing his equation the way he did, and we will try to understand them. The important point is that they were based in physical intuition, rather than mathematical rigor. Hopefully one day there will exist proofs, part of more general theories, that shows why the differential equations we use are the only ones that can model our world. 

### Assumptions and Justification for the Discreet Equation

  Now to business. We need to make some assumptions and definitions before constructing the SCE. In the case of the discrete SCE, we assume our system consists of a large number of fundamental particles dissolved in a fluid medium.They are fundamental in the sense that for the model we ignore any possibility that they can be broken down or built up of smaller particles. For the model they serve as the "Lego bricks" out of which larger particles or "clusters" form through coagulation. Of course, if the fundimental particles are proteins or polymers then they are not actually fundimental, but the idea is that we are ignoring there internal parts and internal degrees of freedom (the monomers or atoms they are made out of). clusters of various sizes (or massses) <img src="https://render.githubusercontent.com/render/math?math=x_i"> form through aggregation of smaller clusters or fundamental particles. <img src="https://render.githubusercontent.com/render/math?math=x_i"> could be the diameter of a cluster or its mass. Alternatively, it could also be the length of a polymer. Finally we assume that aggregation is irreversible: clusters only get bigger, they never fragment or shed particles. However, we can easily modify the SCE to account for both aggregation and fragmentation. We will come back to this.
 
<img src="https://render.githubusercontent.com/render/math?math=1.\quad \frac{\partial n(x_i,t)}{\partial t}= \frac{1}{2} \sum_{j=0}^{i-1}K(x_i-x_j,x_j)n(x_i-x_j,t)n(x_j,t) - \sum_{j=1}^{\infty}K(x_i,x_j)n(x_i,t)n(x_j,t)">

  Above is the SCE in all its glory. What do we notice first about its overall structure? What is the biggest picture view or broadest statement we can make about it? Examining the left hand side, we see it is a partial differential equation (PDE) with respect to time, defining some unknown scalar function <img src="https://render.githubusercontent.com/render/math?math=n(x_i,t)">. Here, <img src="https://render.githubusercontent.com/render/math?math=n(x,t)=\frac{N(x,t)}{V}"> where <img src="https://render.githubusercontent.com/render/math?math=N(x,t)"> is the total number of clusters of size <img src="https://render.githubusercontent.com/render/math?math=x"> in the system at time <img src="https://render.githubusercontent.com/render/math?math=t">, and <img src="https://render.githubusercontent.com/render/math?math=V"> is the volume of the system. This means <img src="https://render.githubusercontent.com/render/math?math=n(x,t)"> is the number of clusters of size <img src="https://render.githubusercontent.com/render/math?math=x"> at time <img src="https://render.githubusercontent.com/render/math?math=t"> per unit volume, that is the number density of clusters. We can imaging <img src="https://render.githubusercontent.com/render/math?math=V"> to be the volume of a container, such as a test tube in which we have prepared our system. Because our clusters our so numerous it is more convenient to deal with density rather than total numbers. In the model, because the clusters are so small compared to the container, the container can be treated as essentially infinite. Thus the number of clusters (and fundimental particles) is essentially infinite as well. This makes the use of density functions necessary, since we cannot deal with infinite quantities.
  
  Now consider the chemical equation <img src="https://render.githubusercontent.com/render/math?math=X %2B Y \rightarrow Z">, where <img src="https://render.githubusercontent.com/render/math?math=X"> and <img src="https://render.githubusercontent.com/render/math?math=Y"> are the reactants and <img src="https://render.githubusercontent.com/render/math?math=Z"> is the product. Using some basic knowledge of chemical kinetics we can write a corrisponding rate equation 
  
<img src="https://render.githubusercontent.com/render/math?math=2.\quad \frac{\partial n(z,t)}{\partial t}=K(x,y)n(x,t)n(y,t)">

  First note that equation 2 is idendical in form to a single term in one of the sums of equation 1. Secondly, equation 2 is an example of the Law of Mass Action. The rate of change of the concentration of a chemical <img src="https://render.githubusercontent.com/render/math?math=Z"> is proportional to the product of the concentration of chemical <img src="https://render.githubusercontent.com/render/math?math=X"> and the concentration of chemical <img src="https://render.githubusercontent.com/render/math?math=Y">. <img src="https://render.githubusercontent.com/render/math?math=K(x,y)"> is the reaction rate constant and models the likelyhood that a reaction between <img src="https://render.githubusercontent.com/render/math?math=X"> and <img src="https://render.githubusercontent.com/render/math?math=Y"> will occur to produce <img src="https://render.githubusercontent.com/render/math?math=Z">. It measures the number of encounters between molecules of <img src="https://render.githubusercontent.com/render/math?math=X"> and molecules <img src="https://render.githubusercontent.com/render/math?math=Y"> per unit volume per unit time. As an interesting asside, this is identical to an assumption made in the Lotka Volterra equations, an ecological model of predator prey interactions: "The rate of predation upon the prey is assumed to be proportional to the rate at which the predators and the prey meet". In the SCE it is called the coagulation kernel and comes from the theory of integral transforms that includes Fourier and Laplace transforms.
  
  Note this all assumes that the system is "well mixed", that is we assume we do not have to worry about chemical species (or animals) of one type segregating into large patches or phases. In that more complex case interactions would happen at interfaces between the different phases, and we would have to consider the details of the motion of the fluid of chemicals or animal populations. For the SCE model we ignore bulk fluid flow. This is illustrated in figure 1. In the case of the SCE the red and blue particles could represent two possible cluster sizes. In a more realisitic scenario there would be many more than just two different cluster sizes. The point about mixing is related to what we mentioned earlier about ingnoring the details of molecular motion in favour of a "big picture view". If we did not make the assumption that the system is well mixed, we probably would not need to know the trajectories of individual molecules, but we would need to take a more granular view of the fluid. This would probably involve creating a model which married the SCE and the reaction-diffusion equations or the Navier-Stokes equations, which are used to model the flow of fluids and chemical species. 

![_config.yml]({{ site.baseurl }}/images/mixed_unmixed.png)

Fig 1: A represents a well mixed system of two species of particles. B represents a system of two species of particles seperated into two phases.
  
  Now consider the overall structure of equation 1 again. We are interested in the rate of change of the number of clusters of size <img src="https://render.githubusercontent.com/render/math?math=x_i"> We expect this rate to depend on the number clusters of size <img src="https://render.githubusercontent.com/render/math?math=x_i"> that are being formed through aggragation of smaller clusters, minus the number that are being removed by combining with other clusters to form still larger clusters. Possible interactions in terms of the fundimental particles are illustrated in the figure 2. The process of multiple reactions (and some of their coagulation kernels) is animated in figure 3.

![_config.yml]({{ site.baseurl }}/images/Smoluchowski_Aggregation_Kinetics.png){:height="30%" width="30%"}

Fig 2: Various possible reactions and there respective coagulation kernels or reaction rate constants.

![_config.yml]({{ site.baseurl }}/images/coagulation_loop.gif)

Fig 3: Illustration of coagulation process with some example coagulation kernels and their respective clusters.

  Let's zoom down further and just consider the first term on the right hand side. This term accounts for the formation of a cluster of size (or mass) <img src="https://render.githubusercontent.com/render/math?math=x_i"> through the sticking together of a particle of size <img src="https://render.githubusercontent.com/render/math?math=x_i-x_j"> and a particle of size <img src="https://render.githubusercontent.com/render/math?math=x_j">. Note <img src="https://render.githubusercontent.com/render/math?math=(x_i-x_j) %2B x_j=x_i">. But there are many particles of size <img src="https://render.githubusercontent.com/render/math?math=x_j"> and <img src="https://render.githubusercontent.com/render/math?math=x_i-x_j"> so we need to sum over <img src="https://render.githubusercontent.com/render/math?math=j"> to account for all of them.

  We account for their likelihood to meet each other, react, and form a cluster of size <img src="https://render.githubusercontent.com/render/math?math=x_i"> using equation 2. This will increase the concentration of a cluster of size <img src="https://render.githubusercontent.com/render/math?math=x_i">. We sum up to <img src="https://render.githubusercontent.com/render/math?math=i-1"> because if <img src="https://render.githubusercontent.com/render/math?math=i"> were allowed to equal <img src="https://render.githubusercontent.com/render/math?math=j"> then <img src="https://render.githubusercontent.com/render/math?math=x_i-x_j=0">. Adding a cluster of size <img src="https://render.githubusercontent.com/render/math?math=0"> to <img src="https://render.githubusercontent.com/render/math?math=x_j=x_i"> would do nothing. Why is
there a <img src="https://render.githubusercontent.com/render/math?math=\frac{1}{2}">? This stops double counting from happening: <img src="https://render.githubusercontent.com/render/math?math=x_1 %2B x_3"> is the same as <img src="https://render.githubusercontent.com/render/math?math=x_3 %2B x_1">. There is no order or directionality to how the reactants combine, because for a single reaction only two chemical species are involved and they only react in one step.

  Now consider the second term on the right hand side. clusters of size <img src="https://render.githubusercontent.com/render/math?math=x_i"> disappear when they fuse with other clusters or with fundamental particles. We sum over all cluster sizes, since addition of any other sized cluster would produce a cluster that is no longer of size <img src="https://render.githubusercontent.com/render/math?math=x_i">. This lowers the instantaneous concentration of clusters of size <img src="https://render.githubusercontent.com/render/math?math=x_i">. To round out our analysis of the SCE let us return to the big picture view and note the single PDE, equation 1, really represents a system of coupled PDEs, because the concentration of any given <img src="https://render.githubusercontent.com/render/math?math=x_i"> depends on the concentrations of all the others, which themselves depend on <img src="https://render.githubusercontent.com/render/math?math=x_i"> and all the others <img src="https://render.githubusercontent.com/render/math?math=x_{j \neq i}">.
  
### The Continuous Generalization

We can generalize the SCE to deal we a continuum of possible clump sizes. We start with equation 1 and make the substitutions <img src="https://render.githubusercontent.com/render/math?math=x_i \rightarrow x">, <img src="https://render.githubusercontent.com/render/math?math=x_j \rightarrow y">, <img src="https://render.githubusercontent.com/render/math?math=\sum_{j=0}^{i-1} \rightarrow \int_{0}^{x} dy">. We take the limit as the size of the fundimental particles goes to zero and the number of fundimental particles added together to make a clump goes to infinity while still keeping the size of the clump at the finite value <img src="https://render.githubusercontent.com/render/math?math=x">.

<img src="https://render.githubusercontent.com/render/math?math=3.\quad \frac{\partial n(x,t)}{\partial t} = \frac{1}{2} \int_{0}^{x} K(x-y,y)n(x-y,t)n(y,t)dy - \int_{0}^{\infty} K(x,y)n(x,t)n(y,t)dy">


## Analytical Solutions, Numerical Methods, and Extensions

![_config.yml]({{ site.baseurl }}/images/n_xt_SCE_k_const.png)

Fig 4: Plot of the solution of the discrete SCE <img src="https://render.githubusercontent.com/render/math?math=n(x_i,t)"> as a function of integer cluster size <img src="https://render.githubusercontent.com/render/math?math=x_i"> and time <img src="https://render.githubusercontent.com/render/math?math=t"> for the constant coagulation kernel <img src="https://render.githubusercontent.com/render/math?math=K(x_i,x_j)=1">

  The analytical solution of the SCE with a constant coagulation kernel <img src="https://render.githubusercontent.com/render/math?math=K(x_i,x_j)=1"> is plotted in figure 4.

<img src="https://render.githubusercontent.com/render/math?math=4.\quad \frac{\partial n(x,t)}{\partial t} = \frac{1}{2} \sum_{j=0}^{i-1} [K(x_i-x_j,x_j)-F(x_i-x_j,x_j)]n(x_i-x_j,t)n(x_j,t) - \sum_{j=1}^{\infty} [K(x_i,x_j)-F(x_i,x_j)]n(x_i,t)n(x_j,t)">

  As mentioned earlier, in the original model cluster growth is always positive. In equation 4 I modified the SCE by adding some terms to account for fragmentation. All I really did was add <img src="https://render.githubusercontent.com/render/math?math=F(x,y)">, which essentially does the opposite of <img src="https://render.githubusercontent.com/render/math?math=K(x,y)">, and accounts for the reverse reaction where a cluster can fragment into two smaller clusters. Perhaps this can happen when two clusters collide and shatter. Note that there is no reason for the forward and reverse processes to have the same rates. Coagulation could be favored over fragmentation, or vis versa. A still some more complicated situation could exist where what effect dominates changes with time. Maybe the clusters become more delicate as they get larger and so are more prone to fragmentation once they have gotten large enough.

  A possible application of this extended model is actin treadmilling.

## Conclusion

In this post we discussed the Smoluchowski Coagulation Equation. We gave an intuitive argument for why the SCE has the form that it does, for both the discrete and the continuous case.

To do list:
1. discuss continuous equation
2. discuss case where clusters have more than one property <img src="https://render.githubusercontent.com/render/math?math=n(x_{i}^{\alpha},x_{j}^{\beta},\ldots, x_{k}^{\gamma},t)">
3. Write conclusion
4. Add sources
5. Proof read

  


