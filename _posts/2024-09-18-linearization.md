---
layout: single
title: "Linearization"
categories: [linear algebra] 
tag: [linear, control]
toc: true
toc_sticky: true
toc_label: 목차
author_profile: true
use_math: true
sidebar: 
    nav: "docs"
search: true # 이러면 search 안됨
sidebar:
    nav: "counts"
# redirect_from:
#     - /coding/first3 # 또다른 url을 추가하는 방법
---

## 선형화(Linearization)란?
**선형화(Linearization)**는 비선형 시스템을 선형 방정식으로 근사하는 기법이다.  
복잡한 시스템을 다룰 때 유용하며, 비선형적인 동작을 분석하는 대신 특정 평형점 근처에서 시스템을 선형적으로 근사하여 분석할 수 있다.
특히, 많은 제어 기법들이 선형 시스템을 대상으로 하고 있다.   
물론 비선형 시스템을 대상으로 하는 제어 기법도 많이 존재하지만, 비선형 시스템 기반의 제어 방법이 반드시 선형 시스템 기반의 제어 방버보다 좋다고할 수는 없다.

어떤 비선형 함수 $f(x)$가 있을 때, 선형화는 특정 점 $x_0$ 근처에서 이 함수를 **1차 테일러 급수(Taylor expansion)**를 사용하여 근사하는 과정이다. 이를 통해 **선형적으로 근사화된 함수**를 얻을 수 있다.

## 1. 일변수 함수(Single-Variable function)의 선형화 ## 
단일 변수 함수 $f(x)$에 대해, 점 $x_0$에서의 선형 근사는 다음과 같이 표현할 수 있다.  
식 (1)은 가장 기본이 되며, 다변수 함수의 선형화, 동적 시스템에서의 선형화로 확장이 가능하다.

$$
\begin{align}
f(x) \approx f(x_0) + f'(x_0)(x - x_0) \tag{1}
\end{align}
$$

### ex1) 비선형 함수의 선형화 예시
비선형 함수 $f(x) = \sin(x)$를 점 $x_0 = 0$에서 선형화를 한다면,

1. **함수 값을 $x_0 = 0$에서 계산:**

   $$
   \begin{align}
   f(0) = \sin(0) = 0 \tag{1-1}
   \end{align}
   $$

2. **함수의 미분값을 계산:**

   $$
   \begin{align}
   f'(x) = \cos(x), \quad f'(0) = \cos(0) = 1 \tag{1-2}
   \end{align}
   $$

3. **선형 근사:**

   선형화 식을 사용하여:
   $$
   f(x) \approx f(0) + f'(0)(x - 0) = 0 + 1 \cdot x = x \tag{1-3}
   $$

따라서 $\sin(x)$는 $x = 0$ 근처에서 $x$로 근사할 수 있다.

## 2.다변수 함수(Multivariable function)의 선형화
일변수 함수의 선형화를 다변수 함수로 확장해 보자.  
다변수 함수의 선형화는 여러 입력 변수를 가지는 비선형 시스템을 특정 점에서 **선형 방정식으로 근사하는 기법**이다.

비선형 함수 $f(\mathbf{x})$는 여러 변수 $\mathbf{x} = (x_1, x_2, \dots, x_n)$를 포함하는 함수라고 해보자.    
선형화는 특정 점 $\mathbf{x}_0$ 근처에서 이 함수를 **1차 테일러 급수(Taylor expansion)**를 사용하여 근사할 수 있다.

다변수 함수 $f(\mathbf{x})$를 점 $\mathbf{x}_0$에서 선형화하면 다음과 같이 표현할 수 있다.

$$
\begin{align}
f(\mathbf{x}) \approx f(\mathbf{x}_0) + \nabla f(\mathbf{x}_0) \cdot (\mathbf{x} - \mathbf{x}_0) \tag{2}
\end{align}
$$

여기서:
- $f(\mathbf{x}_0)$는 $\mathbf{x}_0$에서의 함수 값,
- $\nabla f(\mathbf{x}_0)$는 $\mathbf{x}_0$에서의 gradient vector(각 변수에 대한 편미분으로 이루어진 벡터),
- $\mathbf{x} - \mathbf{x}_0$는 점 $\mathbf{x}_0$로부터 $\mathbf{x}$까지의 거리,
- $\cdot$는 내적(dot product)을 의미한다.

### ex2) 비선형 함수의 선형화 예시

비선형 함수 $f(x_1, x_2) = x_1^2 + x_2^2$를 점 $(x_1, x_2) = (1, 2)$에서 선형화한다면,

