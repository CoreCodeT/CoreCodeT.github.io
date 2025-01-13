---
layout: single
title: "Kinematic Model"
categories: [vehicle dynamics]
tag: [vehicle, modeling]
toc: true
toc_sticky: true
toc_label: 목차
toc_icon: "fas fa-table-tennis"
author_profile: true
sidebar: 
    nav: "docs"
search: true #
use_math: true
sidebar:
    nav: "counts"
---

## Kinematic Model of Lateral Vehicle Motion 이란
**Kinematic Model**은 dynamic model과 다르게 힘을 고려하지 않고, 기구학(geometric) 관계를 기반으로 차량의 움직임을 설명하기 위한 모델이다. 
Kenematic Model을 설명하기 위해서 많은 가정들을 사용하는데, 대표적으로 아래의 가정이 중요하다.

<div class="notice--success">
<h4>Assumptions</h4>
<ul>
  <li> 차량의 속도는 작다. </li>
  <li> 차량의 wheel slip 은 없다. </li>
  <li> 전륜의 좌/우측, 후륜의 좌/우측의 wheel angle은 같다. </li>
  <li> 차량은 planar motion을 갖는다.</li>
</ul>
</div>

### 차량의 기하학적 구조
점 $\mathbf{O}$ 차량의 선회 반경 중심을 의미한다.

<center>
<img src="https://www.dropbox.com/scl/fi/0p6cxp5g74aub2ofc972g/Kinematic.png?rlkey=kmftofgsnuan40p4xxqedlgip&st=mlcywim4&dl=1"
width = "500" height = "500" alt = "Kinematic bicycle model">    
</center>
<center>
Fig 1. Kinematic bicycle model    
</center> 


OCA에서 sin 법칙을 적용하면 식 (1.1)과 같다.


$$
\frac{\sin \left(\delta_f-\beta\right)}{\ell_f}=\frac{\sin \left(\frac{\pi}{2}-\delta_f\right)}{R} \tag{1.1}
$$

OCB에서 sin 법칙을 적용하면 식 (1.2)과 같다.

$$
\frac{\sin \left(\beta-\delta_r\right)}{\ell_r}=\frac{\sin \left(\frac{\pi}{2}+\delta_r\right)}{R} \tag{1.2}
$$


식 (1.1)로 부터 아래 식 (1.3)을 도출할 수 있다.

$$
\frac{\sin \left(\delta_f\right) \cos (\beta)-\sin (\beta) \cos \left(\delta_f\right)}{\ell_f}=\frac{\cos \left(\delta_f\right)}{R} \tag{1.3}
$$


식 (1.2)로 부터 아래 식 (1.4)를 도출할 수 있다.

$$
\frac{\cos \left(\delta_r\right) \sin (\beta)-\cos (\beta) \sin \left(\delta_r\right)}{\ell_r}=\frac{\cos \left(\delta_r\right)}{R} \tag{1.4}
$$


식 (1.3) 양변에  $\frac{\ell_f}{\cos \left(\delta_f\right)}$ 를 곱하면, 식 (1.5)를 얻을 수 있다.

$$
\tan \left(\delta_f\right) \cos (\beta)-\sin (\beta)=\frac{\ell_f}{R} \tag{1.5}
$$


식 (1.4) 양변에  $\frac{\ell_f}{\cos \left(\delta_f\right)}$ 를 곱하면, 식 (1.6)를 얻을 수 있다.

$$
\sin (\beta)-\tan \left(\delta_r\right) \cos (\beta)=\frac{\ell_r}{R} \tag{1.6}
$$


식 (1.5) 와 식 (1.6)을 더하면 식 (1.7)을 도출 할 수 있다.

$$
\left\{\tan \left(\delta_f\right)-\tan \left(\delta_r\right)\right\} \cos (\beta)=\frac{\ell_f+\ell_r}{R} \tag{1.7}
$$

