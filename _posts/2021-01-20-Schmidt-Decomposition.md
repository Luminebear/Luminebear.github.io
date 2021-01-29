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
이를 구하는 방법은 이전의 게시글 '[얽혀있는 공간의 밀도 행렬](/physics/ReducedMatrix)'에서 Reduced Density Matrix로부터 계산되며, 이 행렬을 [행렬 고윳값 분해(대각화)](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix)를 통해 Eigenvalue, Eigenvector를 구함으로 얻어진다.
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
\rho_A = \sum_{\{i,k\}=0}^{1}\vert{i}_A\rangle X^{-1}XUX^{-1}X \langle{k}_A \vert
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
\begin{aligned}
\rho_A &= \vert{0}_A\rangle X^{-1}XUX^{-1}X \langle{0}_A \vert + \vert{0}_A\rangle X^{-1}XUX^{-1}X \langle{1}_A \vert \\
&+ \vert{1}_A\rangle X^{-1}XUX^{-1}X \langle{0}_A \vert + \vert{1}_A\rangle X^{-1}XUX^{-1}X \langle{1}_A \vert \\
&= \lambda_1\vert{+}_A\rangle \langle{+}_A\vert + \lambda_2\vert{-}_A\rangle \langle{-}_A\vert
\end{aligned}
$$

마찬가지로 B에 대한 Reduced Density Matrix도 동일하게 계산이 될 것이다. 그러면 다시 우리가 생각한 Pure State의 파동함수 $\psi_{AB}$를 새로운 Basis에 대한 것으로 쓸 수 있다.

$$
\begin{aligned}
\vert\psi_{AB}\rangle &= \sum_{i,j}{C_{ij}}\vert{i}_A\rangle\vert{j}_B\rangle \\
&= \sqrt{\lambda_1}\vert{+}_A\rangle\vert{+}_B\rangle + \sqrt{\lambda_2}\vert{-}_A\rangle\vert{-}_B\rangle
\end{aligned}
$$

## 폰 노이만 엔트로피와 Concurrence
사실은 폰 노이만 엔트로피를 계산하는 방법이 위와 동일하다. 폰 노이만 엔트로피는 섀넌 엔트로피와 대치할 때, 다음과 같은 조건을 만족하는 경우 순수 상태에 있는 두 시스템은 얽혀있다고 간주한다.

{% capture notice-2 %}
**<u>DEFINITION</u>** : 두 Hilbert Space $\mathcal{H}_A$와 $\mathcal{H}_B$로 이루어진 공간에서 얽혀진 
공간에서 임의의 파동함수 $\vert \psi_{AB} \rangle$에 대한 **얽힘의 정도 $E_{AB}$**는

$$
E_{AB} = S[\rho_{A}] = S[\rho_{B}]
$$

여기서 $S$는 von Neumann Entropy

$$
S[\rho] = -Tr[\rho\ln\rho]
$$
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

정의상으로 보면 어느 부분에서 일치할까 싶지만, 사실은 밀도행렬에서 Trace를 만족하기 위해 행렬 고윳값 분해 과정이 필요하게 된다. 
먼저 얽혀있는 파동함수의 Density Matrix를 구하고, A나 B에 대한 Reduced Density Matrix를 계산한다. 
다음으로 고윳값 분해 과정을 거치게 됨으로 엔트로피의 식이 앞의 게시글 '[엔트로피와 정보이론](/physics/Information-Theory/#폰-노이만-엔트로피-von-neumann-entropy)'에서 마지막식인

$$
S = -\sum_i^n \lambda_i \ln \lambda_i
$$

으로 바뀌는 것이다.

다음으로 Concurrence[^3]라는 척도가 존재한다. 정의를 살펴보자.

{% capture notice-2 %}
**<u>DEFINITION</u>** : 두 Hilbert Space $\mathcal{H}_A$와 $\mathcal{H}_B$로 이루어진 공간에서 얽혀진 
공간에서 임의의 파동함수 $\vert \psi_{AB} \rangle$에 대한 **Concurrence**는

$$
C = \left| \langle \psi_{AB} \vert \sigma_A^y \sigma_B^y \vert \psi_{AB}^* \rangle \right|
$$

여기서 $\sigma_A^y, \sigma_B^y$는 Pauli Matrices 중 하나인

$$
\sigma^y =
\begin{pmatrix}
  0 & -i \\
  i & 0
\end{pmatrix}
$$
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

역시 정의로 바라보았을 때 명확하게 보이지 않기 때문에 앞에서 들었던 예시를 가져오자.
앞에서 A에 대한 Reduced Density Matrix의 행렬 U를

$$
U =
\begin{pmatrix}
  |a|^2 + |b|^2 & ac^{*} + bd^{*} \\
  ca^{*} + db^{*} & |c|^2 + |d|^2
\end{pmatrix}
$$

으로 나타냈다. 참고로 여기서 계수를 다음과 같이 바꾸었다.

$$
{C_{00}} = a, \qquad {C_{01}} = b, \qquad {C_{10}} = c, \qquad {C_{11}} = d
$$

행렬 고윳값 분해를 통해 특성방정식을 구해보면, 

$$
\begin{aligned}
U\lambda - I &= 0 \\
(|a|^2 + |b|^2 - \lambda)(|c|^2 + |d|^2 - \lambda) - (ac^{*} + bd^{*})(ca^{*} + db^{*}) &= 0 \\
\lambda^2 - \lambda + (bc-ad)(b^{*}c^{*}-a^{*}d^{*}) &= 0
\end{aligned}
$$

이고 이제 Eigenvalue를 구하면

$$
\begin{aligned}
\lambda_{\pm} &= \frac{1 \pm \sqrt{1 - 4 \vert bc-ad \vert^2}}{2} \\
&= \frac{1 \pm \sqrt{1 - C^2}}{2} \\
C &=  2\vert bc-ad \vert
\end{aligned}
$$

으로 구해진다. 여기서 C로 대치한 값이 바로 **Concurrence** 이다. 즉 다시 말해 행렬의 Off-Diagonal 성분이 Concurrence가 된다.

[^1]: 이 수가 상수 값인 1/2을 의미하는 것이 아님을 상기하자. 
[^2]: 이것은 Matrix Representation으로 간주할 수 있다.
[^3]: 양자 얽힘의 정도, 일치도라는 한국어의 번역이 있으나 정해진 단어는 없는 것 같아서 영문 명칭으로 표기함. [Cambridge Dictionary](https://dictionary.cambridge.org/dictionary/english/concurrence)에서는 다음으로 설명한다. 'a situation in which things or events happen or exist at the same time'