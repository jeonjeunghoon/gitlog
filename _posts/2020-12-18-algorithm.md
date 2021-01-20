---
layout: post
title: 백준 터렛
subtitle: [TIL07 1002번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---
## 문제

좌표 **x**와 **y** 그리고 거리 **r**이 주어진다.  

**r**은 **(x, y)**에서 부터 **(x', y')**까지의 길이이다.  

**(x1, y1)**, **(x2, y2)** 에서 **(x', y')**까지 측정한 길이를 각각 **r1, r2**라고 할 때, **(x3, y3)**가 위치해 있을 수 있는 **좌표의 수**를 구하시오.  
<br>

## 로직  

두 원의 위치 관계, 내접, 외접 등의 수학적 개념을 활용해 풀었다.  

원의 위치에 따라 생기는 경우의 수들을 처리하였다.  

큰 원의 반지름 = R, 작은 원의 반지름 = r, 두 원 사이의 거리 = dis  

1. 다른 원의 내부에 있고, 만나지 않을 경우

    R - r > dis

    교점 0개  
    <br>

2. 두 윈의 위치가 같고, 서로 만날 경우

    (x1 == x2) && (y1 == y2) && (r1 == r2)
    
    교점 무한개  
    <br>

3. 두 원이 서로 밖에 있고 만나지 않을 경우

    R + r < dis
    
    교점 0개  
    <br>

4. 두 원이 외접할 경우
    
    R + r == dis
    
    교점 1개  
    <br>

5. 두 원이 내접할 경우
    
    R - r = dis
    
    교점 1개  
    <br>

6. 두 원이 서로 다른 두 점에서 만날 경우

    R - r < dis < R + r
    
    교점 2개  
<br>

## 코드  
<br>

```c
#include <stdio.h>
#include <math.h>

int main(void)
{
    int t, x1, x2, y1, y2, r1, r2, R, r = 0;
    double dis, sum = 0;
    
    scanf("%d", &t);
    while (t--)
    {
        scanf("%d %d %d %d %d %d", &x1, &y1, &r1, &x2, &y2, &r2);
        dis = sqrt(pow(x1 - x2, 2) + pow(y1 - y2, 2));
        sum = r1 + r2;
				R = r1 > r2 ? r1 : r2;
				r = r1 < r2 ? r1 : r2;
        if ((x1 == x2) && (y1 == y2))
        {
            if (R != r)
                printf("%d\n", 0);
            else
                printf("%d\n", -1);
        }
				else if (dis > sum || (R > (r + dis)))
            printf("%d\n", 0);
        else if (dis == sum || (R == (r + dis)))
            printf("%d\n", 1);
        else if (dis > R - r && dis < R + r)
            printf("%d\n", 2);
    }
    return (0);
}
```  
<br>

## math.h  

- 다양한 수학적인 함수가 정의되어 있는 헤더 파일

- math.h 의 모든 함수의 인자와 반환 자료형은 double 로 받고, double 로 반환한다.

위 코드에 사용한 sqrt나 pow 같은 함수들은 math.h 헤더에 정의되어 있는 함수들이다.  
<br>

### pow: 제곱  

```c
double pow(double x, double y);
```  
<br>

인자 x의 y제곱을 반환하는 함수이다.

x = base

y = power  
<br>

### sqrt: 제곱근  

```c
double sqrt(double arg);
```  
<br>

인자의 제곱근을 반환하는 함수이다. 루트로 생각하면 되겠다.

만약 arg의 값이 음수일 경우, 지금 내 환경에서는 nan 이라는 값을 반환한다.  

아마 정의되지 않은 행동을 하는 것같다. ⇒ 음수를 넣어서 사용하면 제대로 작동하지 않는다.  
<br>

## 링크
[https://www.acmicpc.net/problem/1002](https://www.acmicpc.net/problem/1002)