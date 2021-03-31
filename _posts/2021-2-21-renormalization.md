---
layout: post
title: Renormalization_Draft
---

## Introduction

In these notes we study the $2D$ Ising model on the triangular lattice using the renormalization method. This is a toy model which is nonetheless extremely difficult to solve analytically. The renormalization group method is a powerful technique in the toolbox of theoretical physics and its development and properties are very interesting in their own right. From it we can arrive at a description of the system which is independent of the scale. Thus a small-scale, highly specific picture gives rise smoothly to a larger-scale, universal picture.

Magnetism has fascinated humans since ancient times, though a clear model of what is going on inside a piece of magnetic material only appeared within the past hundred years or so. We imagine that a magnetic material is composed of a very large number of atomic scale bar magnets, which can take on various orientations. The microscopic structure of a magnet can be visualized as some three dimensional arrangement of these bar magnets. We will refer to these little bar magnets as spins.

In physics we like to simplify our picture as much as possible. We can reduce this model still further by imagining that the spins are arranged in some regular, repeating pattern in space (a lattice), are locked in particular positions in the lattice and cannot move from them, and can only have one of two possible orientations at any given time. We call the two orientations {\it{up}} or {\it{down}} and visualize them as small arrows. Of course, in a real material the spins will move about somewhat, since the spins are atoms and each atoms is connected to all the others by forces that act like small springs. In addition, the spins themselves can take on an infinite number of possible directions in $3D$ space. Finally, there is no guarantee that the spins will be arranged regularly in space. In a real material the will be impurities in the form of holes or inclusions of different types of atoms, as well as multiple domains with differently oriented crystal planes fused together. Keeping all this in mind, we still argue for our approximations. Since Newton we have understood that one of the most effective ways to study nature is to start with a simple model or scheme, investigate its properties, then gradually add on additional layers of complexity. As we shall see, just investigating the simplified model described above will prove quite challenging.

By making all of these assumptions we arrive at the {\it{Ising model}}. The Ising model is one of the core models in statistical mechanics, and has been studied extensively for nearly a hundred years. However, no analytic solutions exist for dimensions greater than two, and the two dimensional case is highly non-trivial to solve. It can be studied using computational methods, such as Monte Carlo, but we would like some sort of more manageable theoretical approach as well.

\begin{figure}
\includegraphics[trim = 200 120 120 120,clip,width=10.0cm]{reduce.pdf}
\caption{Illustration of the renormalization concept.} 
\label{reduce}
\end{figure}

Another approach is offered by renormalization. The intuition of renormalization is illustrated in figure \ref{reduce}. In this figure the spins are represented at points in a plane. We wish to reduce the number of degrees of freedom involved in the problem by converting the black lattice into the red lattice. This will involve a modification and simplification of the Hamiltonian. Recall that the Hamiltonian is essentially a statement of the mathematical model of the microscopic structure of the system. The Hamiltonian for the Ising model with no external field is:
\begin{equation}
H(\{\sigma_{i}\}) = -K \sum_{<i,j>} \sigma_{i}\sigma_{j}
\label{ham}
\end{equation}
We denote a particular configuration of the spins as $\{\sigma_{i}\}$. The sum is taken over pairs of nearest neighbors in the lattice. $K=\beta J$, where $J$ tunes the interaction strength between neighboring spins. 

Recall that the main focus of equilibrium statistical mechanics can essentially be reduced to solving the partition function, since it is the normalization factor for the probability density of the microstates. In words this will give us the probability that the system will be in a particular configuration of all the spins. The partition function also leads us to the equation of state of the system. The partition function is defined as:
\begin{equation}
Z(N,B,T) =  \sum_{\{\sigma_{i}\}} e^{-H(\{\sigma_{i}\})}
\end{equation}
Note that there will be $2^N$ terms in the sum, since this is the number of possible spin configurations. Also note that with no external field $B=0$ and is not relevant. For the Ising model we will not be too concerned with the equation of state, since pressure is not really relevant, or even defined for this kind of system.

## Relabeling and Reindexing

