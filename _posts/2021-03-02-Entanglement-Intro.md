---
title: "양자 얽힘: 분리 가능과 얽힘"
tags: [Phyiscs, QuantumMechanics, qi, 물리학, 양자역학, 양자정보] # 태그 입력
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

**양자 얽힘(Quantum Entanglement)**은 양자역학에서만 나타나는 기이한 현상으로, 단순하게는 어떤 한 쌍의 무언가가
서로 영향을 끼치며 연관되어 있는(correlated) 상황을 의미한다. 얼핏 들으면 기존의 연관되는 무언가들 (이를테면
단순히 수요와 공급간 관계라든지.)과 다른것이 있을 까 싶지만, 양자 얽힘은 이러한 현상을 넘어 고전적으로는
설명할 수 없는 현상이 나타난다. 예를들어 한 입자가 두개의 상태로 중첩되어 있고 얽혀있다고 하면,
어떤 현상이 발생하여 분리되거나 영향을 끼칠 때, 동시에 물리적 현상이 미치고 하나의 상태로 결정이 되는 등,
그리고 양자적 특징을 잃어버리는 등의 현상이 나타난다. 이러한 경우, 각 입자들은 독립적인 상호작용이 불가능하다. 

또한, 이 현상은 아직 제대로 밝혀지진 않았으나, 거리에 상관없이, 광속을 고려하지 않고 '동시에' 전달 되는 현상이
나타난다. 다시말해, 어떤 정보를 전송할 때는 반드시 시간이 걸리긴 마련인데, 그러한 점을 무시하고, 얽혀있던 상태가
한 사람의 결정으로 인해, 다른 사람의 상태가 결정이 되는, 기이한 현상이 나타난다. 말로만 들으면 이게 가능할까?
싶지만, 물리학은 수식 도구를 이용하여 기술할 수 있으므로, 어떻게 나타날 수 있는 지 살펴보도록 하자.