Kenematic model에서는 heading angle(yaw angle) 변화율인 yaw rate $\dot{\psi}$ 을 식 (1.8)처럼 나타낼 수 있다.

$$
\dot{\psi}=\frac{V}{R} \tag{1.8}
$$

식 (1.8)을 식 (1.9)에 대입하여 $R$ 을 제거하면, 식 (1.9)처럼 표현할 수 있다.

$$
\dot{\psi}=\frac{V \cos (\beta)}{\ell_f+\ell_r}\left(\tan \left(\delta_f\right)-\tan \left(\delta_r\right)\right) \tag{1.9}
$$


<mark style='background-color: #dcffe4'>
따라서, kinematic model의 운동방정식은 식 (1.10)처럼 표현할 수 있다.
</mark> 

$$
\begin{aligned}
& \dot{X}=V \cos (\psi+\beta) \\
& \dot{Y}=V \sin (\psi+\beta) \\
& \dot{\psi}=\frac{V \cos (\beta)}{\ell_f+\ell_r}\left(\tan \left(\delta_f\right)-\tan \left(\delta_r\right)\right)
\end{aligned} \tag {1.10}
$$

위 식 (1.10)에서의 input은 $\delta_f, \delta_r$ and $V$ 이다.   
$V$은 time varying function으로 가정할 수도 있으며, 다른 종방향 차량모델로부터 계산하여 값을 얻을 수 있다.

Side slip angle을 유도해 보자. 식 (1.5)에 $\ell_r$ 를 곱하면, 식 (1.11) 처럼 표현된다.

$$
(\tan \left(\delta_f\right) \cos (\beta)-\sin (\beta))\ell_r = \frac{\ell_f}{R}\ell_r \tag{1.11}
$$

식 (1.6)에 $\ell_f$ 를 곱하면, 식 (1.12) 처럼 표현된다.

$$
(\sin (\beta)-\tan \left(\delta_r\right) \cos (\beta))\ell_f = \frac{\ell_r}{R}\ell_f \tag{1.12}
$$


Side slip angle을 유도하기 위해 식 (1.11)에서 식 (1.12)를 빼면, 식 (1.13)을 얻을 수 있다.

$$
(\tan \left(\delta_f\right) \cos (\beta)-\sin (\beta))\ell_r = (\sin (\beta)-\tan \left(\delta_r\right) \cos (\beta))\ell_f \tag{1.13}
$$

<mark style='background-color: #dcffe4'>
식 (1.13)를 정리하면, $\beta$는 식 (1.14) 처럼 $\beta$에 대해 표현할 수 있다.
</mark> 

$$
\beta=\tan ^{-1}\left(\frac{\ell_f \tan \delta_r+\ell_r \tan \delta_f}{\ell_f+\ell_r}\right) \tag{1.14}
$$

- $L$: wheel base [m]
- $\delta_f$: steering angle for the front wheel [rad]
- $\delta_r$: steering angle for the rear wheel [rad]
- $\beta$: side slip angle [rad]
- $V$: vehicle speed [m/s]
- $\psi$: heading angle or yaw[rad]
- $\gamma$: course angle [rad]
- $\(X, Y\)$: vehicle global position [m]

<!-- ### 자전거 모델 운동 방정식
자전거 모델은 시간에 따라 차량의 위치와 방향이 어떻게 변화하는지를 설명합니다. 차량의 상태는 위치 $(x, y)$, 헤딩 $\theta$, 속도 $v$로 설명됩니다. 제어 입력은 조향각 $\delta$와 차량의 속도 $v$입니다.

운동학 방정식은 다음과 같습니다:

$$
\dot{x} = v \cos(\theta)
$$

$$
\dot{y} = v \sin(\theta)
$$

$$
\dot{\theta} = \frac{v}{L} \tan(\delta)
$$

여기서:
- $\dot{x}$, $\dot{y}$, $\dot{\theta}$는 각각 $x$, $y$, $\theta$의 시간 변화율을 나타냅니다.

