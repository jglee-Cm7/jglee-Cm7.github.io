---
emoji: 🧢
title: 프로그래머스 Lv.3 가장 먼 노드
date: '2023-04-20 09:08:40'
author: jglee
tags: 프로그래머스 Lv.3 PS 그래프 BFS
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/49189](https://school.programmers.co.kr/learn/courses/30/lessons/49189)

## 문제 출처

- 그래프 기본예제

## 사용 알고리즘

- BFS

## 풀이

<br/>

1. 최단 경로 이동 문제이므로 BFS 로 정점의 방문 순서를 기록
2. 가장 먼 거리의 값이 몇개 인지 체크한다.

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

int solution(int n, vector<vector<int>> edge) {
    int answer = 0;
    vector<vector<int>> adj(n+1);
    vector<int> vis(n+1);
    for(auto e : edge) {
        adj[e[0]].push_back(e[1]);
        adj[e[1]].push_back(e[0]);
    }
    
    queue<int> q;
    q.push(1);
    vis[1] = 1;
    while(!q.empty()) {
        int cur = q.front();
        q.pop();
        for(int nxt : adj[cur]) {
            if(vis[nxt]) continue;
            vis[nxt] = vis[cur] + 1;
            q.push(nxt);
        }
    }
    
    int mx = *max_element(vis.begin(), vis.end());
    answer = count(vis.begin(), vis.end(), mx);
    
    return answer;
}
```

</details>

<br/>

```toc

```