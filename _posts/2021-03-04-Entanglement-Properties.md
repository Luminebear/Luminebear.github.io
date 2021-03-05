---
title: "양자 얽힘: 양자 얽힘만의 특징"
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

이번에는 고전적 상관관계와 달리 양자 얽힘에서 나타나는 특징을 조금 더 자세히 다루어보도록 하자.
또한 여기서는 광학계를 기본으로 하는 경우에서 살펴보도록 한다. 즉, 수평 편광 $\vert \leftrightarrow \rangle$, 
수직 편광 $\vert \updownarrow \rangle$ 을 basis 으로 하는 경우이다. 

<figure alt="" class="center">
  <a href="/assets/images/polbasis.png">
	<img src="/assets/images/polbasis.png"></a>
	<figcaption>수평 편광과 수직 편광을 basis로 하는 system 의 시각화.</figcaption>
</figure>

또한 기호의 따른 혼동을 발생할 수 있으므로, 여기서는 
$\vert \leftrightarrow \rangle \rightarrow \vert 0 \rangle \,, \vert \updownarrow \rangle \rightarrow \vert 1 \rangle$
으로 간주하도록 하자. 그리고 singlet Bell state $\vert \Psi_{\rm AB}^{-} \rangle$ 를 선택하여
예제를 살펴보도록 한다.

$$
\vert \Psi_{\rm AB}^{-} \rangle = \frac{1}{\sqrt{2}} \left( \vert 01 \rangle - \vert 10 \rangle \right)
$$

물론 $\vert 0 1 \rangle = \vert 0\_{A} \rangle \otimes \vert 1\_{B} \rangle$ 이다.

## 얽힘에 대한 측정과 붕괴
먼저 고전적인 상황을 생각을 해보자. Alice 와 Bob 이라는 두 사람이 주머니에서 0 또는 1 이라는
숫자를 무작위로 뽑는다. 만약에 Alice 가 0 을 뽑았으면, Bob 은 반드시 1 을 뽑게되고, 반대로
Alice 가 1 을 뽑았으면, Bob 은 반드시 0 가 될 것이다. 즉 어느 숫자를 뽑느냐에 따라
그 숫자가 결정이 되는 것이다.

그렇다면 양자 얽힘 상황은 어떻게 이루어 질까? 그 전에, 양자 얽힘 상황에서는 뽑는 행위,
다시말해 측정 행위를 정의하도록 하자. 여기서는 기본적인 PVM(Projection-Valued Measure)
으로 생각할 것이다. 예를 들어, Alice 가 A 를 측정하는 행위에 대해,

$$
\vert 0_{\rm A} \rangle \langle 0_{\rm A} \vert \Psi_{\rm AB}^{-} \rangle \qquad \vert 1_{\rm A} \rangle \langle 1_{\rm A} \vert \Psi_{\rm AB}^{-} \rangle
$$

으로 나타낸다. 마찬가지로 고전적인 상황과 동일하게 0 과 1 로 뽑는 것을 생각해보면,
Alice 가 측정으로 $\vert 0\_{A} \rangle$ 의 결과를 얻었다고 하자.
그러면 Bob 은 $\vert 1\_{B} \rangle$ 의 결과를 얻는다. 이것을 식으로 나타내면,

$$
\begin{aligned}
\vert 0_{\rm A} \rangle \langle 0_{\rm A} \vert \Psi_{\rm AB}^{-} \rangle
&= \frac{1}{\sqrt{2}} \vert 0_{\rm A} \rangle \left( \langle 0_{A} \vert 0 1 \rangle - \langle 0_{A} \vert 1 0 \rangle \right) \\
&= \frac{1}{\sqrt{2}} \vert 0_{\rm A} \rangle \vert 1_{\rm B} \rangle 
\end{aligned}
$$

