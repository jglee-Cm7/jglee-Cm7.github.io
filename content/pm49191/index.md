---
emoji: 🧢
title: 프로그래머스 Lv.3 순위
date: '2023-05-17 11:41:33'
author: jglee
tags: 프로그래머스 Lv.3 PS 그래프
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/49191](https://school.programmers.co.kr/learn/courses/30/lessons/49191)

## 문제 출처

- 프로그래머스 그래프 기본문제

## 사용 알고리즘

- DFS / BFS

## 풀이

<br/>
1. A -> B를 이기고 B -> C를 이기면 A -> C를 이길 수 있다는 사실을 DFS 또는 BFS 순회에서 방문을 하느냐 못하느냐로 확인할 수 있다. <br/><br/>
2. 따라서 A가 모든 점을 방문할 수 있다면 A의 순위는 확정될 수 있다. <br/><br/>
3. 이기는 경우와 지는 경우 두 가지를 나누어서 순회하고, 그 결과를 같이 이용해야 한다. <br/><br/>

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;


void dfs(int v, vector<int> adj[], vector<bool>& vis) {
    vis[v] = 1;
    for(int nxt : adj[v]) {
        if(vis[nxt]) continue;
        dfs(nxt, adj, vis);
    }
}

int solution(int n, vector<vector<int>> results) {
    int answer = 0;
    vector<int> adjF[105];
    vector<int> adjB[105];
    for(auto result : results) {
        int a = result[0];
        int b = result[1];
        adjF[a].push_back(b);
        adjB[b].push_back(a);
    }

    for(int i=1; i<=n; i++) {
        vector<bool> visF(n+1, 0);
        dfs(i, adjF, visF);
        
        vector<bool> visB(n+1, 0);
        dfs(i, adjB, visB);
        
        bool check = true;
        for(int i=1; i<=n; i++) {
            if(!visF[i] && !visB[i]) {
                check = false;
                break;
            }
        }
        if(check) answer++;
    }
    
    return answer;
}
```

</details>

<br/>

```toc

```