---
title: "Linear Algebra"
date: 2023-06-04T20:40:59+08:00
draft: false
featuredImage: ""
description: ""
author: Louis LU
editor: ""
source: ""            # The source of the text
rights: ""            # Rights for this text
pageTitle:            # The title for the content w/o setting <title> tag
private: true         # Hide text from search engines
katex: true           # enable latex
tags:
  - "courses"
  - "linear algebra"
type: posts
toc: false            # enable it if you want to show the contents in the sidebar
semanticType: about   # Semantic type of the work (used for Schema.org)
annotations: false    # Disable annotation via hypothesis on this page
---

This post contains notes on the MIT OpenCourseWare Linear Algebra
[course](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/video_galleries/video-lectures/).

{{< toc >}}

## LECTURE 1: The Geometry of Linear Equations

* **Ax is a combination of the columns of A.**

$$
A = \begin{bmatrix} 2 & 5 \\\\ 1 & 2 \end{bmatrix},
x = \begin{bmatrix} 1 \\\\ 2 \end{bmatrix}
$$

$$
Ax =
\begin{bmatrix} 2 & 5 \\\\ 1 & 2 \end{bmatrix}
\begin{bmatrix} 1 \\\\ 2 \end{bmatrix} =
1 \begin{bmatrix} 2 \\\\ 1 \end{bmatrix} +
2 \begin{bmatrix} 5 \\\\ 2 \end{bmatrix} =
\begin{bmatrix} 12 \\\\ 7 \end{bmatrix}
$$

## LECTURE 2: Elimination with Matrices

### 2.1 Example Equations

$$
\begin{align*}
x + 2y + z &= 2 \\\\
3x + 8y + z &= 12 \\\\
4y + z &= 2
\end{align*}
$$

### 2.2 Elimination

#### 2.2.1 Success

$$
A =
\begin{bmatrix} 1 & 2 & 1 \\\\ 3 & 8 & 1 \\\\ 0 & 4 & 1 \end{bmatrix}
\underrightarrow{(2,1)} \begin{bmatrix} 1 & 2 & 1 \\\\ 0 & 2 & -2 \\\\ 0 & 4 & 1 \end{bmatrix}
\underrightarrow{(3,2)} \begin{bmatrix} 1 & 2 & 1 \\\\ 0 & 2 & -2 \\\\ 0 & 0 & 5 \end{bmatrix}
$$

Augmented matrix

$$
b =
\begin{bmatrix} 2 \\\\ 12 \\\\ 2 \end{bmatrix}
\rarr \begin{bmatrix} 2 \\\\ 6 \\\\ 2 \end{bmatrix}
\rarr \begin{bmatrix} 2 \\\\ 6 \\\\ -10 \end{bmatrix}
$$

$$
1^{st}\space pivot \rarr A_{1,1} \rarr 1
$$

$$
U \coloneqq \begin{bmatrix} 1 & 2 & 1 \\\\ 0 & 2 & -2 \\\\ 0 & 0 & 5 \end{bmatrix} \\\\
c \coloneqq \begin{bmatrix} 2 \\\\ 6 \\\\ -10 \end{bmatrix}
$$

#### 2.2.2 Failure

* Temporary failure: If a zero is encountered in the pivot position, we can perform a row exchange to rectify the situation.
* Complete failure: If a zero is encountered and there are no rows below it for exchange, the matrix is not invertible.

### 2.3 Back-Substitution

$$
\begin{align*}
x + 2y + z &= 2 \\\\
2y - 2z &= 6 \\\\
5z &= -10
\end{align*} \rarr
\begin{align*}
x &= 2 \\\\
y &= 1 \\\\
z &= -2
\end{align*}
$$


### 2.4 Matrices Multiplication

$$
\begin{align*}
matrix \times column &= matrix \\\\
row \times matrix &= row
\end{align*}
$$

