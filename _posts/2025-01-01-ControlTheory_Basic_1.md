---
layout: single
title: "Control Theory Basic - 1"
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

## 1. 제어 이론이란?
제어 이론(Control Theory)은 시스템의 <span style="color:blue"> 출력 </span>을 <span style="color:blue"> 원하는 목표</span>로 도달하도록 입력을 조절하는 방법을 연구하는 학문이다.    
일반적으로 <mark style='background-color: #dcffe4'> 출력(output)이 입력(input)을 따라가도록 제어 </mark>를 수행한다. 이 떄문에 <mark style='background-color: #dcffe4'> input을 desired output </mark>이라고 부르기도 한다.

## 2. 고전 제어와 현대 제어의 차이
고전 제어와 현대 제어는 여러 면에서 차이가 있으며, 각각의 특징은 아래와 같다.

### 2.1 고전 제어 이론 (Classical Control Theory)
- **주요 방법론**: 전달함수, 주파수응답 등을 고려하여 제어기를 개발
  - **전달 함수(Transfer Function)**: 입력과 출력 간의 관계를 표현
  - **주파수 응답(Frequency Response)**: Bode Plot, Nyquist Plot을 사용하여 시스템의 안정성과 성능을 분석
- **설계 기법**: Root Locus, Bode Plot, Nyquiest Plot 등을 활용하여 시스템의 안정성과 응답 특성을 설계
- **적용 대상**: 주로 단일 입력 단일 출력(SISO, Single Input Single Output) 시스템에 초점을 맞춤

### 2.2 현대 제어 이론 (Modern Control Theory)
- **주요 방법론**: 상태 공간 모델을 고려하여 제어기를 개발
  - **상태 공간 모델(State-Space Model)**: 시스템의 동적 특성을 상태 변수로 표현하여 다변수 시스템 해석에 유리
- **설계 기법**: LQR(Linear Quadratic Regulator), Kalman Filter, H∞ 제어와 같은 최적 제어 및 강인 제어 기법 사용
- **적용 대상**: 다중 입력 다중 출력(MIMO, Multiple Input Multiple Output) 시스템 및 복잡한 비선형 시스템에 효과적
