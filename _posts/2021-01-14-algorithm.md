---
layout: post
title: 백준 평균은 넘겠지
subtitle: [TIL16 4344번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 문제

대학교 학생들의 평균 점수를 넘는 학생들의 비율을 반올림하여 소숫점 셋째 자리까지 출력한다.  
<br>

## 로직

배열을 활용해서 문제를 해결해야 겠다는 생각을 했다.  
<br>

## 코드

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int t, n;
    float *arr, avg, res;
    
    t = n = 0;
    scanf("%d", &t);
    for (int i = 0; i < t; i++)
    {
        avg = res = 0.0f;
        scanf("%d", &n);
        arr = malloc(sizeof(float) * n);
        for (int j = 0; j < n; j++)
        {
            scanf("%f", &arr[j]);
            avg += arr[j];
        }
        avg /= n;
        for (int j = 0; j < n; j++)
        {
            if (arr[j] > avg)
                res++;
        }
				free(arr);
				res = (res / n) * 100;
        printf("%.3f%%\n", res);
    }
    return (0);
}
```  
<br>

## 링크

[https://www.acmicpc.net/problem/4344](https://www.acmicpc.net/problem/4344)