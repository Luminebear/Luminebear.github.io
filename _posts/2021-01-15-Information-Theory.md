---
title: "엔트로피와 정보 이론"
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

이 게시글에서는 양자 정보를 배우기 앞서 통계역학적으로 필요한 개념들을 소개한다. 많은 내용을 함축적으로 담았기 때문에 양자 정보에 대해 어떤 흐름으로 가게 되는지 살펴보는 정도로 알아본다.

## 맥스웰의 악마 (Maxwell's Demon)
James Clerk Maxwell은 '맥스웰의 악마(Maxwell's Demon)'이라는 사고실험을 하나 만들었다. 그 과정은 다음과 같다.

----

1. 바깥과 에너지 교환이 없는 계를 하나 생각하자. 이 공간에는 균일하게 기체인 입자들이 존재한다.
2. 그 공간을 정확히 절반으로 나누되, 출입할 수 있는 문 같은 것이 있다고 하자.
3. 이제 '악마(Demon)'라는 존재가 있다고 가정하자. 이 존재는 앞서 언급한 문을 이리저리 여닫을 수 있다.
4. 악마는 조건이 주어짐에 따라 문을 여닫을 수 있다. 예를 들어, 두 개로 나누어진 공간에 기체를 0.3, 0.7의 비율로 나누거나, 만약 두 종류의 기체로 섞여있을 경우,
이리저리 문을 여닫으며 출입하는 입자를 조절한다.

----

여기서 주요하게 볼 문제점은 '악마가 조건이 주어짐에 따라 행동하는 것'이다. 물론 예시로 든 경우들이 물리적으로 말도 안되지만, 악마는 이러한 조건을 '어디선가 받아 알고 있어야 한다.'
즉, 이 과정에서 악마는 **'조건'이라는 정보**를 가지고 행동을 취한다고 말할 수 있다. 

## 열역학적 엔트로피 (Thermodynamic Entropy)
양자 정보에서 주로 사용하는 **폰 노이만 엔트로피(von Neumann Entropy)**를 보기 앞서 어떻게 발전해왔는지 짧게 살펴보도록 하자. 

### 열역학 1법칙의 또다른 표현
먼저 우리는 열역학 제 1법칙인 에너지 보존식을 다음과 같이 기술한다.

$$
dU = \delta{Q} + \delta{W}
$$

여기서 $\delta$는 불완전미분을 말한다. 클라우지우스 원리로부터 엔트로피 변화는 다음과 같이 정의되었다.

$$
dS = \frac{\delta{Q_{rev}}}{T} \geq \frac{\delta{Q}}{T} 
$$

여기서 rev는 가역적인(Reversible)을 의미한다. 그리고 같은 양의 기체가 용기에 들어있고 등압(Isobaric Work) 조건에서 가역과정인 경우, 열원에서 열을 받아들임으로 기체가 외부에 하는 일은

$$
\delta{W}_{rev} = -pdV
$$

여기서 부호가 음수인 것은 계의 입장에서 바라봤을 때 외부에 일을 함으로 에너지를 잃기 때문이다. 이제 dU를 다음으로 바꿔쓰자.

$$
dU = \delta{Q_{rev}} + \delta{W_{rev}} = TdS - pdV
$$

따라서 에너지 보존식이 T,S,p,V의 함수로 만들어졌다. 

### 볼츠만 엔트로피 (Boltzman Entropy)
앞에서 얻은 또 다른 에너지 보존식의 표현을 이용할 것이다. 이 식을 전미분의 형태로 쓰게되면,

$$
dU = \frac{\partial{U}}{\partial{S}} \vert_V dS + \frac{\partial{U}}{\partial{V}} \vert_S dV
$$

그러면 온도에 대한 식을 다음과 같이

$$
T = \frac{\partial{U}}{\partial{S}} \vert_V
$$

나타낼 수 있고, 여기서 에르고딕 가설에 의한 온도의 정의는

$$
\frac{1}{k_BT} = \frac{d\ln\Omega}{dE}
$$

여기서 $\Omega$는 microstate의 총 상태수로 양의 정수값을 가진다. E는 그 상태수가 가지는 에너지이다.
두 식을 결합하면,

$$
\frac{\partial{S}}{\partial{U}} \vert_V = {k_B}\frac{d\ln\Omega}{dE}
$$

그러므로 볼츠만의 엔트로피 표현을 얻는다.

$$
S = k_B\ln\Omega
$$

### 깁스 엔트로피 (Gibbs Entropy)
앞에서 살펴본 엔트로피는 사실 거시적으로 살펴본 것이다. 만약에 이 거시상태들에 각각 동등한 미시 상태(microstate)가 주어진다면 어떻게 생각해야 할까? 전체적인 엔트로피를 다음과 같이 쓰자.

$$
S_{tot} = S + S_{micro}
$$ 

