---
layout: post
title: 백준 단어공부
subtitle: [TIL17 1157번]
thumbnail-img: ../images/algorithm.png
tags: [TIL, 알고리즘, C]
comments: true
---

## 문제

알파벳 대소문자로 된 단어가 주어지면, 이 단어에서 가장 많이 사용된 알파벳이 무엇인지 알아내는 프로그램을 작성하시오.  

단, 대문자와 소문자를 구분하지 않는다.  
<br>

유의해야 할 점

- 가장 많이 사용된 알파벳을 대문자로 출력한다.  

- 출력해야 할 알파벳이 여러개라면 '?' 를 출력한다.  
<br>

## 로직

아스키코드와 배열을 활용해서 풀어야 할 것같다.  
<br>

## 코드

```c
#include <stdio.h>
#include <string.h>

int main(void)
{
    int arr[255];
    int max, is_qmark;
    size_t len;
    char s[1000000], c;

    for (int i = 0; i < 255; i++)
        arr[i] = 0;
    scanf("%s", s);
    len = strlen(s);
    for (int i = 0; i < len; i++)
    {
        if (s[i] >= 97 && s[i] <= 122)
            s[i] -= 32;
        arr[s[i]]++;
    }
    max = arr[s[0]];
    c = s[0];
    for (int i = 0; i < len; i++)
    {
        if (max < arr[s[i]])
        {
            max = arr[s[i]];
            c = s[i];
        }
    }
    is_qmark = 0;
    for (int i = 0; i < len; i++)
    {
        if (max == arr[s[i]] && c != s[i])
            is_qmark++;
    }
    if (is_qmark)
        printf("?\n");
    else
        printf("%c\n", c);
    return (0);
}
```  


'?' 를 출력할 경우에서 코드도 길어지고 난잡해졌다. 그리고 시간복잡도 문제도 발생한 것같다.  

문제를 만만하게 봤는데, 사실은 내가 더 만만했다.  
<br>

## 링크

[https://www.acmicpc.net/problem/1157](https://www.acmicpc.net/problem/1157)