으로 나타난다. 여기서 주의할 점이 있다. Alice 가 **'측정이라는 행위'**를 통해서
결과를 얻었다는 점이다. 다시말해, Alice 가 측정을 하지 않는 이상은,
양자 상태가 붕괴되어 결정되지 않고, $\vert \Psi_{\rm AB}^{-} \rangle$ 인 상태를 유지한다.
즉 아주 멀리 떨어져 있더라도, 한 쪽에서 측정행위가 이루어지지 않는 이상은, 양자 상태를
유지하게 된다는 점이다.

## Orthonormal basis 변환에 대한 correlation / anticorrelation 불변
이번에는 basis 를 바꾸는 측정을 해보도록 하자. 기존의 측정이 수평, 수직 편광에 대해서
이루어져 basis 를 이루었다면, 이번에는 45도를 틀어 $45^{\circ} \,, 135^{\circ}$ 를 구분하는
측정을 한다고 해보자. 이렇게 만들어지는 새로운 basis 를 $\vert {+} \rangle \,, \vert {-} \rangle$
이라고 하면,

$$
\vert {+} \rangle = \frac{1}{\sqrt{2}} \left( \vert 0 \rangle + \vert 1 \rangle \right) \qquad
\vert {-} \rangle = \frac{1}{\sqrt{2}} \left( \vert 0 \rangle - \vert 1 \rangle \right)
$$

으로 나타낼 수 있다.[^1]

<figure class="half">
    <a href="/assets/images/polnewbasis3d.png"><img src="/assets/images/polnewbasis3d.png"></a>
    <a href="/assets/images/polnewbasis2d.png"><img src="/assets/images/polnewbasis2d.png"></a>
    <figcaption>45도 틀어서 만들어진 새로운 basis</figcaption>
</figure>

새롭게 세운 기준을 기존에 측정하던 방법으로 다시 쓰게되면,

$$
\vert 0 \rangle = \frac{1}{\sqrt{2}}\left( \vert {+} \rangle + \vert {-} \rangle \right)
\qquad
\vert 1 \rangle = \frac{1}{\sqrt{2}}\left( \vert {+} \rangle - \vert {-} \rangle \right)
$$

으로 나타내진다. 이제 이 식을 singlet Bell state 에 대입하도록 하자.

$$
\begin{aligned}
\vert \Psi_{\rm AB}^{-} \rangle &= \frac{1}{\sqrt{2}} \left( \frac{1}{2}\left( \vert {+} \rangle + \vert {-} \rangle \right)\_{\rm A} \left( \vert {+} \rangle - \vert {-} \rangle \right)\_{\rm B} - \frac{1}{2}\left( \vert {+} \rangle - \vert {-} \rangle \right)\_{\rm A} \left( \vert {+} \rangle + \vert {-} \rangle \right)\_{\rm B} \right) \\
&= \frac{1}{\sqrt{2}} \left( - \vert {+}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle + \vert {-}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle \right)
\end{aligned}
$$

