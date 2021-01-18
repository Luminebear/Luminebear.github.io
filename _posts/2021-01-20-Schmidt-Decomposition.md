---
title: "슈미트 분해"
tags: [Phyiscs, Information, QuantumInformation, 물리학, 정보, 양자정보] # 태그 입력
categories: Physics
mathjax: true # MathJax 사용을 위한 태그
image:
  path: /_images/abstract-3.jpg
  feature: abstract-3.jpg
comments: true
published: false
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

으로 기술하였다. 물론 규격화 조건 $\sum_{i,j}{\vert C_{ij} \vert}^2$를 만족하며, 
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
슈미트 분해식을 살펴보면 합의 표현이 하나의 Dummy Index 'k'으로 나타난다. 그리고 Ket Vector 앞에 붙는 계수에 대해 특별히 Schmidt Number라고 부르는데, 이것이 중요한 역할을 한다.