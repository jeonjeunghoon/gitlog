---
layout: post
title: 백준 숫자의 합
subtitle: [TIL19 11720번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 로직

숫자의 갯수를 주는 것을 보고 메모리 동적 할당을 이용해야 한다는 힌트를 얻었다.  
<br>

**char 형 배열을 선언한 이유**

타입마다 배열의 인자 한 칸에 저장할 수 있는 바이트 수가 다르기 때문이다.

- char 형 배열 안에 여러 숫자를 저장할 경우: 배열의 인자 한 칸에 숫자 하나씩 잘 들어간다.  

- int 형 배열 안에 여러 숫자를 저장할 경우: 배열의 인자 한 칸에 여러 숫자가 같이 들어간다.  
<br>

## 코드

```c
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	int n, sum = 0;
	char *arr;

	scanf("%d", &n);
	arr = malloc(sizeof(char) * n);
	scanf("%s", arr);
	for (int i = 0; i < n; i++)
		sum += arr[i] - '0';
	free(arr);
	printf("%d\n", sum);
	return (0);
}
```  
<br>

## 링크

[https://www.acmicpc.net/submit/11720/25426676](https://www.acmicpc.net/submit/11720/25426676)