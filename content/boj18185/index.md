---
emoji: 🧢
title: 백준 18185 라면 사기 (Small)
date: '2023-04-17 20:46:22'
author: jglee
tags: 백준 18185 그리디
categories: PS
---

## 문제 링크

- [https://www.acmicpc.net/problem/18185](https://www.acmicpc.net/problem/18185)

## 문제 출처

- 경기과학고등학교 > 나는코더다 2019 송년대회 B1번

## 사용 알고리즘

- 그리디

## 풀이

<br/>



<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;
int n;
int f[10010];

int main() {
  ios::sync_with_stdio(0);
  cin.tie(0);

  cin >> n;
  for (int i = 0; i < n; i++)
    cin >> f[i];

  int answer = 0;

  for (int i = 0; i < n; i++) {
    if (f[i] == 0) continue;
    if (f[i + 1] == 0) {
      answer += f[i] * 3;
      f[i] = 0;
      continue;
    } else {

      if (f[i + 1] > f[i + 2]) {
        int mn = min(f[i + 1] - f[i + 2], f[i]);
        answer += mn * 5;
        f[i] -= mn, f[i + 1] -= mn;
        if (f[i] != 0) {
          mn = min(f[i], f[i + 2]);
          answer += mn * 7;
          f[i] -= mn, f[i + 1] -= mn, f[i + 2] -= mn;
        }
        if (f[i] != 0) {
          answer += f[i] * 3;
          f[i] = 0;
        }
      } else {
        int mn = min(min(f[i], f[i + 1]), f[i + 2]);
        answer += mn * 7;
        f[i] -= mn, f[i + 1] -= mn, f[i + 2] -= mn;
        if (f[i] != 0) {
          answer += f[i] * 3;
          f[i] = 0;
        }
      }
    }
  }

  cout << answer;
}
```

</details>

<br/>

```toc

```