놀랍게도, basis 는 달라졌지만, anticorrelation 은 유지하는 것을 확인할 수 있다! 마찬가지로,
[양자 얽힘: 벨 상태](/physics/Entanglement-Bellstate/#벨-상태-bell-state) 게시글에서 소개한
나머지 Bell state 에 대해서도 $\vert + \rangle \,, \vert - \rangle$ 의 basis 로 변환을 하면,

$$
\begin{aligned}
\vert \Psi_{\rm AB}^{+} \rangle &= \frac{1}{\sqrt{2}} \left( \vert 0 1 \rangle + \vert 1 0 \rangle \right) \\
&= \frac{1}{\sqrt{2}} \left( \vert {+}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle
- \vert {-}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle \right) 
\rightarrow \vert \Phi_{\rm AB}^{-} \rangle \\
\vert \Psi_{\rm AB}^{-} \rangle &= \frac{1}{\sqrt{2}} \left( \vert 0 1 \rangle - \vert 1 0 \rangle \right) \\
&= \frac{1}{\sqrt{2}} \left( -\vert {+}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle
+ \vert {-}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle \right)
\rightarrow -\vert \Psi_{\rm AB}^{-} \rangle \\
\vert \Phi_{\rm AB}^{+} \rangle &= \frac{1}{\sqrt{2}} \left( \vert 0 0 \rangle + \vert 1 1 \rangle \right) \\
&= \frac{1}{\sqrt{2}} \left( \vert {+}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle 
+ \vert {-}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle \right) 
\rightarrow \vert \Phi_{\rm AB}^{+} \rangle \\
\vert \Phi_{\rm AB}^{-} \rangle &= \frac{1}{\sqrt{2}} \left( \vert 0 0 \rangle - \vert 1 1 \rangle \right) \\
&= \frac{1}{\sqrt{2}} \left( \vert {+}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle 
+ \vert {-}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle \right) 
\rightarrow \vert \Psi_{\rm AB}^{+} \rangle
\end{aligned}
$$

으로 변환이 되는 모습을 알 수 있다. 두 번째 경우가 anticorrelation 인데, 나머지 경우들을
살펴보면 correlation 끼리 바뀌거나 그대로 유지하는 모습을 보인다.

## Basis 변환과 양자 얽힘
또한 양자 얽힘에 있어 재미있는 사실은, orthonormal basis 에 대한 변환을 하지 않은
상태에서 얽힘의 관계가 더 크다는 점이다. 예를 들어 $\vert 0 1 \rangle$ 과 같이 얽혀진
큐비트가 주어진 상황에서, $\vert {+} \rangle \,, \vert {-} \rangle$ 으로 basis를 바꾼다고
생각해보자. 그러면

$$
\begin{aligned}
\vert 0 1 \rangle &= \frac{1}{2}\left( \vert {+} \rangle + \vert {-} \rangle \right)
\left( \vert {+} \rangle - \vert {-} \rangle \right) \\
&= \frac{1}{2} \left( \vert {+}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle - \vert {+}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle + \vert {-}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle - \vert {-}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle \right) \\
&= \frac{1}{2} \left[ \left( \vert {+}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle - \vert {-}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle \right)
+ \left( - \vert {+}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle + \vert {-}\_{\rm A} \rangle \vert {+}\_{\rm B} \rangle \right) \right]
\end{aligned}
$$

으로 정리할 수 있고, 각각 correlation 과 anticorrelation 으로 나뉘는 것을 확인할 수 있다.
이러한 점이 눈여겨 보야할 점이다. 측정의 관점에서 생각해보면, 
$\vert 0 \rangle \,, \vert 1 \rangle$ 을 측정하는 관점에서,
반드시 anticorrelation 이 있다. 그러나 $\vert + \rangle \,, \vert - \rangle$ 으로 측정하는
관점에서는, 50% 는 correlation 을, 50% 는 anticorrelation 이라는 점이다. 예를 들어
A 의 상태가 $\vert - \rangle$ 이면

$$
\vert {-}\_{\rm A} \rangle \langle {-}\_{\rm A} \vert 0 1 \rangle 
= \frac{1}{2} \left( - \vert {-}\_{\rm A} \rangle \vert {-}\_{\rm B} \rangle + \vert {-}\_{\rm A} \rangle \vert {+}\_{\rm B} \right)
$$

으로 B가 $\vert - \rangle$ 일지 $\vert + \rangle$ 일지 알 수없다. 그러므로 상관도가 높은
$\vert 0 \rangle \,, \vert 1 \rangle$ 의 측정이 얽힘의 상관관계를 가지고, basis 를 바꾼
상황에서는 상관관계가 약해진 것이 된다.

## References
* 이해웅, 양자 정보학 강의, 3장
* Wikipedia, [Measurement in quantum mechanics](https://en.wikipedia.org/wiki/Measurement_in_quantum_mechanics)

[^1]: 물론, 후자는 $-45^\circ$ 를 basis 로 할 수도 있다.