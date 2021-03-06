---
title: Friedberg 선형대수학 문제 풀이
categories: Friedberg
tage: [선형대수학]
comments: true
---

1. 평행한지 조사하라

(a). (3,1,2) and (6,4,2) - X 

(b). (-3,1,7) and (9,-3,-21) - O

(c). (5,-6,7) and (-5,6,-7) - O

(d). (2,0,-5) and (5,0,-2) - X

2. 두 점을 지나는 방정식을 찾아라

(a). (3,-2,4) and (-5,7,1)

$$
v = (-5,7,1) - (3,-2,4) = (-8,9,-3) \\
(x,y,z) = p_{0}+tv = (-5,7,1)+t(-5,7,1)
$$

3. 세 점을 지나는 방정식을 찾아라

(a) (2,-5,-1), (0,4,6) and (-3,7,1)

$$
X=x_{0}+t_{1}((0,4,6)-(2,-5,-1)) + t_{2}((-3,7,1)-(2,-5,-1)) \\ = (2,-5,-1) + t_{1}(-2,9,7) + t_{2}(-5,12,2)
$$

6. (a,b)와 (c,d)의 중앙이 ((a + c)/2, (b + d)/2)임을 보여라

* ((a + c)/2, (b + d)/2)는 (a,b)와 (c,d)를 지나는 직선 위에 있다

$$
y = \frac{d-b}{c-a}(x-a)+b \\
\frac{b+d}{2} = \frac{d-b}{c-a}(\frac{a+c}{2}-a)+b \\
=\frac{(d-b)(a+c)}{2(c-a)} - a\frac{d-b}{c-a}+b \\
= \frac{(d-b)(a+c)}{2(c-a)} - \frac{2a(d-b)}{2(c-a)}+b \\
= \frac{(d-b)(a+c)-2a(d-b)}{2(c-a)}+b \\
= \frac{(d-b)(a+c-2a)}{2(c-a)}+b \\
= \frac{(d-b)(c-a)}{2(c-a)}+b \\
= \frac{(d-b)}{2}+b \\
= \frac{d-b+2b}{2} \\
= \frac{b+d}{2}
$$

* (a,b)와 ((a + c)/2, (b + d)/2), ((a + c)/2, (b + d)/2)와 (c,d)사이의 거리가 동일하다

$$
\sqrt{(\frac{a+c}{2}-a)^2+(\frac{b+d}{2}-b)^2} = \sqrt{(c-\frac{a+c}{2})^2+(d-\frac{b+d}{2})^2}\\
(\frac{a+c}{2}-a)^2+(\frac{b+d}{2}-b)^2 = (c-\frac{a+c}{2})^2+(d-\frac{b+d}{2})^2 \\
(\frac{a+c}{2})^2-2a\frac{a+c}{2}+a^2+(\frac{b+d}{2})^2-2b\frac{b+d}{2}+b^2=
c^2-2c\frac{a+c}{2}+(\frac{a+c}{2})^2+d^2-2d\frac{b+d}{2}+(\frac{b+d}{2})^2 \\
-2a\frac{a+c}{2}+a^2-2b\frac{b+d}{2}+b^2=
c^2-2c\frac{a+c}{2}+d^2-2d\frac{b+d}{2} \\
2(c-a)\frac{a+c}{2}+2(d-b)\frac{b+d}{2}=c^2-a^2+d^2-b^2 \\
(c-a)(a+c)+(d-b)(b+d)=c^2-a^2+d^2-b^2 \\
c^2-a^2+d^2-b^2
$$

1. 참과 거짓을 판단하라

* (a) 모든 벡터 공간은은 영벡터를 포함 한다 - O
* (b) 벡터 공간은 둘 이상의 영벡터를 가질 수 있다 - X
* (c) 어떤 벡터 공간에서 $ax=bx$가 $a=b$를 내포합니다 - X
* (d) 어떤 벡터 공간에서 $ax=ay$가 $x=y$를 내포합니다 - X
* (e) $F^n$의 벡터 $A$는 행렬 $M_{n\times1}(F)$로 간주할 수 있다 - O
* (f) $m\times n$ 행렬은 $m$열과 $n$행을 가지고 있다 - X
* (g) P$(F)$에서는 같은 차수의 다항식만 더할할 수 있습니다.
* (h) $f$와 $g$가 n차 다항식이면, $f+g$는 n차 다항식입니다. - O
* (i) $f$가 n차 다항식이고, $c$가 0이 아닌 스칼라면, $cf$는 n차 다항식이다 - O
* (j) 0이 아닌 스칼라는 0차 다항식으로 간주 될 수 있다 -O
* (k) $\mathcal{F}(S,F)$에 속하는 두 함수는 S의 각 요소에서 동일한 값을 갖는 경우에만 같습니다. - ?

2. 영벡터 $M_{3\times4}(F)$를 적어라

$$
\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$

3. 만약

$$
M=
\begin{pmatrix}
1&2&3 \\
4&5&6
\end{pmatrix}
$$
일때 $M_{13},M_{21},M_{22}$는?

3,4,5

5. 