$$
\begin{bmatrix} ? & ? & ? \\\\ ? & ? & ? \\\\ ? & ? & ? \end{bmatrix}
\begin{bmatrix} 1 & 2 & 1 \\\\ 3 & 8 & 1 \\\\ 0 & 4 & 1 \end{bmatrix} = 
\begin{bmatrix} 1 & 2 & 1 \\\\ 0 & 2 & -2 \\\\ 0 & 4 & 1 \end{bmatrix}
\rarr
\begin{bmatrix} 1 & 0 & 0 \\\\ -3 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix}
\begin{bmatrix} 1 & 2 & 1 \\\\ 3 & 8 & 1 \\\\ 0 & 4 & 1 \end{bmatrix} = 
\begin{bmatrix} 1 & 2 & 1 \\\\ 0 & 2 & -2 \\\\ 0 & 4 & 1 \end{bmatrix}
$$


#### 2.4.1 Elementary Matrix

> We call it **E** for **elementary** or **elimination**.

$$
\begin{align*}
E_{21} &\coloneqq \begin{bmatrix} 1 & 0 & 0 \\\\ -3 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix} \\\\
E_{32} &\coloneqq \begin{bmatrix} 1 & 0 & 0 \\\\ 0 & 1 & 0 \\\\ 0 & -2 & 1 \end{bmatrix}
\end{align*}
$$

* **Associative Law**

$$
\begin{align*}
E_{32}(E_{21}A) &= U \\\\
(E_{32}E_{21})A &= U
\end{align*}
\rarr E_{32}E_{21} =
\begin{bmatrix} 1 & 2 & 1 \\\\ 0 & 2 & -2 \\\\ 0 & 4 & 1 \end{bmatrix}
$$

#### 2.4.2 Permutation Matrix

* Exchange rows 1 and 2

$$
\begin{bmatrix} ? & ? \\\\ ? & ? \end{bmatrix}
\begin{bmatrix} a & b \\\\ c & d \end{bmatrix} = 
\begin{bmatrix} c & d \\\\ a & b \end{bmatrix}
\rarr
\begin{bmatrix} 0 & 1 \\\\ 1 & 0 \end{bmatrix}
\begin{bmatrix} a & b \\\\ c & d \end{bmatrix} = 
\begin{bmatrix} c & d \\\\ a & b \end{bmatrix}
$$

> We call it **P** for **permutation**.

$$
P \coloneqq \begin{bmatrix} 0 & 1 \\\\ 1 & 0 \end{bmatrix} 
$$

#### 2.4.3 Column Operations

> To do column operations, the matrix multiples on the right.
> To do row operations, it multiples on the left.

$$
\begin{bmatrix} a & b \\\\ c & d \end{bmatrix}
\begin{bmatrix} ? & ? \\\\ ? & ? \end{bmatrix} = 
\begin{bmatrix} b & a \\\\ d & c \end{bmatrix}
\rarr
\begin{bmatrix} a & b \\\\ c & d \end{bmatrix}
\begin{bmatrix} 0 & 1 \\\\ 1 & 0 \end{bmatrix} = 
\begin{bmatrix} b & a \\\\ d & c \end{bmatrix}
$$

* **NO commutaitive law**: AB != BA

#### 2.4.4 Inverses Preview

* Q: How do you get from U back to A?
* A: _The inverse matrix._

$$
\begin{bmatrix} ? & ? & ? \\\\ ? & ? & ? \\\\ ? & ? & ? \end{bmatrix}
\begin{bmatrix} 1 & 0 & 0 \\\\ -3 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix} = 
\begin{bmatrix} 1 & 0 & 0 \\\\ 0 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix}
\rarr
\begin{bmatrix} 1 & 0 & 0 \\\\ 3 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix}
\begin{bmatrix} 1 & 0 & 0 \\\\ -3 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix} = 
\begin{bmatrix} 1 & 0 & 0 \\\\ 0 & 1 & 0 \\\\ 0 & 0 & 1 \end{bmatrix}
$$

$$
\rarr E^{-1}E=I
$$
