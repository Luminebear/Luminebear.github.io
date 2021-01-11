---
title: "얽혀있는 공간의 밀도 행렬"
tags: [Phyiscs, QuantumMechanics, QuantumInformation, 물리학, 양자역학, 양자정보] # 태그 입력
categories: Physics
mathjax: true # MathJax 사용을 위한 태그
image:
  path: /_images/abstract-3.jpg
  feature: abstract-3.jpg
comments: true
published: true
toc: true
toc_sticky: true
---
**경고**: 아직 완성되지 않은 게시글입니다.
{: .notice--warning}

앞의 게시글에서는 Pure State와 Mixed State가 어떤 차이가 있는 지 알아보았다. 이번에는 Pure State에서 기술하되, 
A와 B라는 서로 다른 힐베르트 공간(Hilbert Space)이 존재하고, 이것의 텐서곱으로 이루어져 있을 때, Density Matrix가 어떻게 나타나는지 살펴보고자 한다. 먼저 주어진 조건의 Hilbert Space를

$$
\mathcal{H}_{AB} = \mathcal{H}_A\otimes\mathcal{H}_B
$$

으로 기술할 수 있다. 그리고 이와 같은 경우에는 A공간과 B공간의 Unit Vector로 얽혀있는 파동함수는,

$$
\vert\psi\rangle_{AB} = \sum_{i,j}{C_{ij}}\vert{i}\rangle_A\vert{j}\rangle_B
$$

이다. 이를 Pure State의 Density Matrix의 정의에 따라 적어보면,

$$
\begin{aligned}
\rho_{AB} &= \vert\psi\rangle_{AB} \langle\psi\vert_{AB} \\
&= \left( \sum_{i,j}{C_{ij}}\vert{i}\rangle_A\vert{j}\rangle_B \right) \left( \sum_{k,l}{C_{kl}^*}\langle{k}\vert_A\langle{l}\vert_B \right) \\
&= \sum_{i,j}\sum_{k,l}{C_{ij}}{C_{kl}^*} \left( \vert{i}\rangle_A \langle{k}\vert_A \right) \left( \vert{j}\rangle_B\langle{l}\vert_B \right)
\end{aligned}
$$

이 때 파동함수의 Bra와 ket의 index는 다르게 구성됨에 주의하자. 이제 여기서 A나 B의 Density Matrix는 어떻게 구하는가? 이 때 사용되는
정의가 바로 **환산 밀도 행렬 (Reduced Density Matrix)**이다.

{% capture notice-2 %}
<span style = "font-size:16pt">**<u>DEFINITION</u>**</span>
: 두 Hilbert Space $\mathcal{H}_A$와 $\mathcal{H}_B$로 이루어진 공간에서 얽혀진 Density Matrix의 
**Reduced Density Matrix** $\rho_A$, $\rho_B$는 

$$
\begin{aligned}
\rho_A = Tr_B\vert \psi \rangle_{AB} \langle \psi \vert_{AB} \\
\rho_B = Tr_A\vert \psi \rangle_{AB} \langle \psi \vert_{AB}
\end{aligned}
$$

여기서 Tr은 **대각합 (Trace, 트레이스)**이다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

식을 간단하게 해석해보면, $\rho_A$는 Density Matrix에서 B의 대각 성분을 모두 합하고 남은 것들, 즉 A만을 의미한다. 이제 앞에서 주어진 Density Matrix $\rho_{AB}$로 A에 대한 Reduced Density Matrix를 구해보도록 하자.

$$
\begin{aligned}
\rho_A &= Tr_B \rho_{AB} \\
&= Tr_B \left( \sum_{i,j}{C_{ij}}\vert{i}\rangle_A\vert{j}\rangle_B \right) \left( \sum_{k,l}{C_{kl}^*}\langle{k}\vert_A\langle{l}\vert_B \right) \\
\end{aligned}
$$

이 때 B에 대한 Trace는 아래와 같은 관계식을 만족한다.[^1]

$$
Tr_B(\vert{j}\rangle_B\langle{l}\vert_B) = \delta_{jl}
$$

그러므로 $\rho_A$는

$$
\begin{aligned}
\rho_A &= \sum_{i,j}\sum_{k,l} \delta_{jl} {C_{ij}}{C_{kl}^*} \left( \vert{i}\rangle_A\vert{j}\rangle_B \right) \left( \langle{k}\vert_A\langle{l}\vert_B \right) \\
&= \sum_{i,j}\sum_{k} {C_{ij}}{C_{kj}^*} \left( \vert{i}\rangle_A\vert{j}\rangle_B \right) \left( \langle{k}\vert_A\langle{j}\vert_B \right)
\end{aligned}
$$

이 때 여기서 Completeness Relation

$$
\sum_{j} = \vert j \rangle \langle j \vert_B = \mathbf{I}
$$

을 만족하기 때문에 최종적으로 A의 Reduced Density Matrix는

$$
\rho_A = \sum_{i,k}{C_{i}}{C_{k}^*}\vert{i}\rangle_A\langle{k}\vert_A
$$

으로 결정된다. 마찬가지로 B에 대한 Reduced Density Matrix는

$$
\rho_B = \sum_{j,l}{C_{j}}{C_{l}^*}\vert{j}\rangle_B\langle{l}\vert_B
$$

[^1] J.J. Sakurai, Jim Napolitano, 'Modern Quantum Mechanics', 1.5 Change of Basis - Transformation Matrix 참조.