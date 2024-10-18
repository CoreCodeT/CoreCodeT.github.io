---
layout: single
title: "Vector"
categories: [linear algebra]
tag: [vector]
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

## Understanding Vectors
In mathematics and physics, a **vector** is a quantity that has both **magnitude** and **direction**. Vectors are commonly used to represent physical quantities such as velocity, force, and displacement.

## Vector Representation
Vector can be represented in two ways:
1. **bold**: $\mathbf{v}$
2. **With an arrow**: $\vec{v}$

Vector consists of two froms: **column from** and **row form**.
1. **Column form**:
   $$
   \mathbf{v} = \begin{pmatrix} v_1 \\ v_2 \\ v_3 \end{pmatrix}
   $$
2. **Row form**:
   $$
   \mathbf{v} = \begin{pmatrix} v_1, v_2, v_3 \end{pmatrix}
   $$

## Vector Operations
### 1. **Vector Addition**
The sum of two vectors $\mathbf{a}$ and $\mathbf{b}$ is given by:
$$
\mathbf{a} + \mathbf{b} = \begin{pmatrix} a_1 \\ a_2 \\ a_3 \end{pmatrix} + \begin{pmatrix} b_1 \\ b_2 \\ b_3 \end{pmatrix} = \begin{pmatrix} a_1 + b_1 \\ a_2 + b_2 \\ a_3 + b_3 \end{pmatrix}
$$   

### 2. **Scalar Multiplication**
Multiplying a vector $\mathbf{v}$ by a scalar $\lambda$ results in:
$$
\lambda \mathbf{v} = \lambda \begin{pmatrix} v_1 \\ v_2 \\ v_3 \end{pmatrix} = \begin{pmatrix} \lambda v_1 \\ \lambda v_2 \\ \lambda v_3 \end{pmatrix}
$$

### 3. **Dot Product (Scalar Product)**
The dot product of two vectors $\mathbf{a}$ and $\mathbf{b}$ is defined as:
$$
\mathbf{a} \cdot \mathbf{b} = a_1b_1 + a_2b_2 + a_3b_3
$$
Alternatively, in terms of magnitudes and the angle $\theta$ between the vectors:
$$
\mathbf{a} \cdot \mathbf{b} = |\mathbf{a}| |\mathbf{b}| \cos \theta
$$
The dot product results in a scalar.

### 4. **Cross Product (Vector Product)**
The cross product of two vectors $\mathbf{a}$ and $\mathbf{b}$ in 3D is given by:
$$
\mathbf{a} \times \mathbf{b} = \begin{vmatrix} \hat{i} & \hat{j} & \hat{k} \\ a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \end{vmatrix}
$$
This results in a new vector that is perpendicular to both $\mathbf{a}$ and $\mathbf{b}$, and its direction is given by the right-hand rule.

## Magnitude of a Vector

The magnitude (or length) of a vector $\mathbf{v} = \begin{pmatrix} v_1 \\ v_2 \\ v_3 \end{pmatrix}$ is given by:


$$
|\mathbf{v}| = \sqrt{v_1^2 + v_2^2 + v_3^2}
$$    

For example, in 2D, if $\mathbf{v} = \begin{pmatrix} 3, \\ 4 \end{pmatrix}$, the magnitude is:
$$
|\mathbf{v}| = \sqrt{3^2 + 4^2} = \sqrt{9 + 16} = 5
$$

## Unit Vector

A **unit vector** is a vector that has a magnitude of 1 and points in the direction of a given vector.   
The unit vector $\vec{\mathbf{v}}$ is calculated by:
$$
\vec{\mathbf{v}} = \frac{\mathbf{v}}{|\mathbf{v}|}
$$   
For example, if $\mathbf{v} = \begin{pmatrix} 3 \\ 4 \end{pmatrix}$ , the unit vector is:
$$
\vec{\mathbf{v}} = \frac{1}{5} \begin{pmatrix} 3 \\ 4 \end{pmatrix} = \begin{pmatrix} \frac{3}{5} \\ \frac{4}{5} \end{pmatrix}
$$

## Application of Vectors

Vectors have a wide range of applications in various fields:
- **Physics**: Representing force, velocity, acceleration.
- **Computer Graphics**: Modeling directions and positions in 3D space.
- **Engineering**: Structural analysis, fluid dynamics.
- **Machine Learning**: Representing data points in high-dimensional space.

## Conclusion
Vectors are a fundamental concept in mathematics and are used in many fields to describe quantities that have both direction and magnitude. By understanding vector operations such as addition, scalar multiplication, and dot/cross products, we can model and solve various real-world problems more effectively