#### 예시: 회전 반경

주어진 조향각 $\delta$에 대해 회전 반경 $R$은 다음과 같이 계산할 수 있습니다:

$$
R = \frac{L}{\tan(\delta)}
$$

이 식은 회전 반경이 조향각 $\delta$에 반비례함을 보여줍니다.

### 자전거 모델의 가정
- 차량은 평면에서 이동합니다.
- 작은 조향각을 가정하여 측방향 미끄러짐이 없다고 봅니다.
- 속도와 조향각은 연속적으로 변화합니다.

## 2. 차동 구동 모델

차동 구동 모델은 좌우에 각각 독립적으로 구동되는 두 바퀴를 가진 로봇에 자주 사용됩니다. 각 바퀴는 다른 속도로 회전할 수 있어 로봇이 직진하거나 회전할 수 있습니다.

### 차량의 기하학적 구조

차동 구동 모델의 파라미터는 다음과 같습니다:

- $r$: 각 바퀴의 반지름
- $l$: 두 바퀴 사이의 거리
- $\omega_L$ 및 $\omega_R$: 좌우 바퀴의 각속도

### 차동 구동 운동 방정식

로봇의 위치 $(x, y)$와 방향 $\theta$는 다음과 같은 방정식으로 설명됩니다:

$$
v = \frac{r}{2}(\omega_R + \omega_L)
$$

$$
\omega = \frac{r}{l}(\omega_R - \omega_L)
$$

여기서:
- $v$는 로봇의 선속도입니다.
- $\omega$는 각속도(방향 $\theta$의 변화율)입니다.

차동 구동 로봇의 운동 방정식은 다음과 같습니다:

$$
\dot{x} = v \cos(\theta)
$$

$$
\dot{y} = v \sin(\theta)
$$

$$
\dot{\theta} = \omega
$$

### 순방향 및 역방향 운동학

차동 구동 시스템에서 **순방향 운동학**은 바퀴 속도를 기반으로 로봇의 속도 및 방향 변화를 계산하는 것을 의미합니다:

$$
v_x = r \frac{\omega_R + \omega_L}{2}
$$

$$
v_y = 0
$$

$$
\omega = r \frac{\omega_R - \omega_L}{l}
$$

반면 **역방향 운동학**은 원하는 로봇 속도 $v$와 각속도 $\omega$로부터 바퀴 속도 $\omega_R$와 $\omega_L$을 계산하는 과정입니다:

$$
\omega_R = \frac{v}{r} + \frac{l\omega}{2r}
$$

$$
\omega_L = \frac{v}{r} - \frac{l\omega}{2r}
$$

## 3. 운동학적 제약

자전거 모델과 차동 구동 모델 모두 운동학적 제약을 가집니다. 이러한 제약은 차량이나 로봇이 물리적 구조로 인해 임의의 방향으로 움직일 수 없다는 것을 반영합니다.

- **비홀로노믹 제약**: 차량은 옆으로 움직일 수 없으므로 측면 속도는 항상 0이어야 합니다. 이 제약은 수학적으로 다음과 같이 표현됩니다:

$$
\dot{y} \cos(\theta) - \dot{x} \sin(\theta) = 0
$$

이 제약은 제어 및 경로 계획 작업을 단순화하지만, 차량이 원하는 궤적을 따라가도록 하기 위해서는 정교한 제어 알고리즘이 필요합니다.

## 결론

자전거 모델과 차동 구동 모델과 같은 운동학 모델은 차량과 로봇이 평면에서 어떻게 움직이는지에 대한 중요한 통찰력을 제공합니다. 이러한 모델은 관성이나 마찰과 같은 동적 효과를 무시하지만, 실질적인 경로 계획과 제어에서 단순성과 효과로 인해 널리 사용됩니다.

더욱 정확한 모델링을 위해, 이러한 모델은 차량에 작용하는 힘과 모멘트를 포함한 동적 모델로 확장될 수 있습니다. -->
