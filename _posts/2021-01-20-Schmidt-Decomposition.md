---
title: "슈미트 분해"
tags: [Phyiscs, Information, QuantumInformation, 물리학, 정보, 양자정보] # 태그 입력
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

슈미트 분해(Schmidt Decomposition)는 양자 얽힘(Quantum Entanglement)에서 가장 중요한 수학적 기술 중 하나로, 이것을 이용하면 복잡하게 얽혀있는 Ket-Vector를 최소화된 항으로 만들어 줄 수 있다.

이 방법은 우리가 선형대수학에서 배운 ['그람-슈미트 과정(Gram-Schmidt Process)'](https://en.wikipedia.org/wiki/Gram%E2%80%93Schmidt_process)의 그 Enhard Schmidt가 제안한 방법이다. 그러면 이제 정의를 살펴보도록 하자.

## 정의
앞의 게시글과 같이 먼저 A와 B가 텐서곱으로 얽혀있는 Hilbert Space를 생각하자.

$$
\mathcal{H}_{AB} = \mathcal{H}_A\otimes\mathcal{H}_B
$$

그리고 이와 같은 경우에는 A공간과 B공간의 Unit Vector로 얽혀있는 파동함수를

$$
\vert\psi_{AB}\rangle = \sum_{i,j}{C_{ij}}\vert{i}_A\rangle\vert{j}_B\rangle
$$

으로 기술하였다. 물론 규격화 조건 $\sum_{i,j}{\vert C_{ij} \vert}^2=1$를 만족하며, 
$\vert{i}_A\rangle, \vert{j}_B\rangle$는 orthonomal condition으로 주어진다.
이것을 생각하고 슈미트 분해의 정의를 써보도록 하자.

{% capture notice-2 %}
**<u>DEFINITION</u>** : 두 Hilbert Space $\mathcal{H}_A$와 $\mathcal{H}_B$로 이루어진 공간에서 얽혀진  
공간에서 임의의 파동함수에 대한 **슈미트 분해**는

$$
\vert\psi_{AB}\rangle = \sum_{k}{\lambda_{k}}\vert{k}_A\rangle\vert{k}_B\rangle
$$

여기서 $\lambda_k$를 **슈미트 수(Schmidt Number)**라고 한다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

임의의 파동함수와 슈미트 분해식과 비교할 때 눈에 보이는 차이점은 바로 **인덱스**를 보면 알 수 있다.
슈미트 분해식을 살펴보면 합의 표현이 하나의 Dummy Index 'k'으로 나타난다. 그리고 Ket Vector 앞에 붙는 계수에 대해 특별히 Schmidt Number라고 부르는데, 이것이 중요한 역할을 한다. 예를 들어 스핀계에서 다음과 같은 순수상태의 파동함수

$$
\vert \psi \rangle = \frac{1}{2} \left( \vert \uparrow \uparrow \rangle + \vert \uparrow \downarrow \rangle + \vert \downarrow \uparrow \rangle + \vert \downarrow \downarrow \rangle \right)
$$

가 주어졌다고 하자. 이 때 주어진 파동함수의 항 $\vert \uparrow \uparrow \rangle = \vert \uparrow \rangle_A \otimes \vert \uparrow \rangle_B$ 으로 표현된 것이다. 얼핏보면 이 항들이 Schmidt Decomposition이 될 것인가 생각할 수 있다. 하지만 다음과 같이 임의의 Base Ket을 새로 잡아보자.

$$
\begin{aligned}
\vert + \rangle_A = \frac{1}{\sqrt{2}} \left( \vert \uparrow \rangle_A + \vert \downarrow \rangle_A \right) \qquad \vert - \rangle_A = \frac{1}{\sqrt{2}} \left( \vert \uparrow \rangle_A - \vert \downarrow \rangle_A \right) \\
\vert + \rangle_B = \frac{1}{\sqrt{2}} \left( \vert \uparrow \rangle_B + \vert \downarrow \rangle_B \right) \qquad \vert - \rangle_B = \frac{1}{\sqrt{2}} \left( \vert \uparrow \rangle_B - \vert \downarrow \rangle_B \right) 
\end{aligned}
$$

그러면 주어진 파동함수를 새로 만든 Base Ket으로 다음과 같이 표현할 수 있다.

$$
\begin{aligned}
\vert \psi \rangle_A = \frac{1}{2}(\vert + \rangle_A \vert + \rangle_B)
\end{aligned}
$$

앞의 정의와 같이 같은 Index로 나타내지는 것을 확인할 수 있다. 이것이 Schmidt Decomposition이며, 이 때 Schmidt Number는 1이 된다.[^1]

## 일반적인 경우
앞에서 $\vert\psi_{AB}\rangle$와 같은 상태에 있는 일반적인 경우에 Schmidt Decomposition을 어떻게 기술할 수 있을까? 
이를 구하는 방법은 이전의 게시글 '[얽혀있는 공간의 밀도 행렬](/_posts/2021-01-07-ReducedMatrix.md)'에서 Reduced Density Matrix로부터 계산되며, 이 행렬을 [행렬 고윳값 분해(대각화)](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix)를 통해 Eigenvalue, Eigenvector를 구함으로 얻어진다.
그 과정을 살펴보도록 하자. 먼저 Reduced Density Matrix는 밀도 행렬 $\rho_{AB}$에 대해

$$
\begin{aligned}
\rho_A = Tr_B\vert \psi_{AB} \rangle \langle \psi_{AB} \vert \qquad
\rho_B = Tr_A\vert \psi_{AB} \rangle \langle \psi_{AB} \vert
\end{aligned}
$$

으로 썼다. 그리고 Trace의 성질로 인해 A에 대한 Reduced Density Matrix는

$$
\rho_A = \sum_{i,j,k} {C_{ij}}{C_{kj}^*} \vert{i}_A\rangle \langle{k}_A \vert
$$

이였다. 여기서 i,j,k가 0부터 1까지인 경우만을 생각해보자. $\rho_A$를 전체 전개하면

$$
\begin{aligned}
\rho_A &= {C_{00}}{C_{00}^*} \vert{0}_A\rangle \langle{0}_A \vert
+ {C_{01}}{C_{01}^*} \vert{0}_A\rangle \langle{0}_A \vert \\
&+ {C_{00}}{C_{10}^*} \vert{0}_A\rangle \langle{1}_A \vert
+ {C_{01}}{C_{11}^*} \vert{0}_A\rangle \langle{1}_A \vert \\
&+ {C_{10}}{C_{00}^*} \vert{1}_A\rangle \langle{0}_A \vert
+ {C_{10}}{C_{01}^*} \vert{1}_A\rangle \langle{0}_A \vert \\
&+ {C_{10}}{C_{10}^*} \vert{1}_A\rangle \langle{1}_A \vert
+ {C_{11}}{C_{11}^*} \vert{1}_A\rangle \langle{1}_A \vert \\
\end{aligned}
$$

상수들을 행렬로 묶으면 다음과 같은 형태가 된다.[^2] 이것을 행렬 U라고 부르자.

$$
U =
\begin{pmatrix}
  |{C_{00}}|^2 + |{C_{01}}|^2 & C_{00}C^{*}_{10} + C_{01}C^{*}_{11} \\
  C_{10}C^{*}_{00} + C_{11}C^{*}_{01} & |{C_{10}}|^2 + |{C_{11}}|^2
\end{pmatrix}
$$

특성방정식을 통해서 우리는 Eigenvalue $\lambda$를 구할 수 있으며, 이에 대응 하는 Normalized Eigenvector와 이로 구성된 행렬 X

$$
\mathbf{x_1} = \left( x_{11}, x_{12} \right) \qquad
\mathbf{x_2} = \left( x_{21}, x_{22} \right)
$$
$$
X = 
\begin{pmatrix}
  x_{11} & x_{12} \\
  x_{21} & x_{22}
\end{pmatrix}
$$

으로 대각화가 이루어진다.

$$
XUX^{-1} = 
\begin{pmatrix}
  \lambda_1 & 0 \\
  0 & \lambda_2 
\end{pmatrix}
$$

이 식을 이용하여 $\rho_A$를 다시 써보면

$$
\rho_A = \sum_{\{i,k\}=1}^{2}\vert{i}_A\rangle X^{-1}XUX^{-1}X \langle{k}_A \vert
$$

으로 쓸 수 있고, 이 때 행렬 X를 Transformation Matrix로 간주하면, 다시말해

$$
\vert{j}_A\rangle = X\vert{i}_A\rangle
$$

임을 생각하고 현재의 경우에 대해 적용을 하면,

$$
\begin{pmatrix}
  \vert{+}_A\rangle \\
  \vert{-}_A\rangle 
\end{pmatrix}
=
\begin{pmatrix}
  x_{11} & x_{12} \\
  x_{21} & x_{22}
\end{pmatrix}
\begin{pmatrix}
  \vert{0}_A\rangle \\
  \vert{1}_A\rangle 
\end{pmatrix}
$$

이며 따라서 Reduced Density Matrix $\rho_A$를 다음으로 바꿔쓸 수 있다.

$$
\rho_A = \lambda_1\vert{+}_A\rangle \langle{+}_A\vert + \lambda_2\vert{-}_A\rangle \langle{-}_A\vert 
$$

마찬가지로 B에 대한 Reduced Density Matrix도 동일하게 계산이 될 것이다. 그러면 다시 우리가 생각한 Pure State의 파동함수 $\psi_{AB}$를 새로운 Basis에 대한 것으로 쓸 수 있다.

$$
\begin{aligned}
\vert\psi_{AB}\rangle &= \sum_{i,j}{C_{ij}}\vert{i}_A\rangle\vert{j}_B\rangle \\
&= \sqrt{\lambda_1}\vert{+}_A\rangle\vert{+}_B\rangle + \sqrt{\lambda_2}\vert{-}_A\rangle\vert{-}_B\rangle
\end{aligned}
$$

## 폰 노이만 엔트로피와 Concurrence

[^1]: 이 수가 상수 값인 1/2을 의미하는 것이 아님을 상기하자. 
[^2]: 이것은 Matrix Representation으로 간주할 수 있다.