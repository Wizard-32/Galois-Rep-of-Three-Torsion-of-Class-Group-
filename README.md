# Galois-Rep-of-Three-Torsion-of-Class-Group
## Mathematical Overview
Let $E$ be an elliptic curve over $\mathbb{Q}$, and $K = \mathbb{Q}(E[3]).$ Then the Galois action of $G:=\text{Gal}(K/\mathbb{Q})$ on $E[3] \cong \mathbb{Z}/3\mathbb{Z} \times \mathbb{Z}/3\mathbb{Z}$ gives a representation $G \to \text{GL}(2,\mathbb{F}_3).$ Suppose the image is conjugate to the normalizer of split Cartan subgroup, a sub group of order $8$ isomorphic to $D_4.$ Consider the action of $G$ on $\text{Cl}(K)[3],$ i.e. the $3$ torsion part of the class group of $K.$ We want to decompose this action.

Fix $t,d.$ From Zywina's paper and Weston's calculation, the elliptic curve then is
$$y^2+xy=x^3+\frac{1}{4}\left(\frac{1}{D}-1\right)x^2-\frac{36}{D^2(j-1728)}-\frac{1}{D^3(j-1728)}.$$
Here, $j=\left(\frac{3(t+1)(t-3)}{t}\right)^3$ and $D=\frac{(t-3)(t+1)}{2(t^2+3)d}.$
The corresponding field extension is
$$K=\mathbb{Q}(E[3]) = \mathbb{Q}\left(\sqrt{-3},\sqrt{t^2-6t-3},\sqrt{d\left(-1+\frac{t+1}{t^2-6t-3}\sqrt{-3}\sqrt{t^2-6t-3}\right)}\right).$$

## Overview of Functions 
Here's an overview of the functions used:
1. $\texttt{NSCurve(t,d)}$ returns the curve $E.$
4. $\texttt{ThreeTorsionField(t,d)}$ returns the field $K = \mathbb{Q}(E[3]).$
5. $\texttt{GiveGalois(t,d)}$ returns $G=\text{Gal}(K/\mathbb{Q}).$
6. $\texttt{GiveCharacter(phi,e,g,H)}$ returns the character of $g \in G.$ Here,
   - $\texttt{phi}$ is the map from the class group $\text{Cl}(K)$ which takes a group element and returns an actual ideal in the ring of integers $\mathcal{O}_K \subset K.$
   - $\texttt{e}$ is the map from $G=\text{Gal}(K/\mathbb{Q})$ to the automorphisms group. This is because in Magma, you can use only the elements of the automorphisms group (and not the Galois Group) to act on elements.
   - $g$ is an element of $G=\text{Gal}(K/\mathbb{Q}).$
   - $H$ is $\text{Cl}(K)[3].$
7. $\texttt{CharacterClassFunction(phi, e, G, H)}$ returns the list of characters in the format of a row of the character table. The representatives of the conjugacy classes, in order, are $[Id(G), G.1^2, G.2, G.1*G.2, G.1].$
8. $\texttt{FindDecompositionMultiplicity}(G, x, xi)$ returns the multiplicity of the irreducible character $\texttt{xi}$ in the decomposition of $\texttt{xi}.$ Here,
   - $\texttt{xi}$ is a list of characters for the irreducible representation $\chi_i.$
   - $\texttt{x}$ is a list of characters for our representation. This is obtained from $\texttt{CharacterClassFunction}.$
9. $\texttt{FindDecomposition(t,d, print_info)}$ returns the full decomposition of our representation.
   - $\texttt{print_info}$ is $1$ if you want to print additional information such as the Elliptic Curve's equation, Galois Groups. It is $0$ otherwise. 


