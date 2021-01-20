---
layout: post
title: 백준 단어의 개수
subtitle: [TIL20 1152번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 문제

영어 대소문자와 띄어쓰기만으로 이루어진 문자열이 주어진다.  

이 문자열에는 몇 개의 단어가 있을까? 이를 구하는 프로그램을 작성하시오.  

단, 한 단어가 여러 번 등장한 횟수도 모두 세어야 한다.  
<br>

## 로직

처음엔 scanf로 문자열을 받아 띄어쓰기 나오는 구간을 기준점으로 잡아 단어 개수를 세어야 겠구나 라고 생각하고 로직을 작성했다.  

그런데 이상하게 자꾸만 반환값이 1개로 고정되어 나오길래 문자열을 살펴 보았더니, 띄어쓰기 이후의 문자열은 저장되지 않았다.  

그래서 이번 문제는 scanf의 반환값을 이용해 풀게 되었다.  
<br>

**반환값**

1. 입력 성공: 입력된 인자의 개수를 반환한다.

2. 입력 실패: 입력된 인자의 개수보다 적은 수를 반환하거나 0을 반환한다.

    - 0: 사용 가능한 입력이 있었지만 변환이 할당되지 않았음을 나타낸다.

3. 파일 종료 또는 입력 오류: EOF 반환 (-1)  
<br>

## 코드

```c
#include <stdio.h>

int main(void)
{
    char arr[1000001];
    int count, i;

	count = i = 0;
    while (scanf("%s", arr) != EOF)
	{
		count++;
		while (arr[i])
			i++;
	}
    printf("%d\n", count);
	return (0);
}
```  
<br>

## 링크

[https://www.acmicpc.net/problem/1152](https://www.acmicpc.net/problem/1152)