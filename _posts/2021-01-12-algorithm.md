---
layout: post
title: 백준 A + B (4)
subtitle: [TIL14 10951번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 문제

두 정수 A와 B를 입력 받은 다음, A+B를 출력하는 프로그램을 작성하시오  
<br>

## 로직  

문제에서 입력 데이터의 끝을 나타내는 표식은 따로 없다.

또한 이 문제는 EOF(파일의 끝)을 판단할 수 있어야 한다. 그래서 몇 줄이 주어지는 지에 대한 정보는 없다.

scanf함수는 읽은 변수의 수를 반환한다. 그래서 만약 읽은게 아무 것도 없다면 0 혹은 에러나 파일의 끝을 도달한다면 -1 (EOF)를 반환한다.

이러한 성질을 이용해 코드를 구현한다.  
<br>

## 코드  

```c
#include <stdio.h>

int main(void)
{
    int a, b;
    
    while ((scanf("%d %d", &a, &b) != EOF))
		printf("%d\n", a + b);
	return (0);
}
```  
<br>

## 링크  

[https://www.acmicpc.net/board/view/39199](https://www.acmicpc.net/board/view/39199)