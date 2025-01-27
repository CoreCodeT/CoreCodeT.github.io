---
layout: single
title: "Control Theory Basic - 2"
categories: [control theory]
tag: [control]
toc: true
toc_sticky: true
toc_label: 목차
author_profile: true
sidebar: 
    nav: "docs"
search: true #
use_math: true
sidebar:
    nav: "counts"
---

## 1. 시스템 모델링
일반적으로 제어기를 개발할 때 시뮬레이션을 통해 시스템의 응답을 파악하고, 적절한 제어기를 개발한다. 시스템을 응답 특성을 파악하기 위해서는 <span style="color:blue"> 시스템의 모델링 </span>이 필수적이다. 
시스템의 모델은 <span style="color:blue"> 미분 방정식으로 표현</span>이 가능하며, 시스템의 응답은 <span style="color:blue"> 미분방정식의 해</span> 를 찾음으로써 알 수 있다.
시스템 모델링은 물리 법칙을 활용하거나, 측정 데이터를 통해 수행할 수 있다.
- **Based on physics**: 실제 시스템의 유형을 파악하고, 적절한 물리 법칙을 적용하여 시스템을 모델링
- **Based on measurement data**: Input에 대한 Output 정보를 기반으로 시스템의 응답 특성을 파악하여 시스템을 모델링

Fig.1은 시스템 모델링부터 시스템 응답의 흐름을 설명하고 있다.
<center>
<img src="https://www.dropbox.com/scl/fi/gt1fikxzmtodwa53h5blt/1_Modeling.png?rlkey=dpd748rlpgia58l8rm1q4jqgx&st=fe7njcnd&dl=1" width = "100%" height = "100%" 
alt ="System Modeling explain">    
</center>
<center>
Fig 1. System Modeling
</center> 


## 2. open loop sysem VS closed loop sysem 
Fig. 2.1는 open loop control system, Fig. 2.2는 closed loop control system에 대해 블록 다이어그램으로 표현한 그림이다. System에 입력되는 값으로는 제어 입력 외, 외란(disturbance), 노이즈(noise)가 있다. 

<center>
<img src="https://www.dropbox.com/scl/fi/d0z791ca9abq4l384paca/2_BlockDiagram_of_open.png?rlkey=r4pv0w3s3vm0svnka3hsgsmu4&st=skyrer3l&dl=1"
width = "100%" height = "100%" alt ="Block diagram of open loop system">    
</center>     
<br> <!-- 줄바꿈으로 간격 추가 --> 
<center>
Fig 2.1 Block diagram of open loop system
</center> 
<br> <!-- 줄바꿈으로 간격 추가 --> 

<center>
<!-- <img src="https://www.dropbox.com/scl/fi/9v2nkiv2rn8t8rqeepc38/2_BlockDiagram.png?rlkey=nsb46qf2itsa9g6ark6qhp99h&st=qenatwb2&dl=1"
width = "1800" height = "1800" alt = "Block diagram of closed loop system">     -->
<img src="https://www.dropbox.com/scl/fi/9v2nkiv2rn8t8rqeepc38/2_BlockDiagram.png?rlkey=nsb46qf2itsa9g6ark6qhp99h&st=qenatwb2&dl=1"
width = "100%" height = "100%" alt = "Block diagram of closed loop system">    
</center>     
<br> <!-- 줄바꿈으로 간격 추가 --> 
<center>
Fig 2.2 Block diagram of closed loop system
</center> 

- $r$: reference input(desired output)
- $e$: error 
- $u$: control input(controller output)
- $y$: system output
- $w_d$: disturbance
- $w_n$: noise

### Example) Open loop 와 closed loop control 출력 값 비교 
일반적으로 제어는 open loop 제어가 아닌 closed loop 제어를 수행한다. 왜 open-loop가 아닌 closed-loop 제어를 수행해야 할까? 
이를 알아보기 위해 위 Fig. 2.1과 Fig. 2.2의 parameter들은 아래처럼 설정해 보자.
(<span style="color:green">이는 단순화 된 cruise control model이라고 볼 수 있다. 동역학 적인 요소는 없으며, 간단하게 input이 바로 output이 되는 구조이다. </span>)
<br> <!-- 줄바꿈으로 간격 추가 --> 

