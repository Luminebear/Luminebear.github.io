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
**경고**: 아직 완성되지 않은 게시글입니다.
{: .notice--warning}

우리가 살고있는 지구에서 대기는 질소(78%), 산소(21%), 아르곤(0.93%), 이산화 탄소(0.04%)로 이루어져 있다고 알려져 있다. 
이처럼 지구의 대기는 인간이 숨을 들이내쉬어 생명활동을 하는 산소로만 이루져 있지 않다. 이와 같이 양자계에서도 하나의 물질이 아닌
섞여있는 상태로 이루어져 있거나, 또는 하나의 물질로만 이루어진 순수한 상태를 생각해볼 수 있다. 이 게시글에서는 양자역학에서 구분하는
**순수 상태**와 **혼합 상태**를 알아보자 한다.

## 순수 상태 (Pure State)
정의부터 알아보고 가자.

{% capture notice-2 %}
**DEFINITION**: 어떤 양자계에서 파동함수가 중첩되어 있을 때, 각 파동함수를 구별할 수 있다면 이를 **Pure State**라고 한다. 다시말해,

$$
\vert \psi \rangle = \sum_i a_i\vert \phi \rangle_i
$$

여기서 $a_i$는 i번째 확률 진폭(Probability Amplitude), $\vert \phi \rangle_i$는 i번째 직교 규격화된 파동함수이다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

다시 말해서 순수 상태는 중첩되어 있지만 각 직교 규격화된 ket과 그것의 확률을 알 수 있는 상황을 말한다. 

## 혼합 상태 (Mixed State)
혼합 상태는 순수 상태와 반대의 개념이라고 생각하면 된다. 

{% capture notice-2 %}
**DEFINITION**: 어떤 양자계에서 파동함수가 중첩되어 있을 때, 각 파동함수를 구별할 수 없고 여러 Pure State가 섞인 경우
이를 **Mixed State**라고 한다. 이 경우에는 앞과는 달리 섞여있기 때문에 파동함수의 구별이 불가능 하다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

혼합 상태에서는 완전히 섞여있는 탓에 섞여져 있는 것의 각 파동함수를 알 수가 없다. 그렇다면, 두 상태를 이렇게만 구분하는 걸까?
그렇지 않다. 두 상태를 구분하는 방법은 바로 **밀도행렬**을 이용하면 구별할 수 있다.

## 밀도 행렬 (Density Matrix)
밀도 행렬은 다음과 같이 정의된다.

{% capture notice-2 %}
**DEFINITION**: 유한 차원 함수 공간에서 **Denstiy Matrix**는

$$
\rho = \vert \psi \rangle \langle \psi \vert = \sum_i a_ia_i^*\vert\phi\rangle \langle\phi\vert
$$

{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

하지만 이 정의로는 Pure State와 Mixed State에서 Density Operator[^1]로 구분하기는 어렵다. 그러므로 여기에 더해 A와 B라는 서로 다른 힐베르트 공간(Hilbert Space)에서 다루어 보도록 하자. 다시말해,

$$
\mathcal{H}_{AB} = \mathcal{H}_A\otimes\mathcal{H}_B
$$

를 생각해보자. 이와 같은 경우에는 A공간과 B공간의 Unit Vector로 얽혀있는 파동함수,

$$
\vert\psi\rangle_{AB} = \sum_{i,j}{C_{ij}}\vert{i}\rangle_A\vert{j}\rangle_B
$$

이다. 이를 Density Matrix의 정의에 따라 적으면,

$$
\begin{aligned}
\rho &= \vert\psi\rangle_{AB} \langle\psi\vert_{AB} \\
&= \left( \sum_{i,j}{C_{ij}}\vert{i}\rangle_A\vert{j}\rangle_B \right) \left( \sum_{k,l}{C_{kl}^*}\langle{k}\vert_A\langle{l}\vert_B \right) \\
&= \sum_{i,j}\sum_{k,l}{C_{ij}}{C_{kl}^*} \left( \vert{i}\rangle_A \langle{k}\vert_A \right) \left( \vert{j}\rangle_B\langle{l}\vert_B \right)
\end{aligned}
$$

이 때 파동함수의 Bra와 ket의 index는 다르게 구성됨에 주의하자. 이제 여기서 A나 B의 Density Matrix는 어떻게 구하는가? 이 때 사용되는
정의가 바로 **환산 밀도 행렬 (Reduced Density Matrix)**이다.

{% capture notice-2 %}
**DEFINITION**: 두 Hilbert Space \mathcal{H}_A와 \mathcal{H}_B로 이루어진 공간에서 얽혀진 Density Matrix의 
**Reduced Density Matrix** $\rho_A$, $\rho_B$는 

$$
\begin{aligned}
\rho_A = Tr_B\vert \psi \rangle_{AB} \langle \psi \vert_{AB} \\
\rho_B = Tr_A\vert \psi \rangle_{AB} \langle \psi \vert_{AB}
\end{aligned}
$$

{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

식을 간단하게 해석해보면, $\rho_A$는 Density Matrix에서 B의 대각 성분을 모두 합하고 남은 것들[^2], 즉 A만을 의미한다.

[^1]: Density Matrix가 연산자의 역할을 수행하기 때문에 연산자로 부르기도 한다.
[^2]: 여기서 B의 off-diagonal elements는 0으로 정당화 할 수 있을까? 이것은 차후 게시물에서 참조하자.