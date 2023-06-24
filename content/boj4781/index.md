---
emoji: 🧢
title: 백준 4781 사탕 가게
date: '2023-04-17 20:43:19'
author: jglee
tags: 백준 4781 DP
categories: PS
---

## 문제 링크

- [https://www.acmicpc.net/problem/4781](https://www.acmicpc.net/problem/4781)

## 문제 출처

- 2012 Southeast USA Regional Programming Contest > Division 1 A번
- 2012 Southeast USA Regional Programming Contest > Division 2 A번

## 사용 알고리즘

- DP

## 풀이

<br/>



<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

int main() {
  ios::sync_with_stdio(0);
  cin.tie(0);

  while (1) {
    int n;
    double d;
    cin >> n >> d;
    if (n == 0) break;
    int m = (d * 100 + 0.5);
    vector<int> dp(m + 1, 0);
    vector<pair<int, int>> candy;
    for (int i = 0; i < n; i++) {
      int a;
      double b;
      cin >> a >> b;
      candy.push_back({a, (int)(b * 100 + 0.5)});
    }
    for (int i = 0; i < n; i++) {
      for (int j = 1; j <= m; j++) {
        auto [cal, price] = candy[i];
        if (j - price < 0) continue;
        dp[j] = max(dp[j], dp[j - price] + cal);
      }
    }

    cout << dp[m] << "\n";
  }
}
```

</details>

<br/>

```toc

```