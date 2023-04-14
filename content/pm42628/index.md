---
emoji: 🧢
title: 프로그래머스 Lv.3 이중우선순위큐
date: '2023-04-13 10:03:50'
author: jglee
tags: programmers 프로그래머스 PS Lv.2
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/42628](https://school.programmers.co.kr/learn/courses/30/lessons/42628)

## 문제 출처

- Heap 기본문제

## 사용 알고리즘

- 힙

## 풀이

<br/>

1. MIN, MAX 두개의 우선순위 큐를 생성
2. 두 큐의 개수를 동기화시킨다.

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

vector<int> solution(vector<string> operations) {
    vector<int> answer;
    priority_queue<int> q1;
    priority_queue<int, vector<int>, greater<int>> q2;
    int cnt = 0;

    for(string op : operations) {
        char code = op[0];
        int v = stoi(op.substr(2));
        if(code == 'I') q1.push(v), q2.push(v), cnt++;
        else if(code == 'D') {
            if(!q1.empty() && v == 1) q1.pop(), cnt--;
            else if(!q2.empty() && v == -1) q2.pop(), cnt--;
        }
        if(!cnt) {
            q1 = priority_queue<int>();
            q2 = priority_queue<int, vector<int>, greater<int>>();
        }
    }
    if(q1.empty()) answer.push_back(0);
    else answer.push_back(q1.top());

    if(q2.empty()) answer.push_back(0);
    else answer.push_back(q2.top());

    return answer;
}
```

</details>

<br/>

```toc

```
