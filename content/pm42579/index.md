---
emoji: 🧢
title: 프로그래머스 Lv.3 베스트앨범
date: '2023-04-15 07:30:03'
author: jglee
tags: 프로그래머스 Lv.3 PS 해시
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/42579](https://school.programmers.co.kr/learn/courses/30/lessons/42579)

## 문제 출처

- 프로그래머스 해시 연습문제

## 사용 알고리즘

- 해시

## 풀이

<br/>
1. Map {장르, 장르 내 모든 플레이 시간} 로 장르별 전체 플레이 시간 저장 <br/>
2. Map {장르, Vector{플레이 시간, 플레이 고유번호}} 로 장르별 플레이 정보 저장 <br/>
3. 1번을 Vector 화 시킨 후 정렬 <br/>
4. 정렬된 장르로 2번에서 Vector{플레이 시간, 플레이 고유번호} 를 조회 <br/>
5. 4번에서 조회한 Vector를 플레이 시간에 대한 내림차순, 고유번호는 오름차순으로 정렬 <br/>
6. 정답 출력 <br/>
<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

vector<int> solution(vector<string> genres, vector<int> plays) {
    vector<int> answer;
    int n = genres.size();
    map<string, int> gtp; // {genre, total play}
    map<string, vector<pair<int, int>>> gp; // {genre, {play, index}}
    
    for(int i = 0; i < n; i++) {
        gtp[genres[i]] += plays[i];
        gp[genres[i]].push_back({plays[i], i});
    }
    
    vector<pair<int, string>> gr; // genre rank
    for(auto [key, value] : gtp) gr.push_back({value, key});
    sort(gr.begin(), gr.end(), greater<>());
    
    for(auto [tp, genre] : gr) {
        sort(gp[genre].begin(), gp[genre].end(), [](const auto a, const auto b) {
            if(a.first != b.first) return a.first > b.first;
            else return a.second < b.second;
        });
        int count = 0;
        for(auto [p, i] : gp[genre]) {
            if(count == 2) break;
            answer.push_back(i);
            count++;
        }
    }
    
    
    return answer;
}
```

</details>

<br/>

```toc

```