1. **함수 값 계산**:

   점 $(1, 2)$에서 함수 $f(x_1, x_2)$의 값을 계산하면,

   $$
   \begin{align}
   f(1, 2) = 1^2 + 2^2 = 1 + 4 = 5 \tag{2-1}
   \end{align}
   $$

2. **기울기 계산**:

   각 변수 $x_1$과 $x_2$에 대한 편미분을 계산하면,

   $$
   \begin{align}
   \frac{\partial f}{\partial x_1} = 2x_1, \quad \frac{\partial f}{\partial x_2} = 2x_2 \tag{2-2}
   \end{align}
   $$

   점 $(1, 2)$에서 기울기 벡터를 구하면,

   $$
   \begin{align}
   \nabla f(1, 2) = \left( 2 \cdot 1, 2 \cdot 2 \right) = (2, 4) \tag{2-3}
   \end{align}
   $$

3. **선형 근사**:

   점 $(1, 2)$에서의 선형 근사는 다음과 같다.

   $$
   \begin{align}
   \begin{split}
   f(x_1, x_2) & \approx f(1, 2) + \nabla f(1, 2) \cdot \left( \begin{pmatrix} x_1 \\ x_2 \end{pmatrix} - \begin{pmatrix} 1 \\ 2 \end{pmatrix} \right)\\
   & \approx 5 + (2, 4) \cdot \begin{pmatrix} x_1 - 1 \\ x_2 - 2 \end{pmatrix}\\
   & \approx 5 + 2(x_1 - 1) + 4(x_2 - 2)\\
   & \approx 5 + 2x_1 - 2 + 4x_2 - 8\\
   & \approx 2x_1 + 4x_2 - 5
   \end{split}\tag{2-4}
   \end{align}
   $$


따라서, $f(x_1, x_2) = x_1^2 + x_2^2$는 점 $(1, 2)$ 근처에서 선형화는 다음과 같다.

$$
\begin{align}
f(x_1, x_2) \approx 2x_1 + 4x_2 - 5 \tag{2-5}
\end{align}
$$
   
Fig .1은 선형 및 비선형 함수의 그래프를 나타낸 그림이다. 선형화한 함수는 $(1, 2)$에서 접하는 것을 알 수 있다.
<center>
<img src="https://www.dropbox.com/scl/fi/9kkrdr4a6qddyrppmhtke/A1_Linearization_Polynomial_1_.jpg?rlkey=k3r4zufv10ou694njl3ia9qik&st=ecg40qun&dl=1" width = "500" height = "500">    
</center>

<center>
Fig 1. 선형 및 비선형 함수의 그래프
</center>


## 3. 동적 시스템의 선형화

제어 이론 및 동적 시스템에서는 비선형 시스템이 다음과 같은 $\dot{\mathbf{x}} = \mathbf{f}(\mathbf{x}, \mathbf{u})$ 으로 표현할 수 있다.   
여기에서 $\mathbf{x}$는 상태 벡터, $\mathbf{u}$는 입력 벡터, $\mathbf{f}$는 비선형 함수를 의미한다.


시스템을 평형점 $\mathbf{x}_0, \mathbf{u}_0$ 근처에서 선형화할 수 있으며, 선형화된 시스템은 다음과 같이 표현할 수 있다.

$$
\dot{\mathbf{x}} \approx A \mathbf{x} + B \mathbf{u} \tag{3}
$$

여기서:      
$$A = \frac{\partial \mathbf{f}}{\partial \mathbf{x}} \Big|_{\mathbf{x} = \mathbf{x}_0, \mathbf{u} = \mathbf{u}_0} \tag{3-1}$$
$$B = \frac{\partial \mathbf{f}}{\partial \mathbf{u}} \Big|_{\mathbf{x} = \mathbf{x}_0, \mathbf{u} = \mathbf{u}_0} \tag{3-2}$$

### ex3) 동적시스템 선형화 예시

비선형 함수 $\dot{x} = f(x, u) = x^2 + u$를 점 $x_0 = 0$과 $u_0 = 0$에서 선형화한다면,

1. **편미분 계산:**

   $$
   A = \frac{\partial f}{\partial x} = 2x, \quad B = \frac{\partial f}{\partial u} = 1 \tag{3-3}
   $$

2. **평형점에서 선형화된 시스템:**

   $$
   A = 2 \cdot 0 = 0, \quad B = 1 \tag{3-4}
   $$

따라서, $x_0 = 0$과 $u_0 = 0$ 근처에서 선형화된 시스템은 아래와 같이 표현할 수 있다.

$$
\dot{x} \approx 0 \cdot x + 1 \cdot u = u \tag{3-5}
$$
