---
emoji: 🧢
title: 백준 12865 평범한 배낭
date: '2023-04-19 19:52:42'
author: jglee
tags: 백준 12865 DP
categories: PS
---

## 문제 링크

- [https://www.acmicpc.net/problem/12865](https://www.acmicpc.net/problem/12865)

## 문제 출처

- 

## 사용 알고리즘

- DP

## 풀이

<br/>
대표적인 0-1 냅색 문제 <br/>

n개의 짐이 있고, 배낭의 무게제한이 k 라고 한다면 <br/>
n * k 의 2차원 배열로 DP 풀이가 가능하다. <br/>

점화식은 다음과 같다. <br/>

i 가 짐의 인덱스 <br/>
w 는 i 번 짐의 무게 <br/>
v 는 i 번 짐의 가치 <br/>

dp[i][j] = max(dp[i-1][j], dp[i-1][j-w] + v)


<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;
int dp[105][100010];
int main() {
  ios::sync_with_stdio(0);
  cin.tie(0);
  int n, k;
  cin >> n >> k;
  vector<pair<int, int>> items;
  for (int i = 0; i < n; i++) {
    int w, v;
    cin >> w >> v;
    items.push_back({w, v});
  }
  for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= k; j++) {
      dp[i][j] = dp[i - 1][j];
      auto [w, v] = items[i - 1];
      if (j - w >= 0) dp[i][j] = max(dp[i][j], dp[i - 1][j - w] + v);
    }
  }

  cout << dp[n][k];
}
```

</details>

<br/>

```toc

```