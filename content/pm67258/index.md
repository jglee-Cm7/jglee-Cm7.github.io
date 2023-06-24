---
emoji: 🧢
title: 프로그래머스 Lv.3 보석 쇼핑
date: '2023-04-17 20:40:43'
author: jglee
tags: 프로그래머스 Lv.3 PS 해시 투포인터
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/67258](https://school.programmers.co.kr/learn/courses/30/lessons/67258)

## 문제 출처

- 2020 카카오 인턴십

## 사용 알고리즘

- 해시, 투포인터

## 풀이

<br/>



<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

vector<int> solution(vector<string> gems) {
    map<string, int> m;
    for(string gem : gems) m[gem]++;
    int count = m.size();
    vector<pair<int,int>> candi;
    
    map<string, int> t;
    int i = 0;
    int j = 0;
    for(; i < gems.size(); i++) {
        while(1) {
            if(t.size() == count) {
                candi.push_back({i+1, j});
                break;
            }
            if(j == gems.size()) break;
            t[gems[j++]]++;
        }
        t[gems[i]]--;
        if(t[gems[i]] == 0) t.erase(gems[i]);
    }
    
    i = 1, j = gems.size();
    for(auto [a, b] : candi)
        if(b-a < j-i || (b-a == j-i && a < i))
            i = a, j = b;
    return {i, j};
}
```

</details>

<br/>

```toc

```