- Actual system: $y = u$
- Modeling system: $y = 2u$
- Disturbnace: $w_d = 10\sin(\pi t)$
- Reference input : $r = 40$

#### i. open loop 제어
모델링 된 시스템은 $y=2u$ 이다. open loop 제어 시, 제어기는 시스템의 역수를 취해 계산해 보자. Controller의 출력 $u$는 식 (3.1)처럼 계산할 수 있다.
(<span style="color:green">물론, 단순히 시스템의 역수를 취하는 방법 말고 다른 여러가지 방법도 생각해 볼 수 있다.</span>)

$$
\begin{align}
u = \frac{r}{2}\tag {3.1}
\end{align}
$$

따라서, 시스템의 출력 $y$는 식 (3.2)와 같다.
$$
\begin{align}
y = \frac{r}{2} + w_d\tag {3.2}
\end{align}
$$

#### ii. closed loop 제어
closed loop 제어 시, P제어를 수행해 보자. $K$를 제어기의 gain이라고 하면, controller의 출력 $u$는 식 (3.3)처럼 계산할 수 있다.
식 (3,3)은 외부 입력인 $r$, $w_d$로 이루어진 것을 알 수 있다.
<mark style='background-color: #ffdce0'> $K$가 크면 클수록 외란인 $w_d$에 대한 항은 0에 수렴하고, reference input $r$에 해당 하는 값은 $r$로 수렴한다. 따라서, 제어기 게인 K는 크면 클수록 외란에 강인하다고 할 수 있다. </mark>
(<span style="color:green">현실에서 K는 controller가 출력하는 output이므로, 실제 actuator의 성능에 좌우된다. 무한히 크게할 수도 없고, Step input처럼 동작하게 하는 것도 불가능하다. </span>)
  
$$
\begin{align}
\begin{split}
y &= K\left(w_r-y\right)+w_d \\
  &= \frac{K}{1+K} r+\frac{1}{1+K} w_d \\
\end{split}\tag{3.3}
\end{align}
$$

#### iii. open loop vs closed loop 제어 결과 비교
Fig. 2.3은 open loop와 closed loop system의 출력 값을 비교한 그래프이다. Open loop는 외란에 대해 민감하게 반응하는 반면, closed loop 제어의 경우 외란에 무관하게 reference input을 잘 추종하고 있다.
<center>
<img src="https://www.dropbox.com/scl/fi/7ge8da4o0203lhtze38q4/2_OLvsCL-Graph.png?rlkey=4sfvi9lpxcg5urxzbsarv3k6l&st=c5ms0k1w&dl=1"
width = "100%" height = "100%" alt = "Graph of open loop versus closed loop system">    
</center>     
<br> <!-- 줄바꿈으로 간격 추가 --> 
<center>
Fig 2.3 Block diagram of open and closed loop system
</center> 

## 3. closed loop 제어를 수행해야 하는 이유
closed loop 제어를 수행해야 하는 이유는 많지만, 아래처럼 정리해 볼 수 있다. 특히, 본 페이지에서는 Disturbance에 대해 open loop와 closed loop 제어 성능을 비교해 보았다.
**1) Uncertainty**
- 제어를 할 때, 시스템을 모델링하게 되는데, 모델링을 100% 정확하게 수행하는 것은 불가능하며, 모델의 불확실성으로 인해 open loop는 제어의 성능이 좋지 못하다.
- open loop는 시스템 parameter 변화를 감지하지 못한다.

**2) Disturbance**
- 완벽하게 시스템 모델링이 가능 하더라도, open loop 는 외부 외란을 고려하지 못한다.

**3) Stability**
- open loop 제어를 통해서는 불안정하게 동작하는 시스템을 안정적으로 만들 수 없다.
<br> <!-- 줄바꿈으로 간격 추가 --> 

Reference: Data Driven Science & Engineering Machine Learning, Dynamical Systems, and Control, _Steven L. Brunton Department of Mechanical Engineering University of Washington, J. Nathan Kutz Department of Applied Mathematics University of Washington_
