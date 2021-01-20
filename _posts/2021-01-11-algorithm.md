---
layout: post
title: 백준 알람 시계
subtitle: [TIL13 2884번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 문제

scanf를 통해 시간이 주어졌을 때 (0:0 ~ 23:59), 주어진 시각을 45분 이전으로 수정하여 출력한다.  
<br>

## 로직  

나는 두 가지의 경우로 나누어 생각하였다.

1. 분의 숫자가 **'45 이상'** 일 때

2. 분의 숫자가 **'45 미만'** 일 때  
<br>

### 분의 숫자가 45 이상  

1. 시간 : 받은 숫자 그대로 출력.

2. 분: 분의 숫자 - 45

3. 분 출력  
<br>

### 분의 숫자가 45 미만  

1. 시간: 시간의 숫자가 0인지 판별한다.(예외처리)

    1. 0(24시) ❌: 시간의 숫자에서 1을 뺄셈한다.

    2. 0(24시) ⭕️: 시간의 숫자를 23으로 치환해서 생각해야 하므로 1을 뺄셈하면 안된다.

2. 시간 출력 

3. 분: 60 - (45 - 분의 숫자)

4. 분 출력  
<br>

## 코드  

```c
#include <stdio.h>

int main(void)
{
    int h, m;
    
    h = m = 0;
    scanf("%d %d", &h, &m);
    if (m >= 45)
        printf("%d %d\n", h, m - 45);
    else
    {
        if (h == 0)
            printf("%d ", 23);
        else
            printf("%d ", h - 1);
        printf("%d\n", 60 - (45 - m));
    }
    return (0);
}
```  
<br>

## 링크  

[https://www.acmicpc.net/problem/2884](https://www.acmicpc.net/problem/2884)