## 큐비트 (Qubit)
[엔트로피와 정보이론](/physics/Information-Theory/#섀넌-엔트로피-shannon-entropy) 게시글에서 Shannon entropy 식은
정보 엔트로피라는 물리량을 주고, 이것의 단위가 바로 **비트(Bit)**였다. 식에 따르면, 사실 우리가 사용하고 있는
비트는 주어진 system 의 평균 정보량이 최대가 되는 경우를 생각하고, 0과 1, 두 숫자로 나눈 것이다. 또한 비트가 차지하는
system 은 1차원의 공간으로, 하나의 선에서, 0과 1로 줄지을 수 있다. 여기서 1차원을 추가하여, 2차원의 공간으로
system 이 구성되면, 이것이 바로 **큐비트(Qubit)**가 된다.

{% capture notice-2 %}
**<u>DEFINITION</u>** : 양자 정보를 싣고 나르는 기본계가 2차원인 것을 
**큐비트(Qubit)** 이라고 한다.
{% endcapture %}
<div class="notice--info">{{ notice-2 | markdownify }}</div>

고전 정보량의 단위인 비트에서 '1과 0'을 '불빛의 켬과 끔'으로 표현하듯이, 큐비트에서도 이러한 것을 적용할 수 있다.
대표적으로 다음과 같은 예시가 있다.

1. 서로 수직하는 광선을 통과시키는 편광축 - 수평: $\vert \leftrightarrow \rangle$ 수직: $\vert \updownarrow \rangle$
2. 전자의 스핀 - 스핀업: $\vert \uparrow \rangle$, 스핀다운: $\vert \downarrow \rangle$
3. 원자의 에너지 준위 - 들뜬상태: $\vert e \rangle$, 바닥상태:$\vert g \rangle$[^1]

세 경우 모두 두 가지로 상황을 나누어 생각하지만, 비트와는 다르게 **Ket** $'\vert \quad \rangle\text'$을 이용하여
나타낸다. 이것을 제대로 이해하기 위해서는 선형대수적 배경이 필요하다. 방향을 가지는 2차원의 수이기 때문인데,
간단하게 다음과 같이 생각할 수 있다.

$$
\vert \leftrightarrow \rangle = \begin{pmatrix} 1 \\ 0 \end{pmatrix} \qquad
\vert \updownarrow \rangle = \begin{pmatrix} 0 \\ 1 \end{pmatrix}
$$

그리고 큐비트는 광자를 가지고 살펴보기 좋아서, 양자 광학 분야에서 특히 발달이 되어 있고, 실험적으로도
알려진 현상들이 많다. 또한 이러한 기초적인 양들은 서로 수직하고 규격화된, **'직교 규격화된 기저(orthonormal basis)'**인데, 
이러한 특징으로 새로운 기저를 세울 수 있는 등의 특징을 가지고 있다.
이를테면, 첫 번째 경우에 대한 새로운 basis 를 다음과 같이

$$
\begin{aligned}
\vert + \rangle = \frac{1}{\sqrt{2}} \left( \vert \leftrightarrow \rangle + \vert \updownarrow \rangle \right) \qquad
\vert - \rangle = \frac{1}{\sqrt{2}} \left( \vert \leftrightarrow \rangle - \vert \updownarrow \rangle \right)
\end{aligned}
$$

으로 하는 큐비트계를 만들 수도 있는 것이다.

## 양자 얽힘 (Quantum Entanglement)
이제 양자 정보를 기술하는 큐비트를 알았으니 이를 바탕으로 양자 얽힘 현상을 알아보도록 하자.
우리는 여러 큐비트를 기술하는 계 중 Spin-1/2 system 을 선택하여 살펴볼 것이다. 여기서 얽힘
현상을 기술하기 위해, 아래와 같이 두 개의 subsystem 으로 구성되는 Hilbert space 를 먼저
구성하도록 한다.

$$
\mathcal{H}_{\rm AB} = \mathcal{H}_{\rm A} \otimes \mathcal{H}_{\rm B}
$$

Spin-1/2 system 을 선택했기 때문에, 각 subsystem 에 대한 모든 상태를 다음과 같이 기술할 수 있다.

$$
\vert \uparrow \rangle_{\rm A} \quad \vert \downarrow \rangle_{\rm A} \qquad
\vert \uparrow \rangle_{\rm B} \quad \vert \downarrow \rangle_{\rm B}
$$

두 subsystem 이 얽혀진 상태를 아래와 같은 축약된 형태

$$
\vert \uparrow \uparrow \rangle = \vert \uparrow_{\rm A} \rangle \otimes
\vert \uparrow_{\rm B} \rangle
$$

으로 기술하면, 모든 가능한 상태는 다음과 같이 기술할 수 있다.

$$
\vert \psi_{\rm AB} \rangle = a\vert \uparrow \uparrow \rangle + b\vert \uparrow \downarrow \rangle + c\vert \downarrow \uparrow \rangle + d\vert \downarrow \downarrow \rangle
$$

이 때 a,b,c,d 는 복소수이고, 코펜하겐 해석에 따라 전체 확률이 1로 만족하기 위해, $\vert a \vert^2 + \vert b \vert^2 + \vert c \vert^2 + \vert d \vert^2 = 1$이다.
이 때 이 식을 특별히 두 상태로 나누어보면,

$$
\begin{aligned}
\vert \Psi_{\rm AB} \rangle &= b\vert \uparrow \downarrow \rangle + c\vert \downarrow \uparrow \rangle \\
\vert \Phi_{\rm AB} \rangle &= a\vert \uparrow \uparrow \rangle + d\vert \downarrow \downarrow \rangle
\end{aligned}
$$

첫 번째 상태 $\vert \Psi_{\rm AB} \rangle$의 경우 각 상태가 서로 반대로 얽혀 있으므로, '반상관관계(anticorrelation)'이며, 
두 번째 상태 $\vert \Phi_{\rm AB} \rangle$의 경우 각 상태가 같은 상태로 얽혀 있으므로,
'상관관계(correlation)'에 있다고 한다. 또한 이 두 상태는 서로 분리되지 않는 **얽혀있는**
상태이다. 

설명을 위해 $\vert \Psi \rangle_{\rm AB}$를 살펴보면, 우리가 A에 대해 spin-up 을 측정하면,
B는 spin-down 으로 결정된다. 반대로 A에 대해 spin-down 을 측정하면, B는 spin-up 으로 결정된다. 하지만,
A가 spin-up 으로 측정이 될지, spin-down 으로 측정이 될지는 알 수 없으며, 단지 그 확률이 
$\vert a \vert^2 \,, \vert b \vert^2$ 이다.

## 분리 가능 상태 (Seperable State)
**'곱 상태 (Product State)'**라고 하는 이 상태는 단순히 두 subsystem 이 독립적으로만
구성되어 있는 것이다. 위와 같은 상태에서 개별 system 의 spin-up, spin-down 이 단독적으로 행동하며,
식으로는 다음과 같이 나타낼 수 있다.

$$
\vert \phi_{AB} \rangle = \left( \alpha \vert \uparrow_{\rm A} \rangle + \beta \vert \downarrow_{\rm A} \rangle \right)
\otimes \left( \gamma \vert \uparrow_{\rm B} \rangle + \delta \vert \downarrow_{\rm B} \rangle \right)
$$

다시말해, A, B 가 서로 상관관계 없이, A의 up-spin 과 down-spin 의 확률이 각각 $\vert \alpha \vert^2 \,, \vert \beta \vert^2$ 이며, B의 spin-up 과 spin-down 의 확률이 각각 $\vert \gamma \vert^2 \,, \vert \delta \vert^2$ 이다. 

## 일반화
순수 상태(pure state)인 경우에서 얽힘 상태를 일반화 하면 아래와 같다.

$$
\vert\psi_{\rm AB}\rangle = \sum_{i,j}{C_{ij}}\vert{i}_A\rangle\vert{j}_B\rangle
$$

물론 규격화 조건 $\sum_{i,j}{\vert C_{ij} \vert}^2=1$를 만족하며, $\vert{i}\_A\rangle, \vert{j}\_B\rangle$ 
는 orthonormal basis 이다. 여기서 특별히, 모든 복소수 계수 $C\_{i,j}$가 $C\_{i,j} = a\_{i}b\_{j}$를 만족하면,
분리 가능 상태의 일반화된 식이 된다. 다시말해,

$$
\vert\psi_{\rm AB}\rangle = \sum_{i}{a_i}\vert{i}_A\rangle \sum_{j}{b_j}\vert{j}_B\rangle
= \vert \psi_{\rm A} \rangle \vert \psi_{\rm B} \rangle
$$

를 만족하는 경우, 분리 가능 상태가 된다.

## References
* 이해웅, 양자 정보학 강의, 1장 및 3장
* 그 외 논문이나 기타 자료로 접한 것들 (특정지을 수 없음)

[^1]: e: excited state, g: ground state