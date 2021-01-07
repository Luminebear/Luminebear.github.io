---
title: "순수 상태와 혼합 상태"
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
우리가 살고있는 지구에서 대기는 질소(78%), 산소(21%), 아르곤(0.93%), 이산화 탄소(0.04%)로 이루어져 있다고 알려져 있다. 
이처럼 지구의 대기는 인간이 숨을 들이내쉬어 생명활동을 하는 산소로만 이루져 있지 않다. 이와 같이 양자계에서도 하나의 물질이 아닌
섞여있는 상태로 이루어져 있거나, 또는 하나의 물질로만 이루어진 순수한 상태를 생각해볼 수 있다. 이 게시글에서는 양자역학에서 구분하는
**순수 상태**와 **혼합 상태**를 알아보자 한다.

## 순수 상태 (Pure State)
정의부터 알아보고 가자.

{% capture notice-2 %}
**DEFINITION**: 어떤 양자계에서 파동함수가 중첩되어 있을 때, 각 파동함수를 구별할 수 있다면 이를 **Pure State**라고 한다. 다시말해,

$$
\vert \psi \rangle = \sum_i a_i\vert \phi_i \rangle
$$

여기서 $a_i$는 i번째 확률 진폭(Probability Amplitude), $\vert \phi \rangle_i$는 i번째 직교 규격화된 파동함수이다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

다시 말해서 순수 상태는 중첩되어 있지만 각 직교 규격화된 Base ket과 그것의 확률을 알 수 있는 상황을 말한다. 

## 혼합 상태 (Mixed State)
혼합 상태는 순수 상태와 반대의 개념이라고 생각하면 된다. 

{% capture notice-2 %}
<u>**DEFINITION**</u>: 어떤 양자계에서 파동함수가 중첩되어 있을 때, 각 파동함수를 구별할 수 없고 여러 Pure State가 섞인 경우
이를 **Mixed State**라고 한다. 이 경우에는 앞과는 달리 섞여있기 때문에 개별 파동함수의 구별이 불가능 하다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

혼합 상태에서는 완전히 섞여있는 탓에 섞여져 있는 것의 각 파동함수를 알 수가 없다. 그렇다면, 두 상태를 이렇게만 구분하는 걸까?
그렇지 않다. 두 상태를 구분하는 방법은 바로 **밀도행렬**을 이용하면 구별할 수 있다.

## 밀도 행렬 (Density Matrix)
밀도 행렬은 다음과 같이 정의된다.

{% capture notice-2 %}
<u>**DEFINITION**</u>: 유한 차원 함수 공간에서 **Denstiy Matrix**는

$$
\rho = \vert \psi \rangle \langle \psi \vert = \sum_i a_ia_i^*\vert\phi_i\rangle \langle\phi_i\vert
$$

{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

여기서 밀도 행렬은 어떤 Base Ket이 주어지면 밀도 행렬의 공간으로 투영(Projection)해주는 연산자의 역할도 수행한다. 다시말해,

$$
\left( \vert \psi \rangle \langle \psi \vert \right) \cdot \vert \phi \rangle = \vert \psi \rangle \cdot \left( \langle \psi \vert \phi \rangle \right) = a_\psi \vert \psi \rangle
$$

이제 Pure State와 Mixed State의 차이를 살펴보자. Pure State와 Mixed State를 구분하는 방법은 바로 **대각합(Trace, 트레이스)**를 이용한다.
먼저 Pure State에서는 파동함수를 구별할 수 있다고 언급하였다. 여기서 중요한 성질이 하나 있는데 Pure State에서,

$$
\rho^2 = \rho
$$

이것은 간단하게 보일 수 있다.

$$
\begin{aligned}
\rho^2 = \vert \psi \rangle \langle \psi \vert \psi \rangle \langle \psi \vert = \vert \psi \rangle \langle \psi \vert
\end{aligned}
$$

따라서 Pure State의 Density Matrix의 Trace를 구해보자.

$$
\begin{aligned}
Tr\rho &= Tr\rho^2 \\
&= \sum_i \langle \phi_i \vert \rho \vert \phi_i \rangle \\
&= \sum_i \langle \phi_i \vert \psi \rangle \langle \psi \vert \phi_i \rangle \\
&= \sum_i a_ia_i^* = \sum_i p_i = 1
\end{aligned}
$$

그러므로 Pure State의 모든 확률의 합은 1로 나타난다. 다음으로 Mixed State의 Density Matrix의 Trace를 구해보자. 이 때 Mixed State의 Density Matrix는 각 Pure State의 Density Matrix의 합

$$
\rho = \sum_i p_i\rho_i
$$

으로 표현된다. 여기서 구분되는 점은 Pure State와 달리

$$
\rho \neq \rho^2
$$

이라는 사실이다. 간단하게 살펴보면, 앞의 Pure State와 같이 전체 확률을 1로 둘 때 $Tr\rho = 1$이 되는 것은 당연하다. 하지만 $\rho^2$의 경우,

$$
\begin{aligned}
\rho^2 &= \left( \sum_ip_i\rho_i \right) \left( \sum_ip_i\rho_i \right) \\
&\neq \left( \sum_i \langle \phi_i \vert \rho \vert \phi_i \rangle \right)\left( \sum_i \langle \phi_i \vert \rho \vert \phi_i \rangle \right)
\end{aligned}
$$

정의를 다시 생각해보면, 당연히 성립이 되지 않는다. 왜냐하면 우리는 Mixed State에서 정확한 파동함수를 알 수 없다고 했기 때문이다. 따라서 Mixed State의 $Tr\rho^2$은

$$
Tr\rho^2 = \sum_ip_i^2 < 1
$$

으로 나타난다. 이제 Pure State와 Mixed State의 등식을 정리하자.

{% capture notice-2 %}
<u>**THEOREM**</u>: **Pure State**에서 Density Matrix의 Trace는

$$
Tr \rho^2 = Tr \rho = 1
$$

**Mixed State**에서 Denstiy Matrix의 Trace는

$$
Tr \rho^2 < 1
$$

{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

[^1]: Density Matrix가 연산자의 역할을 수행하기 때문에 연산자로 부르기도 한다.