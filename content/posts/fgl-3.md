---
title: "Formal groups, part 3: height and p-typical FGLs"
date: 2024-08-02
draft: true
---
$\newcommand{\pard}[2]{\frac{\partial #1}{\partial #2}} \newcommand{\ZZ}{\mathbb{Z}} \newcommand{\QQ}{\mathbb{Q}} \newcommand{\GG}{\mathbb{G}} \newcommand{\FF}{\mathbb{F}} \DeclareMathOperator{\nil}{nil} \DeclareMathOperator{\Spec}{Spec} \DeclareMathOperator{\Spf}{Spf} \DeclareMathOperator{\Ab}{Ab}$Last time, we have seen that FGLs are boring over $\QQ$. So what if we do not invert all primes, but invert all primes *except for $p$*? The resulting ring is called $\ZZ_{(p)}$, which is $\ZZ$ localized at the prime ideal $(p)$. This is a local ring with maximal ideal $p\ZZ_{(p)}$, and it satisfies the property that for any ring $A$ in which primes $q\neq p$ are all invertible, there is a unique map $\ZZ_{(p)}\to A$ (i.e. it is a $\ZZ_{(p)}$-algebra in a unique way). We will study FGLs over $\ZZ_{(p)}$-algebras. 