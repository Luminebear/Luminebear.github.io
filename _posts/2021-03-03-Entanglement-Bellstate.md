---
title: "양자 얽힘: 벨 상태"
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

앞의 게시글에서 두 스핀계가 주어질 때의 식

$$
\begin{aligned}
\vert \psi_{\rm AB} \rangle &= a\vert \uparrow \uparrow \rangle + b\vert \uparrow \downarrow \rangle + c\vert \downarrow \uparrow \rangle + d\vert \downarrow \downarrow \rangle
\end{aligned}
$$

에서 특별히 두 가지의 경우로 나누었는데,

$$
\begin{aligned}
\vert \Psi_{\rm AB} \rangle &= b\vert \uparrow \downarrow \rangle + c\vert \downarrow \uparrow \rangle \\
\vert \Phi_{\rm AB} \rangle &= a\vert \uparrow \uparrow \rangle + d\vert \downarrow \downarrow \rangle
\end{aligned}
$$

전자를 anticorrelation, 후자를 correlation 이라고 불렀다. 여기서 특별한 경우를 살펴보도록 하자.

## Coefficient에 따른 얽힘의 최소와 최대
먼저 두 식에 있는 coefficient가 규격화 조건 

$$
\vert b \vert^2 + \vert c \vert^2 =1 \,, \vert a \vert^2 + \vert d \vert^2 = 1
$$

을 만족하면, 사실 $\vert \Psi_{\rm AB} \rangle$ 과 $\vert \Phi_{\rm AB} \rangle$ 는 다음과 같이 바뀐다.

$$
\begin{aligned}
\vert \Psi_{\rm AB} \rangle &= (1-\vert c \vert^2)\vert \uparrow \downarrow \rangle + \vert c \vert^2\vert \downarrow \uparrow \rangle \\
\vert \Phi_{\rm AB} \rangle &= \vert a \vert^2 \vert \uparrow \uparrow \rangle + (1-\vert a \vert^2)\vert \downarrow \downarrow \rangle
\end{aligned}
$$

따라서, 정규화된 이항분포(Binomial Distribution)을 따르게 된다.[^1] 그러므로, 변수의 값이 0이나 1이면,
분리 가능 상태가 되므로, 얽힘의 정도는 0이 된다. 그렇다면, 얽힘이 최대가 되는 경우는 언제일까?
바로 $' 1/\sqrt{2} '$일 때 이다. 즉,

$$
\begin{aligned}
\vert \Psi_{\rm AB} \rangle &= \frac{1}{\sqrt{2}} \left( \vert \uparrow \downarrow \rangle + e^{i\phi}\vert \downarrow \uparrow \rangle \right) \\
\vert \Phi_{\rm AB} \rangle &= \frac{1}{\sqrt{2}} \left( \vert \uparrow \uparrow \rangle + e^{i\phi}\vert \downarrow \downarrow \rangle \right)
\end{aligned}
$$

으로 쓸 수 있다. 이 때, 불확실성을 넣기 위하여, 뒤의 항에 위상$(e^{i\phi})$ 을 추가하였다.

## 벨 상태 (Bell State)
이 때, 특별히 위상이 $\phi = n\pi$ (n은 정수) 를 만족하는 경우, 아래와 같은 네가지의 식을 만들 수 있다.

$$
\begin{aligned}
\vert \Psi_{\rm AB}^{+} \rangle &= \frac{1}{\sqrt{2}} \left( \vert \uparrow \downarrow \rangle + \vert \downarrow \uparrow \rangle \right) \quad
\vert \Psi_{\rm AB}^{-} \rangle = \frac{1}{\sqrt{2}} \left( \vert \uparrow \downarrow \rangle - \vert \downarrow \uparrow \rangle \right) \\
\vert \Phi_{\rm AB}^{+} \rangle &= \frac{1}{\sqrt{2}} \left( \vert \uparrow \uparrow \rangle + \vert \downarrow \downarrow \rangle \right) \quad
\vert \Phi_{\rm AB}^{-} \rangle = \frac{1}{\sqrt{2}} \left( \vert \uparrow \uparrow \rangle - \vert \downarrow \downarrow \rangle \right)
\end{aligned}
$$

이 네가지 상태를 특별히 **벨 상태 (Bell State)** 라고 한다. 벨 상태 역시 orthonormal basis 가 되어 
주어진 Hilbert space 를 이루는 complete set 이다. 이를 테면 처음 식 $\vert \psi_{\rm AB} \rangle$ 을
네가지 벨 상태의 식으로 나타내면,

$$
\begin{aligned}
\vert \psi_{\rm AB} \rangle = A\vert \Psi_{\rm AB}^{+} \rangle + B\vert \Psi_{\rm AB}^{-} \rangle
+ C\vert \Phi_{\rm AB}^{+} \rangle + D\vert \Phi_{\rm AB}^{-} \rangle
\end{aligned}
$$

으로 나타낼 수 있다. 이 때 처음 식을 비교하여 계수를 구해보면,

$$
A = \frac{b+c}{\sqrt{2}} \quad B = \frac{b-c}{\sqrt{2}} \quad C = \frac{a+d}{\sqrt{2}} \quad D = \frac{a-d}{\sqrt{2}}
$$

으로 계산된다. 그러므로 벨 상태 역시 각 상태의 측정 확률은 $\vert A \vert^2 \,, \vert B \vert^2 \,, \vert C \vert^2 \,, \vert D \vert^2$ 가 된다.

[^1]: 엄밀하게는, 변수의 제곱인 경우.