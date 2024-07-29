---
title: "Formal groups, part 2: the logarithm"
date: 2024-07-29
draft: false
---
$\newcommand{\pard}[2]{\frac{\partial #1}{\partial #2}} \newcommand{\ZZ}{\mathbb{Z}} \newcommand{\QQ}{\mathbb{Q}} \newcommand{\GG}{\mathbb{G}} \newcommand{\FF}{\mathbb{F}} \DeclareMathOperator{\nil}{nil} \DeclareMathOperator{\Spec}{Spec} \DeclareMathOperator{\Spf}{Spf} \DeclareMathOperator{\Ab}{Ab}$Before diving into stacks, I'd like to stay in the elementary situation a bit longer and discuss an important construction: the logarithm.

Over the initial ring $\ZZ$ (hence over any ring $R$), we have two very basic examples of FGLs:

- The additive group, $\GG_a(x,y)=x+y$;
- The multiplicative group, $\GG_m(x,y)=xy+x+y$.

(I probably should have called them $\widehat{\GG}_a$ and $\widehat{\GG}_m$ but let's not go there yet.)

To see why these names make sense, consider the functors they represent. The first one attaches to any ring $A$ its nilradical $\nil(A)$ with the usual addition law, hence "additive". The second one has $F(x,y) + 1 = (x+1)(y+1)$, so if we think of the nilpotent elements $x$ as in bijection with the "unipotent" elements $x + 1$, the multiplicative FGL gives precisely the multiplicative group on the set of unipotent elements of $A$. (Note that the nilpotent elements themselves do not have a multiplicative identity.)

Now, over $\ZZ$, these two FGLs are not isomorphic, which can be easily seen mod 2. But over the rational numbers $\QQ$, there is an isomorphism, given by the familiar logarithm:

$$u(x)=\log(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \dots$$

This needs to be over $\QQ$ because the coefficients are rational numbers. Indeed, to check that it is an isomorphism, 

$$u(\GG_m(x,y)) = \log((1+x)(1+y)) = \log(1+x)+\log(1+y) = \GG_a(u(x),u(y)).$$

It turns out that this phenomenon is not specific to the multiplicative group. In fact, over any $\QQ$-algebra, any FGL $F$ is isomorphic to $\GG_a$ via its logarithm $\log_F(x)$, which we will construct now.

First, let's construct an *invariant differential*. If this were to be a Lie group, the 1-form $\omega$ would satisfy $f^*\omega = \omega$ where $f$ is left multiplication by an element.  In this context, $\omega = h(y)dy$ should satisfy

\\[h(F(x,y))F_2(x,y) dy =h(y)dy \tag{1}\\]

and plugging in $y = 0$ gives $h(x) \propto \frac{1}{F_2(x,0)}$ (where $F_2(x,y) = \pard{}{y} F(x,y)$). This can be verified to indeed satisfy (1), using associativity of $F$.

Suppose we want to now get a logarithm $\log_F(x)$ which satisfies that $\log_F(F(x,y)) = \log_F(x)+\log_F(y)$. Taking the derivative, we see it has to satisfy

\\[\log_F'(F(x,y))F_2(x,y) = \log_F'(y),\\]

in other words $d(\log_F(y))$ is an invariant differential. Since we already have such a differential $\omega$, we can define

\\[\log_F(x) = \int_0^x \omega.\\]

Explicitly, suppose $F(x,y)=x+y+c_{ij}x^iy^j$ (using Einstein summation convention), then

\\[\omega = \frac{dt}{1 + c_{i1}t^i} = (1 - c_{i1}t^i + (c_{i1}t^i)^2 - \dots)dt\\]

and

\\[\log_F(x) = x - \frac{c_{11}}{2}x^2 + \frac{c_{11}^2 - c_{21}}{3}x^3 + \dots\\]

Again, this only makes sense over $\QQ$-algebras because we need to invert all natural numbers. So FGLs over $\QQ$-algebras are very boring: they are just isomorphic to $\GG_a$. What makes this subject interesting is the phenomenon over finite and mixed characteristic. 