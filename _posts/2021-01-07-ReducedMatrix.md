---
title: "얽혀있는 공간의 밀도 행렬"
tags: [Phyiscs, QuantumMechanics, qi] # 태그 입력
categories: Physics
sidebar:
  nav: "docs"
last_modified_at: 2025-03-15
mathjax: true # MathJax 사용을 위한 태그
image:
  path: /_images/abstract-3.jpg
  feature: abstract-3.jpg
toc: true
toc_label: Table of Contents
toc_sticky: true
comments: true
published: true
---

앞의 게시글 ["순수 상태와 혼합 상태"](/physics/PureandMixed/)에서는 pure state와 mixed state가 어떤 차이가 있는 지 알아보았다.
이번에는 양자 상태를 이루는 Hilbert space가 composite system, 즉 여러 시스템으로 이루어져 있는 경우 density matrix가 어떻게 기술되고, 어떤 특성을 가지는 지 살펴보고자 한다.

## 개요
먼저 양자계를 표현하는 공간은 Hilbert space으로 N차원 복소공간 $\mathbb{C}^N$에서 $N=2$인 경우로 기술된다. 
즉 Hilbert space $\mathcal{H} \in \mathbb{C}^2$ 이다.
이러한 Hilbert space가 composite system으로 구성되어, 하위계(subsystem) 이 A와 B로 존재할 때, density matrix가 어떻게 나타나는지 살펴본다. 
주어진 조건에서 Hilbert space 를

$$
\mathcal{H}_{AB} = \mathcal{H}_A\otimes\mathcal{H}_B
$$

