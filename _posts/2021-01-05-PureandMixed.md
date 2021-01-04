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

이번 게시글은 상태의 구분을 위해 만들어진 개념들이다.

## 순수 상태 (Pure State)
정의부터 알아보고 가자.

**DEFINITION**: 어떤 양자계에서 파동함수가 중첩되어 있을 때, 각 파동함수를 구별할 수 있다면 이를 **Pure State**라고 한다. 다시말해,
$$
\vert \psi \rangle = \sum_i a_i\vert \phi \rangle_i
$$
여기서 $a_i$는 i번째 확률 진폭(Probability Amplitude), $\vert \phi \rangle_i$는 i번째 직교 규격화된 파동함수이다.
{: .notice--info}

다시 말해서 순수 상태는 중첩되어 있지만 각 직교 규격화된 ket과 그것의 확률을 알 수 있는 상황을 말한다. 

## 혼합 상태 (Mixed State)
혼합 상태는 순수 상태와 반대의 개념이라고 생각하면 된다. 

**DEFINITION**: 어떤 양자계에서 파동함수가 중첩되어 있을 때, 각 파동함수를 구별할 수 없고 여러 Pure State가 섞인 경우
이를 **Mixed State**라고 한다. 이 경우에는 앞과는 달리 섞여있기 때문에 파동함수의 구별이 불가능 하다.
{: .notice--info}

혼합 상태에서는 완전히 섞여있는 탓에 섞여져 있는 것의 각 파동함수를 알 수가 없다. 그렇다면, 두 상태를 이렇게만 구분하는 걸까?
그렇지 않다. 두 상태를 구분하는 방법은 바로 **밀도행렬**을 이용하면 구별할 수 있다.

## 밀도 행렬 (Density Matrix)
밀도 행렬은 다음과 같이 정의된다.

**DEFINITION**: 유한 차원 함수 공간에서 **Denstiy Matrix**는
$$
\rho = \vert \psi \rangle \langle \psi \vert = \sum_i a_ia_i^*\vert\phi\rangle \langle\phi\vert
$$
{: .notice--info}

하지만 이 정의로는 Pure State와 Mixed State에서 Density Operator[^1]로 구분하기는 어렵다. 그러므로 여기에 더해 A와 B라는 서로 다른 힐베르트 공간(Hilbert Space)에서 다루어야 한다. 다시말해,

$$
\mathcal{H}_A\otimes\mathcal{H}_B
$$
를 생각해보자.

[^1]: Density Matrix가 연산자의 역할을 수행하기 때문에 연산자로 부르기도 한다.