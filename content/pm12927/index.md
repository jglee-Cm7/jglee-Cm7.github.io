---
emoji: 🧢
title: 프로그래머스 Lv.3 야근 지수
date: '2023-04-13 10:28:33'
author: jglee
tags: Programmers 프로그래머스 Lv.3 PS
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/12927](https://school.programmers.co.kr/learn/courses/30/lessons/12927)

## 문제 출처

- 프로그래머스 연습문제

## 사용 알고리즘

- 우선순위 큐

## 시간 복잡도

- O(NLogM)

## 풀이

<br/>

1. 제곱의 합을 최소화하기 위해서는 가장 큰 값을 줄이는게 포인트
2. 우선순위 큐를 이용, 작업량이 가장 큰 업무부터 1시간씩 처리한다

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>

using namespace std;

long long solution(int n, vector<int> works) {
    long long answer = 0;
    priority_queue<int> q(works.begin(), works.end());
    while(n--) {
        if(q.empty()) break; // 큐가 비었으면 종료.
        int v = q.top();
        q.pop();
        v--;
        if(v) q.push(v); // 완료되지 않은 작업만 큐에 등록.
    }
    while(!q.empty()) {
        int v = q.top();
        q.pop();
        answer += v*v;
    }

    return answer;
}
```

</details>

<br/>

```toc

```
