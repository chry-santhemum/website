---
title: "Formal groups, part 1"
date: 2024-07-27
draft: false
---
$\newcommand{\ZZ}{\mathbb{Z}} \newcommand{\FF}{\mathbb{F}} \DeclareMathOperator{\nil}{nil} \DeclareMathOperator{\Spec}{Spec} \DeclareMathOperator{\Spf}{Spf} \DeclareMathOperator{\Ab}{Ab}$This stuff is all standard material and there are a ton of good expositions on this topic, but I thought this would be a good place to begin because the theory of formal groups starts out being really quite elementary, but it quickly goes pretty deep and reaches into a couple of surprising places. 

Before telling you what a formal group is, let me tell you what a formal group *law* is, which is something arguably easier to describe. Let us fix a ring $R$ (all rings will be unital and commutative). A *formal group law* (FGL for short) over $R$ is simply a formal power series

$$F(x,y) \in R[[x,y]]$$

which satisfies the familiar axioms for abelian groups:
- commutativity $F(x,y)=F(y,x)$
- associativity $F(x,F(y,z))=F(F(x,y),z)$
- identity $F(0,x)=F(x,0)=x$.

In other words, to write down a FGL over $R$, you just need to choose some elements $c_{ij}\in R$ for $i,j\ge 1$, and let 

$$F(x,y) = x + y + \sum_{i,j\ge 1} c_{ij} x^iy^j, \tag{1}$$

as long as the $c_{ij}$ you chose makes $F$ satisfy commutativity and associativity. These constraints, in terms of $c_{ij}$, are some polynomial equations: commutativity is simply $c_{ij} = c_{ji}$, and associativity is more complicated, but nonetheless described by some polynomial relations in the variables $c_{ij}$. 

In other words, there is a "universal" FGL, from which all other FGLs follow. This occurs over the ring where $c_{ij}$ are literally just free variables subject to the above polynomial constraints. This universal ring is called the "Lazard ring":

$$L = \ZZ[c_{ij}]/(\text{relations}),$$

and the universal FGL which lives over it is literally eq. (1). And for an arbitrary ring $R$, to give a FGL over it is exactly the same as giving a ring homomorphism $L\to R$. This is something algebraic geometers really like to do: we have a functor which associates to a ring $R$ the set of FGLs over it, and we have shown that this functor is "representable", in fact represented by the ring $L$.

Another way to phrase this is that the affine scheme $\Spec L$ is the *moduli space* for FGLs, in the sense that its "$R$-points" (aka maps of schemes $\Spec R\to \Spec L$, aka ring maps $L\to R$) are naturally in bijection with FGLs over $R$.

This is all quite trivial so far, so I want to take a slightly different view on what a FGL does. Let's fix an FGL $F(x,y)$ over $R$. For any $R$-algebra $A$, we can consider the set $\nil(A)$ of elements $a\in A$ which are nilpotent. You can easily check that the set $\nil(A)$ actually forms an ideal in $A$, the nilradical. There is already an addition on it, namely if $x,y\in\nil(A)$ then so is $x+y\in \nil(A)$. But this FGL we have gives us another way of adding $x,y$ together, namely $F(x,y)$. It is well-defined: $x,y$ are nilpotent, so the potentially infinite sum in $F(x,y)$ is actually a finite sum. Furthermore it makes $\nil(A)$ into an abelian group, by the axioms which $F$ has to satisfy. So this gives $\nil(A)$ a group structure that is different from plain addition. 

Thus, we have a functor from the category of $R$-algebras to the category of abelian groups, which maps $A$ to $\nil(A)$ with this group structure defined by $F$. In algebraic geometry, this is the functor represented by the formal scheme $\Spf R[[x]]$, which is a group object in the category of formal schemes.

There is a slight catch in this construction which takes us to the concept of formal groups (FG for short). The catch is that the power series $F(x,y)$ cannot be completely recovered from the functor it defines. To see this, let's choose any power series $u(t) \in R[[t]]$ such that $u(t)\equiv t\pmod{t^2}$, and let 

$$G(x,y) = u(F(u^{-1}(x), u^{-1}(y))).$$

What's going on here is that $u$ can be seen as an invertible change of coordinates. And even though $F\neq G$ as formal power series, they represent isomorphic functors. You can also view $u$ as an isomorphism of FGLs $F\to G$. 

So different FGLs may define the same formal group. In other words, to a ring $R$ we can really associate not just a set, but a *groupoid* of FGLs, wherein an object is a FGL and a map is an isomorphism of FGLs. This groupoid is nontrivial, as FGLs could have many automorphisms! For example, for the additive FGL over $\FF_2$, $F(x,y)=x+y$, any formal power series of form 

$$u(t)=t + a_1t^2 + a_2t^4 + a_3t^8 + \dots$$ 

is an automorphism. In fact, the automorphism group scheme of the additive formal group over $\FF_2$ can be naturally identified with the mod 2 dual Steenrod algebra. (What?)

Just as before $L$ (or more precisely $\Spec L$) was the moduli space for FGLs, we would like to have some sort of moduli space which takes these isomorphisms into account. In other words, we would like to have a ring (or scheme) whose $R$-points are naturally in bijection with the isomorphism classes of FGLs. 

However, such an object doesn't exist as a ring, or even as a scheme. The keyword, of course, is a *stack*. In this post I will avoid this word. Instead, I'll end by telling you what a formal group exactly is.

Recall that from a FGL $F(x,y)$ over $R$ we can get a functor

$$R\text{-algebras} \to \Ab. \tag{2}$$

Given a functor (2), we say it is a *coordinatizable formal group* if it comes from some (non-unique) $F(x,y)$. In particular, a coordinatizable FG is a Zariski sheaf. 

This is not what we eventually want. One reason is that such objects do not satisfy *Zariski descent*. This means that after gluing together several coordinatizable FGs, the resulting functor may not be coordinatizable anymore. The solution then is to just define the problem away.

A *formal group* over $R$ is a functor (2) which is a Zariski sheaf, and which is *Zariski-locally* coordinatizable. In concrete terms, this means that there exists a family of elements $f_1,\dots,f_n\in R$, such that

- They generate the unit ideal (some $R$-linear combination of them is 1);
- For each $i$, the composition $R_{f_i}\text{-algebras} \to R\text{-algebras} \to \Ab$ is coordinatizable, where the first functor is the natural inclusion.