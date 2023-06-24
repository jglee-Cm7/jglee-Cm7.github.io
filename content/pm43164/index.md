---
emoji: 🧢
title: 프로그래머스 Lv.3 여행경로
date: '2023-04-27 20:36:38'
author: jglee
tags: 프로그래머스 Lv.3 PS 백트래킹
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/43164](https://school.programmers.co.kr/learn/courses/30/lessons/43164)

## 문제 출처

- 프로그래머스 깊이/너비 우선 탐색(DFS/BFS)

## 사용 알고리즘

- 백트래킹

## 시간 복잡도

- O(nm) (n: 도시의 개수, m: 하나의 도시에서 갈 수 있는 항공권의 개수)

## 풀이

<br/>

1. 출발/도착이 동일한 티켓도 있을 수 있음을 염두에 두고 모든 항공권을 사용했을 때 종료되는 조건으로 백트래킹을 수행하면 된다.
2. 조건을 만족하는 경로를 구하기 위해서 인접리스트를 구성한 후 정렬을 수행해주어야 한다.

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>

using namespace std;

int n;
map<string, vector<pair<string, bool>>> adj;

void func(int k, string st, vector<string>& answer) {
    if(k == n) return;
    
    for(auto& [en, used] : adj[st]) {
        if(used) continue;
        answer.push_back(en);
        used = true;
        func(k + 1, en, answer);
        if(answer.size() == n + 1) return;
        answer.pop_back();
        used = false;
    }
}

vector<string> solution(vector<vector<string>> tickets) {
    vector<string> answer;
    n = tickets.size();
    for(auto ticket: tickets)
        adj[ticket[0]].push_back({ticket[1], 0});
    
    for(auto& [key, value] : adj)
        sort(value.begin(), value.end());
    
    answer.push_back("ICN");
    func(0, "ICN", answer);
    
    return answer;
}
```

</details>

<br/>

```toc

```