여기서 $S_{micro}$가 추가된 것이 우리가 고려해줘야 할 미시 상태의 엔트로피이며, S가 그것을 고려하지 않았을 때 엔트로피이다.[^1]

microstate에 대해서 상태 측정은 불가능 하지만, 간단한 통계를 이용하여 가늠할 수 있다. 먼저 모든 microstate의 합이 우리가 측정한 거시상태의 수와 동일해야 하므로, 이를 N 이라고 할 때

$$
N = \sum_i{n_i}
$$

$n_i$는 각 개별 상태이다. 그리고 이를 발견할 확률을 $P_i$라고 하면

$$
P_i = \frac{n_i}{\sum_i{n_i}} \qquad \sum_iP_i = 1
$$

볼츠만의 엔트로피 표현에서 $\Omega$는 거시상태에서 보는 microstate의 총 수로 여기서 N과 같기 때문에, Total Entropy를

$$
S_{tot} = k_B\ln{N}
$$

으로 쓰고, microstate에 대한 엔트로피는, 각 개별 상태 엔트로피의 평균으로 나타낸다.

$$
S_{micro} = \langle s_i \rangle = \sum_i P_is_i = \sum_i P_ik_B\ln{n_i}
$$

그러므로 microstate를 제외한 엔트로피 S를

$$
\begin{aligned}
S &= S_{tot} - S_{micro} \\
&= k_B\ln{N} - \sum_i P_ik_B\ln{n_i} \\
&= k_B\sum_i P_i \left( \ln{N} - \ln{n_i} \right) \\
&= k_B\sum_i P_i \ln\frac{N}{n_i} \\
&= -k_B\sum_i P_i \ln\frac{n_i}{N} \\
&= -k_B\sum_i P_i \ln{P_i}
\end{aligned}
$$

Gibbs entropy 표현은 우리가 실제 측정할 수 없는 microstate 를 제외하고 상태의 확률을 알려주는 역할을 해준다.

## 정보이론적 엔트로피 (Informatic Entropy)
### 섀넌 엔트로피 (Shannon Entropy)
Claude Shannon은 어떤 정보량 Q에 대해 다음과 같이 정의하였다.

$$
Q = -k\log_2 P
$$

여기서 k는 양의 상수로, 대부분 1 로 둔다. 정보량에 음수가 붇는다는 것은, 어떤 문장에 담겨있는 확률 P가 작으면 정보 Q는 많아지는 의미를 가진다. Gibbs entropy 표현과 같이 맞추면

$$
S = \langle Q \rangle = -k\sum_iP_i\log_2P_i
$$

이를 Shannon entropy라고 한다. 엄밀하게 따지면, $k=k_B, log_2 \rightarrow \ln$을 만족해야 Gibbs Entropy가 된다.[^2] 그러므로 정보이론에서의 엔트로피는 상수들이 의미하는 바가 열역학적 엔트로피와는 같지 않다.
하지만 다소 정확하지 않은 접근이지만, 표현할 수 있는 식의 형태가 비슷하다. 그러므로 정보이론과 통계역학을 연관 짓는데에는 도움이 된다.[^3]

### 폰 노이만 엔트로피 (von Neumann Entropy)
이제 폰 노이만 엔트로피에 대해서 알아볼 차례가 되었다. 폰 노이만 엔트로피는 확률이 있는 자리에 양자역학에서의 밀도 행렬(density matrix)로 대치가 된다. 즉 다시 말해,

$$
S = -Tr(\rho\ln\rho)
$$

여기서 자연로그로 바뀐것은 일반적으로는 양자계에서 밑이 2인 로그 보다는 자연로그를 사용하기가 용이하기 때문이다. 이 때 여기서 Density Matrix가 Pure State이면
[행렬 고윳값 분해(대각화)](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix)로

$$
S = -\sum_i^n\lambda_i\ln{\lambda_i}
$$

이 되며 앞의 Shannon Entropy와 유사한 형태를 띄게된다. 이것에 대한 자세한 계산과정과 설명은,
'[슈미트 분해](physics/Schmidt-Decomposition/#폰-노이만-엔트로피와-concurrence)' 게시글을 참고할 수 있다.

## References
* Stephen J. Blundell, Concepts in Thermal Physics, CH14, CH15
* Wikipedia, [von Neumann entropy](https://en.wikipedia.org/wiki/Von_Neumann_entropy)

[^1]: 여기서 의문점, 만약에 microstate까지 고려한다면 곱의 형태로 나타내야 하지 않을 까? 그것은 앞의 볼츠만의 엔트로피 표현에서, **로그**가 들어간다는 점을 생각해보면 된다.
[^2]: 사실 로그가 다른 것은 그렇게 중요하진 않다. 로그의 관계식으로 밑만 바꾸면 되기 때문에.
[^3]: 물론 열과 정보 사이의 관계는 Rolf Landauer가 제시한 란다우어의 원리라는 것으로 연결짓기도 한다.