으로 기술할 수 있다.
여기서 연산자 $\otimes$는 두 벡터공간의 곱을 이루는 ['텐서곱'](https://en.wikipedia.org/wiki/Tensor_product)이다.
Subsystem A와 B의 기저가 $\vert i_{\rm A} \rangle, \vert j_{\rm B} \rangle$으로 기술될 때,
pure state의 composite system basis $\vert \psi_{\rm AB} \rangle$는

$$
\vert\psi_{AB}\rangle = \sum_{i,j}{C_{ij}}\vert{i}_{\rm A}\rangle \otimes \vert{j}_{\rm B}\rangle
$$

이 때 계수 ${C_{ij}}$는 복소수이며 $\vert {C_{ij}} \vert^2 = 1$을 만족한다.
참고로, $\vert{i}_{\rm A}\rangle \otimes \vert{j}_{\rm B}\rangle$는 텐서곱을 생략하여 편의상 $\vert{i}_{\rm A}\rangle \vert{j}_{\rm B}\rangle$ 또는 $\vert{i}_{\rm A} {j}_{\rm B}\rangle$으로 기술할 수 있으며, 앞으로 기술될 식에 대해서는 텐서곱 연산자를 생략한다.

Pure state의 density operator의 정의에 따라 composite system의 density operator는

$$
\begin{aligned}
\rho_{AB} &= \vert\psi_{AB}\rangle \langle\psi_{AB}\vert \\
&= \left( \sum_{i,j}{C_{ij}}\vert{i}_A\rangle\vert{j}_B\rangle \right) \left( \sum_{k,l}{C_{kl}^*}\langle{k}_A\vert\langle{l}_B\vert \right) \\
&= \sum_{i,j}\sum_{k,l}{C_{ij}}{C_{kl}^*} \left( \vert{i}_A\rangle \langle{k}_A\vert \right) \left( \vert{j}_B\rangle\langle{l}_B\vert \right)
\end{aligned}
$$

이 때 파동함수의 bra와 ket의 index는 다르게 구성됨에 주의하자. 
이제 여기서 A나 B의 density matrix 는 어떻게 구하는가? 이 때 사용되는
정의가 바로 **환산 밀도 행렬 (Reduced Density Matrix)**이다.

{% capture notice-2 %}
**<u>DEFINITION</u>** : 전체 system 이 $\mathcal{H}_{AB}$ 으로 이루어진 Hilbert space 에서 
전체 system 의 density matrix 에 대한
**Reduced Density Matrix** $\rho_A$, $\rho_B$는 

$$
\begin{aligned}
\rho_A = {\rm Tr}_B\vert \psi_{AB} \rangle \langle \psi_{AB} \vert \\
\rho_B = {\rm Tr}_A\vert \psi_{AB} \rangle \langle \psi_{AB} \vert
\end{aligned}
$$

여기서 Tr은 **대각합 (Trace, 트레이스)**이다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

식을 간단하게 해석해보면, $\rho_A$는 density matrix에서 B의 대각 성분을 모두 합하고 남은 것들, 즉 A만을 의미한다. 

앞에서 주어진 density matrix $\rho_{AB}$로 A에 대한 reduced density matrix를 구해보도록 하자.

$$
\begin{aligned}
\rho_{\rm A} &= {\rm Tr}_{\rm B} \rho_{\rm AB} \\
&= {\rm Tr}_{\rm B} \left( \sum_{i,j}{C_{ij}}\vert{i}_{\rm A}\rangle\vert{j}_B\rangle \right) \left( \sum_{k,l}{C_{kl}^*}\langle{k}_A\vert\langle{l}_B\vert \right) \\
\end{aligned}
$$

이 때 B에 대한 trace 는 아래와 같은 관계식을 만족한다.[^1]

$$
{\rm Tr}_{\rm B}(\vert{j}_{\rm B}\rangle\langle{l}_{\rm B}\vert) = \delta_{jl}
$$

그러므로 $\rho_A$는

$$
\begin{aligned}
\rho_A &= \sum_{i,j}\sum_{k,l} \delta_{jl} {C_{ij}}{C_{kl}^*} \left( \vert{i}_A\rangle\vert{j}_B\rangle \right) \left( \langle{k}_A\vert\langle{l}_B\vert \right) \\
&= \sum_{i,j}\sum_{k} {C_{ij}}{C_{kj}^*} \left( \vert{i}\rangle_A\vert{j}\rangle_B \right) \left( \langle{k}\vert_A\langle{j}\vert_B \right) \\
&= 
\end{aligned}
$$

이 때 completeness relation

$$
\sum_{j} \vert j_B \rangle \langle j_B \vert = \mathbf{I}
$$

이므로 최종적으로 A의 reduced density matrix는

$$
\rho_A = \sum_{i,j,k} {C_{ij}}{C_{kj}^*} \vert{i}_A\rangle \langle{k} \vert_A
$$

으로 결정된다. 마찬가지로 B에 대한 reduced density matrix는

$$
\rho_B = \sum_{i,j,l}{C_{ij}}{C_{il}^*}\vert{j}\rangle_B\langle{l}\vert_B
$$

## Example: Spin System
스핀계에서 다음과 같은 순수상태의 파동함수가 주어질 때 reduced density matrix 를 계산해보도록 하자. 

$$
\vert \psi \rangle = \frac{1}{2} \left( \vert \uparrow \uparrow \rangle + \vert \uparrow \downarrow \rangle + \vert \downarrow \uparrow \rangle + \vert \downarrow \downarrow \rangle \right)
$$

여기서 $\vert \uparrow \uparrow \rangle = \vert \uparrow_A \rangle \otimes \vert \uparrow_B \rangle$를 의미한다. 먼저 density matrix 는

$$
\begin{aligned}
\rho &= \vert \psi \rangle \langle \psi \vert \\
&= \frac{1}{4} \left( \vert \uparrow \uparrow \rangle + \vert \uparrow \downarrow \rangle + \vert \downarrow \uparrow \rangle + \vert \downarrow \downarrow \rangle \right) \left( \langle \uparrow \uparrow \vert + \langle \uparrow \downarrow \vert + \langle \downarrow \uparrow \vert + \langle \downarrow \downarrow \vert \right) \\
\end{aligned}
$$

으로 주어진 eigenvalue 에 대한 matrix representaion 을 통해
4x4 Matrix로 구성이 될 것이다. A에 대한 reduced density matrix를 구해보자.

$$
\begin{aligned}
\rho_A &= Tr_B\rho_{AB} \\
&= \sum_i \langle i_B \vert \rho_{AB} \vert i_B \rangle \\
&= \langle \uparrow_B \vert \rho_{AB} \vert \uparrow_B \rangle + \langle \downarrow_B \vert \rho_{AB} \vert \downarrow_B \rangle \\
&= \frac{1}{4} \left( \vert \uparrow \rangle + \vert \downarrow \rangle \right) \left( \langle \uparrow \vert + \langle \downarrow \vert \right) + \frac{1}{4} \left( \vert \uparrow \rangle + \vert \downarrow \rangle \right) \left( \langle \uparrow \vert + \langle \downarrow \vert \right)
\end{aligned}
$$

B에 대한 reduced density matrix도 계산해보면

$$
\begin{aligned}
\rho_B &= Tr_B\rho_{AB} \\
&= \sum_i \langle i_A \vert \rho_{AB} \vert i_A \rangle \\
&= \langle \uparrow_A \vert \rho_{AB} \vert \uparrow_A \rangle + \langle \downarrow_A \vert \rho_{AB} \vert \downarrow_A \rangle \\
&= \frac{1}{4} \left( \vert \uparrow \rangle + \vert \downarrow \rangle \right) \left( \langle \uparrow \vert + \langle \downarrow \vert \right) + \frac{1}{4} \left( \vert \uparrow \rangle + \vert \downarrow \rangle \right) \left( \langle \uparrow \vert + \langle \downarrow \vert \right)
\end{aligned}
$$

으로 A와 B에 대한 reduced denstiy matrix를 구했다. 지금과 같은 상황에서는 두 공간이 다르지만 동일한 식을 구성하는 모습을 보인다.

[^1]: 이 식에 대해서는 J.J. Sakurai, Jim Napolitano, 'Modern Quantum Mechanics', 1.5 Change of Basis - Transformation Matrix 을 참조할 것.