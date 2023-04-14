---
emoji: 🧢
title: 프로그래머스 Lv.3 최고의 집합
date: '2023-04-13 10:11:24'
author: jglee
tags: Programmers 프로그래머스 Lv.3 PS
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/12938](https://school.programmers.co.kr/learn/courses/30/lessons/12938)

## 문제 출처

- 프로그래머스 연습문제

## 사용 알고리즘

- 구현

## 풀이

<br/>

1. 모든 원소가 같은 값을 가질 때, 모든 원소의 곱이 최대가 된다. (라그랑주 승수와 편미분으로 증명)
2. 원소의 값이 자연수이어야 하므로, 몫을 기본값으로 두고 나머지 값을 나눠서 배분한다.

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>

using namespace std;

vector<int> solution(int n, int s) {
    vector<int> answer;
    if(n > s) return {-1};

    int v = s/n;
    for(int i=0; i<n; i++) answer.push_back(v);

    s -= v*n;
    for(int i=0; i<s; i++) answer[n-i-1]++;

    return answer;
}
```

</details>

<br/>

```toc

```
