---
layout: post
title : Floating point
categories: Programming
tags: [FloatingPoint, DataType, IEEE754]
---



`Floating point`(부동소수점)이란 컴퓨터에서 실수를 표현하는 방법중에 하나이다.
특히 이 글에서는 `IEEE 754`의 2진 표기에 대해 알아본다.
(2진법에 대해서는 다른 글을 참조하라.)

# IEEE 754

## 부동소수점의 표현

부동소수점은 3가지 부분으로 나눠서 표현한다. (MLB부터 순서대로)
`sign`, `exponent`, `fraction` 각각 부호부, 지수부, 가수부를 뜻하는 말이다. 
또 `single precision`의 경우 32bit, `double precision`의 경우 64bit를 사용한다.


 |  | Sign | Exponent | Fraction|
 |--|----|--------|-------|
 |single precision| 1bit | 8bit | 23bit |
 |double precision| 1bit | 11bit| 52bit |


각각의 부분이 어떻게 저장되는지 적어보면 다음과 같이 표현할 수 있다.  
  
single precision: SEEEEEEE EFFFFFFF FFFFFFFF FFFFFFFF  
double precision: SEEEEEEE EEEEFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF FFFFFFFF

이제 각각의 부분에 대해서 좀더 살펴 보자.

### 부호부
부호를 나타내는 부분이다. (부동 소수점의 경우 절대값 부호화를 사용한다)


0일때 양수 1일때 음수를 뜻한다

### 지수부

부동소수점이라는 이름에 맞게 소수점을 움직여주는데, 그때 2의 거듭제곱을 이용해서 소수점을 옴직일 수 있다.

지수부는 2의 거듭제곱에서 지수를 나타내는 값으로 음수가 될수도 있고, 양수가 될 수도 있으므로 `bias`를 이용해서 양과 음을 모두 가지는 지수를 나타낸다
single precision(32bit)일 때 bias는 $2^7-1$이 된다.   
double precision(64bit)일 때 bias는 $2^{10}-1$이다.

지수부가 나타내는 수에서 bias를 뺀 값이 실제 지수가 된다.

### 가수부
가수부는 정규화 되어있다. 이 말은 2의 거듭제곱을 이용해서 같은 소수를 여러개의 형태로 나타낼 수 있는데 그중에서 소수점 왼쪽의 수가 1되게 했다는 뜻이다.
> **Example:** $101.111 \to 1.01111*2^2$

정규화가 되어있기 때문에 소수점 아래 부분만 지수부에 표현되어 있다.

### 2진수로 나타내기
다음과 같은 과정을 거쳐서 2진수로 나타낼 수 있다.

1. 부호부가 0이면 양수, 1이면 음수로 설정한다.
2. 가수부에 있는 값을 0.f로 바꿔준 다음 1을 더해준다.
3. 지수부의 수가 $a$라고 하면 $2^{a-bias}$를 곱해준다. (bias는 위에서 언급한 것과 같이 singleprecision에서 127, double precision에서 1023이다)

---

## 예외 규칙

### Denormalized
만약 지수부가 모두 0으로만 이루어져 있다면 다면 정규화 되지 않은것으로 생각을 한다.  

그리고 지수부는 single precision일때 $2^{-126}$이고 double precision일때 $2^{-1022}$가 된다.  

### 영
부호부를 제외한 모든 값이 0이 될때 +0, -0이 된다.  
주의할 점은 부호가 다른것은 개별적으로 존재하지만 비교하면 같다는 결과가 나온다.

### 무한
지수부가 모두 1이고 가수부가 모두 0이면 $+\infty$, $-\infty$가 된다

### 숫자가 아닌 것
NaN(not a number)는 지수부가 모두 1이지만 가수부가 모두 0이 아닌 것이다.


> 참조: [https://steve.hollasch.net/cgindex/coding/ieeefloat.html](https://steve.hollasch.net/cgindex/coding/ieeefloat.html)
