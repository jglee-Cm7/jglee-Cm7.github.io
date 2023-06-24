---
emoji: 🧢
title: 프로그래머스 Lv.3 스티커 모으기(2)
date: '2023-04-20 08:04:37'
author: jglee
tags: 프로그래머스 Lv.3 PS DP
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/12971](https://school.programmers.co.kr/learn/courses/30/lessons/12971)

## 문제 출처

- Summer/Winter Coding(~2018)

## 사용 알고리즘

- DP

## 풀이

<br/>

1. (1) 1번부터 떼는 경우와 (2) 2번 스티커부터 떼는 경우로 나눠서 생각한다.
2. (1)의 경우 n-2까지만 확인한다
3. (2)의 경우 n-1까지 확인한다

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <iostream>
#include <vector>
using namespace std;

int solution(vector<int> sticker)
{
    int answer = 0;
    int n = sticker.size();
    vector<int> dp(n+1, 0);
    vector<int> dp2(n+2, 0);
    if(n == 1) return sticker[0];
    
    for(int i=2; i<=n; i++)
        dp[i] = max(dp[i-1], dp[i-2] + sticker[i-2]);
    for(int i=3; i<=n+1; i++)
        dp2[i] = max(dp2[i-1], dp2[i-2] + sticker[i-2]);
    
    answer = max(dp[n], dp2[n+1]);

    return answer;
}
```

</details>

<br/>

```toc

```