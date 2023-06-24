---
emoji: 🧢
title: 프로그래머스 Lv.3 등굣길
date: '2023-04-13 16:32:49'
author: jglee
tags: 프로그래머스 Lv.3 PS DP
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/42898](https://school.programmers.co.kr/learn/courses/30/lessons/42898)

## 문제 출처

- 프로그래머스 동적계획법 기본문제

## 사용 알고리즘

- DP

## 풀이

<br/>

1. 좌표가 (n, m)이 아니라 (m, n)으로 표시되는 것에 주의
2. dp[i][j] = dp[i-1][j] + dp[i][j-1] (물웅덩이는 0으로 계산)

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

int solution(int m, int n, vector<vector<int>> puddles) {
    vector<vector<int>> dp(n+1, vector<int>(m+1, 0));
    dp[0][1] = 1;
    for(auto pos : puddles)
        dp[pos[1]][pos[0]] = -1;

    for(int i=1; i<=n; i++) {
        for(int j=1; j<=m; j++) {
            if(dp[i][j]) continue;
            int l = 0, u = 0;
            if(dp[i][j-1] != -1) l = dp[i][j-1];
            if(dp[i-1][j] != -1) u = dp[i-1][j];
            dp[i][j] = (l + u) % 1'000'000'007;
        }
    }

    return dp[n][m];
}
```

</details>

<br/>

```toc

```
