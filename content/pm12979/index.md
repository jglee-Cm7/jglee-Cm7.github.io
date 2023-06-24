---
emoji: 🧢
title: 프로그래머스 Lv.3 기지국 설치
date: '2023-04-15 07:48:56'
author: jglee
tags: 프로그래머스 Lv.3 PS 구현
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/12979](https://school.programmers.co.kr/learn/courses/30/lessons/12979)

## 문제 출처

- 프로그래머스 Summer/Winter Coding(~2018)

## 사용 알고리즘

- 구현

## 시간 복잡도

- O(n) <br/>
- n 은 stations의 길이 <br/>

## 풀이

<br/>
1. 현재 기지국 상태에서 음영지역의 길이 정보를 Vector에 저장한다. <br/>
2. 음영지역을 다 덮을 수 있는 최소한의 기지국 개수를 계산한다. <br/>
<br/>
- 음영지역의 길이 / 기지국의 전파길이(2*W + 1) 에 나머지가 존재하면 + 1

<br/>
<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

int solution(int n, vector<int> stations, int w)
{
    int answer = 0;
    vector<int> shadow;
    
    int st = 0;
    for(int station : stations) {
        int en = station - w;
        int sd = en - 1 - st;
        if(sd > 0) shadow.push_back(sd);
        st = station + w;
    }
    if(st < n) shadow.push_back(n - st);
    
    for(int sd : shadow) {
        answer += sd / ((w*2) + 1);
        if(sd % ((w*2) + 1)) answer++;
    }

    return answer;
}
```

</details>

<br/>

```toc

```