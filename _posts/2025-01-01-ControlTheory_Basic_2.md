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
<img src="https://www.dropbox.com/scl/fi/gt1fikxzmtodwa53h5blt/1_Modeling.png?rlkey=dpd748rlpgia58l8rm1q4jqgx&st=fe7njcnd&dl=1" width = "1800" height = "1800" 
alt ="System Modeling explain">    
</center>
<center>
Fig 1. System Modeling
</center> 


## 2. Open-loop sysem VS closed-loop sysem 
Fig. 2.1는 open-loop control system, Fig. 2.2는 closed-loop control system에 대해 블록 다이어그램으로 표현한 그림이다. System에 입력되는 값으로는 제어 입력 외, 외란(disturbance), 노이즈(noise)가 있다. 

<center>
<img src="https://www.dropbox.com/scl/fi/d0z791ca9abq4l384paca/2_BlockDiagram_of_open.png?rlkey=r4pv0w3s3vm0svnka3hsgsmu4&st=skyrer3l&dl=1"
width = "1800" height = "1800" alt ="Block diagram of open-loop system">    
</center>     
<br> <!-- 줄바꿈으로 간격 추가 --> 
<center>
Fig 2.1 Block diagram of open-loop system
</center> 
<br> <!-- 줄바꿈으로 간격 추가 --> 

<center>
<img src="https://www.dropbox.com/scl/fi/9v2nkiv2rn8t8rqeepc38/2_BlockDiagram.png?rlkey=nsb46qf2itsa9g6ark6qhp99h&st=qenatwb2&dl=1"
width = "1800" height = "1800" alt = "Block diagram of closed-loop system">    
</center>     
<br> <!-- 줄바꿈으로 간격 추가 --> 
<center>
Fig 2.2 Block diagram of closed-loop system
</center> 

- $r$: desired output
- $e$: error 
- $u$: control input
- $y$: system output
- $w_d$: disturbance
- $w_n$: noise

### Example) Cruise Control에 대한 open-loop 및 closed-loop control 성능 비교
일반적으로 제어는 open-loop 제어가 아닌 closed-loop 제어를 수행한다. 왜 open-loop가 아닌 closed-loop 제어를 수행해야 할까?
<br> <!-- 줄바꿈으로 간격 추가 --> 

- Actual system: $y = u$
- Modeling system: $y = 2u$
- Disturbnace: $w_d = 10\sin(\pi t)$
- Reference : $r = 60$

#### i. Open-loop 제어
Open-loop 제어 시, 제어기는 시스템의 역수를 취해 계산해 보자. Controller의 출력 $u$는 식 (3.1)처럼 계산할 수 있다.

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

#### ii. Closed-loop 제어
Closed-loop 제어 시, P제어를 수행해 보자. $K$를 제어기의 gain이라고 하면, controller의 출력 $u$는 식 (3.3)처럼 계산할 수 있다.

$$
\begin{align}
\begin{split}
y &= K\left(w_r-y\right)+\mathrm{w}_{\mathrm{d}} \\
  &= \frac{K}{1+K} w_r+\frac{1}{1+K} w_d \\
\end{split}\tag{3.3}
\end{align}
$$

## 3. Closed-loop 제어를 수행해야 하는 이유
**1) Uncertainty**
- 제어를 할 때, 시스템을 모델링하게 되는데, 모델링을 100% 정확하게 수행하는 것은 불가능하며, 모델의 불확실성으로 인해 open-loop는 제어의 성능이 좋지 못하다.
- Open-loop는 시스템 parameter 변화를 감지하지 못한다.

**2) Disturbance**
- 완벽하게 시스템 모델링이 가능 하더라도, Open-loop 는 외부 외란을 고려하지 못한다.

**3) Stability**
- Open-loop 제어를 통해서는 불안정하게 동작하는 시스템을 안정적으로 만들 수 없다.
