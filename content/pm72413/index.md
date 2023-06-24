---
emoji: 🧢
title: 프로그래머스 Lv.3 합승 택시 요금
date: '2023-04-28 07:42:22'
author: jglee
tags: 프로그래머스 Lv.3 PS 최단거리
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/72413](https://school.programmers.co.kr/learn/courses/30/lessons/72413)

## 문제 출처

- 2021 KAKAO BLIND RECRUITMENT

## 사용 알고리즘

- 플로이드-마셜, 다익스트라

## 풀이

<br/>
S -> 임의의 경유지 K <br/>
K -> A <br/>
K -> B <br/>
<br/>
모든 K에 대해 구한 후 최소값을 출력하면 된다. <br/>
<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>

using namespace std;

int solution(int n, int s, int a, int b, vector<vector<int>> fares) {
    vector<int> answer;
    vector<vector<int>> floyd(n + 1, vector<int>(n + 1, 0x3fffff));
    for(auto fare : fares) {
        floyd[fare[0]][fare[1]] = fare[2];
        floyd[fare[1]][fare[0]] = fare[2];
    }
    for(int i = 1; i <= n; i++)
        floyd[i][i] = 0;
    
    for(int k = 1; k <= n; k++) {
        for(int i = 1; i <= n; i++) {
            for(int j = 1; j <= n; j++)
                floyd[i][j] = min(floyd[i][j], floyd[i][k] + floyd[k][j]);
        }
    }
    for(int k = 1; k <= n; k++)
        answer.push_back(floyd[s][k] + floyd[k][a] + floyd[k][b]);
    
    return *min_element(answer.begin(), answer.end());
}
```

</details>

<br/>

```toc

```