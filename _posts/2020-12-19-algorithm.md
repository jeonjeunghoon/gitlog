---
layout: post
title: 백준 피보나치 함수
subtitle: [TIL08 1003번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 문제
```c
int fibonacci(int n)
{
	if (n == 0)
	{
		printf("0");
		return (0);
	}
	else if (n == 1)
	{
		printf("1");
		return (1);
	}
	else
		return (fibonacci(n-1) + fibonacci(n-2));
}
```  
<br>
피보나치 함수에서 N이 주어 졌을 때 0과 1이 각각 몇 번 출력되는지 구하는 프로그램을 작성하라  
<br>

## 로직

1. 처음 떠오른 생각은 전역 변수를 사용해서 0과 1의 경우 마다 전역변수를 증가시켜 해결하는 방법을 생각했다.

2. 그러나 주어진 재귀함수를 활용하면 시간복잡도 때문에 시간초과로 실패한다.

3. 그래서 반복문으로 피보나치를 구하는 함수를 작성했다.

4. fibonacci(N)의 0과 1의 출력 횟수를 구하라고 하였는데, N과 출력 결과 사이에 유의미한 규칙성이 보인다.

5. 그러한 규칙성을 응용하여 문제를 해결한다.  
<br>

## 코드

```c
long long g_zero, g_one;

long long fibonacci(int n)
{
    long long ret, p1, p2 = 0;
    p2 = 1;

	if (n == 0)
        g_zero = 1;
	else if (n == 1)
        g_one = 1;
	else
    {
        for (int i = 0; i < n; i++)
        {
            ret = p1 + p2;
            g_zero = p1;
            g_one = p2;
            p1 = p2;
            p2 = ret;
        }
    }
    return (0);
}

int main(void)
{
    int t = 0;
    long long N = 0;
    scanf("%d", &t);
    while (t--)
    {
        g_zero = 0;
        g_one = 0;
        scanf("%lld", &N);
        fibonacci(N);
        printf("%lld %lld\n", g_zero, g_one);
    }
    return (0);
}
```  
<br>

## 피보나치 수열  

F0 = 0, F1 = 1, F(n+2) = F(n+1) + Fn
<br>

## 링크

[https://www.acmicpc.net/problem/1003](https://www.acmicpc.net/problem/1003)  