The particular model we intend to apply the renormalization method to is the Ising model on the triangular lattice. Our goal here is to arrive at a new Hamiltonian involving fewer degrees of freedom. We want to find some way of transforming our original Hamiltonian into a new one: $H^{'} = \tau(H)$.

\begin{figure}
\includegraphics[trim = 200 120 120 120,clip,width=10.0cm]{new_labels.pdf}
\caption{Regrouping the spins on the lattice.} 
\label{new_labels}
\end{figure}

We start by cordoning off regions of the lattice into a repeating of array of triangles, where each triangle encloses three spins, with one spin at each corner of the triangle. This is illustrated in figure \ref{new_labels}. For each triangle we can assign a {\it{representative spin}}, defined as:
\begin{equation}
\sigma_{i'}^{'} = \frac{\sigma_{i',1}+\sigma_{i',2}+\sigma_{i',3}}{|\sigma_{i',1}+\sigma_{i',2}+\sigma_{i',3}|}
\label{repspin}
\end{equation}
This represents the average of the three spins enclosed within a particular triangle an takes on values of $\pm1$. A new index $i'$ is also introduced which runs over the triangles.


\begin{figure}
\includegraphics[trim = 0 0 0 0,clip,width=10.0cm]{effect_spins.pdf}
\caption{Possible representative spins and the original spin arrangements that give rise to them.} 
\label{effect_spins}
\end{figure}

In this setup a new complexity arises. There is a degeneracy in the representative spins. This is because multiple possible arrangements of the three spins in a single triangle can give you the same value of $\sigma_{i'}^{'}$.  We use another new index $\theta_{i'}$ to label the possible configurations within a single triangle that would yield the representative spin $\sigma_{i'}^{'}$. This is illustrated in figure \ref{effect_spins}. The representative spins themselves can be imagined as new spins lying in the center of their respective triangles. They are illustrated as the red dots in figure \ref{new_labels}.

## Reducing the Degrees of Freedom

So far we have not changed anything. We still have the same Hamiltonian, and thus the same partition function. All we have done is to create a new way of accounting for how the spins fit into the Hamiltonian. Consequently, we can go from writing the partition function in terms of the old indices over the original spins, to writing the partition function in terms of the new indices, the representative spins, and the degenerate indices:
\begin{equation}
Z(N,B,T) =  \sum_{\{\sigma_{i'}^{'}\}} \sum_{\{\theta_{i'}\}}  e^{-H(\{\sigma_{i'}^{'}\},\{\theta_{i'}\})}
\label{newindz}
\end{equation}
This just says that instead of indexing over every original spin, we now index over every representative spin and then index over every degenerate index.

We now define a new object. Let:
\begin{equation}
\sum_{\{\theta_{i'}\}}  e^{-H(\{\sigma_{i'}^{'}\},\{\theta_{i'}\})} = e^{\phi - H^{'}({\sigma_{i'}^{'}})}
\label{wnewh}
\end{equation}
Equation \ref{wnewh} contains our new Hamiltonian $H^{'}$. Also, here we let $H^{'}$ absorb the thermodynamic $\beta$.

Putting equation \ref{wnewh} into equation \ref{newindz}. We then have:
\begin{equation}
Z(N,B,T) =  \sum_{\{\sigma_{i'}^{'}\}} e^{\phi - H^{'}({\sigma_{i'}^{'}})}
\label{newz}
\end{equation}
This is our new expression with fewer degrees of freedom for the partition function. We need to find some clever ways to simplify equation \ref{newz} further.

## Intra and Inter Spin Interactions

Let us return to our original Hamiltonian, as written in equation \ref{newindz}. We now propose to break it up into two parts: 
\begin{equation}
H =  H_{intra} + H_{inter}
\end{equation}
Here $H_{intra}$ indicates the contribution to the energy from interactions between particles inside the same triangle and $H_{inter}$ indicates the contribution to the energy from interactions between particles that are not in the same triangle. 

We can start by simplifying:
\begin{equation}
\sum_{\{\theta_{i'}\}}  e^{-H_{intra} (\{\sigma_{i'}^{'}\},\{\theta_{i'}\})} = \bigg(\sum_{\{\theta_{i'}\}}  e^{K(\sigma_{i',1}+\sigma_{i',2}+\sigma_{i',3})}\bigg)^{N/3}
\label{intrasimp1}
\end{equation}
The $N/3$ exponent appears because we ignore the interaction between spins in different triangles in this term. Consequently the left hand side of equation \ref{intrasimp1} can be factored into a product of $N/3$ identical terms. Each term in the product will involve a contribution from the interaction between the three spins in a single lattice. This leads to three sub-terms within each term on the left hand side of equation \ref{intrasimp1}. All three sub-terms taken together is the contribution to the energy from the interaction of three spins in a single triangle. We can go further with the simplification.
\begin{equation}
\bigg(\sum_{\{\theta_{i'}\}}  e^{K(\sigma_{i',1}\sigma_{i',2} + \sigma_{i',1}\sigma_{i',3} + \sigma_{i',2}\sigma_{i',3})}\bigg)^{N/3} = (e^{3K}+3e^{-K})^{N/3}
\label{intrasimp2}
\end{equation}
Explaining how equation \ref{intrasimp2} arises is a little more tricky. We can write out all the possible combinations of original spins in a single triangle for a particular choice of $\theta_{i'}$, that is all the combinations that would lead to the same value of $\sigma_{i'}^{'}$. This gives for $\sigma_{i'}^{'} = +1$:
\begin{equation}
\begin{split}
 1\cdot1 + 1\cdot1 + 1\cdot1 = 3 \\
-1\cdot1 + 1\cdot1 - 1\cdot1 = -1 \\
-1\cdot1 - 1\cdot1 + 1\cdot1 = -1 \\
 1\cdot1 - 1\cdot1 - 1\cdot1 = -1 \\
\end{split}
\label{list}
\end{equation}
Note there are four numbers in equation \ref{list} because there are four possible values of $\theta_{i'}=1,2,3,4$. Also, note that you arrive at the same numbers for $\sigma_{i'}^{'} = -1$.

## Approximations and Simplifications

We now take equation \ref{intrasimp1}, \ref{intrasimp2} and use it to construct an expression with the form of an average. Start by writing:
\begin{equation}
\sum_{\{\theta_{i'}\}}  e^{-H_{intra} -  H_{inter}} = \bigg(\frac{\sum_{\{\theta_{i'}\}}  e^{-H_{intra} -  H_{inter}}}{\sum_{\{\theta_{i'}\}}  e^{-H_{intra}}}\bigg) \sum_{\{\theta_{i'}\}}  e^{-H_{intra}}
\label{getavg}
\end{equation}

Now let us focus on the term in parentheses. It can be interpreted as an average. Recall the definition of the average of some quantity $A$:
\begin{equation}
\langle A\rangle = \sum_{i} p(x_{i}) A(x_{i})
\label{defavg}
\end{equation}
Using equation \ref{defavg} we can define the term in parentheses in equation \ref{getavg} as:
\begin{equation}
{\bigg\langle e^{H_{inter}} \bigg\rangle}_{intra} = \frac{\sum_{\{\theta_{i'}\}}  e^{-H_{intra} -  H_{inter}}}{\sum_{\{\theta_{i'}\}}  e^{-H_{intra}}}\
\end{equation}
Using the first order {\it{cumulant expansion}} from statistics, we make the approximation:
\begin{equation}
{\bigg\langle e^{H_{inter}} \bigg\rangle}_{intra} \approx e^{{\langle-H_{inter}\rangle}_{intra}}
\label{cumulexp}
\end{equation}
Using equation \ref{ham}, we have:
\begin{equation}
{\bigg\langle H_{inter} \bigg\rangle}_{intra} = \sum_{<i,j>} {\langle \nu_{i',j'} \rangle}_{intra}
\end{equation}
Where $\nu_{i',j'}$ is the energy contribution from the interaction of a pair of spins on different triangles. This can be written explicitly as:
\begin{equation}
{\bigg\langle H_{inter} \bigg\rangle}_{intra} = -K \sum_{<i,j>} {\langle \sigma_{i',3}(\sigma_{j',1} + \sigma_{j',2}) \rangle}_{intra}
\label{avgintranew}
\end{equation}
We can see why equation \ref{avgintranew} has this form by considering figure \ref{reduce} again. Notice that for spin $3$ on the green triangle $i'$ the only spins on a different triangle, nearest neighbors to spin $3$ are spin $1$ and $2$ on triangle $j'$.

Using the approximation in equation \ref{cumulexp} and the factoring properties of exponentials we can write equation \ref{avgintranew} as:
\begin{equation}
{\bigg\langle H_{inter} \bigg\rangle}_{intra} = -2K \sum_{<i,j>} {{\langle \sigma_{i',3}\rangle}_{intra} \langle \sigma_{j',1}\rangle}_{intra}
\label{prodavg}
\end{equation}
We can use equation \ref{defavg} again to write:
\begin{equation}
{\langle \sigma_{i',3} \rangle}_{intra} = \frac{\sum_{\{\theta_{i'}\}} \sigma_{i',3} e^{K(\sigma_{i',1}\sigma_{i',2} + \sigma_{i',1}\sigma_{i',3} + \sigma_{i',2}\sigma_{i',3})}}{\sum_{\{\theta_{i'}\}}e^{K(\sigma_{i',1}\sigma_{i',2} + \sigma_{i',1}\sigma_{i',3} + \sigma_{i',2}\sigma_{i',3})}}
\end{equation}
Using equation \ref{repspin} and the numbers in equation \ref{list} we have:
\begin{equation}
{\langle \sigma_{i',3} \rangle}_{intra} = \sigma_{i'}^{'}\frac{e^{K}+e^{-K}}{e^{3K}+e^{-K}}
\label{intraavg}
\end{equation}
Plugging equation \ref{intraavg} into equation \ref{prodavg} we obtain:
\begin{equation}
{\bigg\langle H_{inter} \bigg\rangle}_{intra} = -2K {\bigg(\frac{e^{K}+e^{-K}}{e^{3K}+e^{-K}}\bigg)}^{2}\sum_{<i,j>} \sigma_{i'}^{'} \sigma_{j'}^{'}
\label{penult}
\end{equation}

## Final Results and Conclusion

What does equation \ref{penult} mean? Recall equation \ref{ham}. Their forms are identical but equation \ref{penult} involves a sum over a small number of degrees of freedom, the indices of the triangles. So we have succeeded at our goal! We can use equation \ref{penult} to define:
\begin{equation}
H^{'}(\{\sigma^{'}\}) = K^{'} \sum_{<i,j>} \sigma_{i'}^{'} \sigma_{j'}^{'}
\label{newham}
\end{equation}
We also have a new coupling constant between the new, representative spins:
\begin{equation}
K^{'} = -2K {\bigg(\frac{e^{K}+e^{-K}}{e^{3K}+e^{-K}}\bigg)}^{2}
\end{equation}

We studied the process of renormalization for the Ising model on a triangular lattice. Through a rather lengthy series of mathematical steps, starting with the original Hamiltonian we where able to arrive at an expression for a new Hamiltonian. This new Hamiltonian depended on fewer degrees of freedom than the original. This process can be repeated. However at some point the renormalization process will reach a fixed point. When this happens further applications of the renormalization procedure will yield the same value for K. Intuitively, this means we arrive at a point where, no matter how far we zoom out from the system, no matter how many degrees of freedom we ignore, the behavior remains the same, and the system can be modeled with our final, limiting form of the Hamiltonian.

## References
1. Beale, P. D. and Pathria, R. K. (2011). Statistical Mechanics.
2. Vitali, E. (2020). Physics 275T Lecture Slides

Test equation:
<img src="https://render.githubusercontent.com/render/math?math=3.\quad \frac{\partial n(x,t)}{\partial t} = \frac{1}{2} \int_{0}^{x} K(x-y,y)n(x-y,t)n(y,t)dy - \int_{0}^{\infty} K(x,y)n(x,t)n(y,t)dy">

Test image:
![_config.yml]({{ site.baseurl }}/images/marian_smoluchowski_original.jpg)
