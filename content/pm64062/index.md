---
emoji: 🧢
title: 프로그래머스 Lv.3 징검다리 건너기
date: '2023-04-20 08:43:01'
author: jglee
tags: 프로그래머스 Lv.3 PS 이분탐색 매개변수탐색
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/64062](https://school.programmers.co.kr/learn/courses/30/lessons/64062)

## 문제 출처

- 2019 카카오 개발자 겨울 인턴십

## 사용 알고리즘

- 이분 탐색, 매개변수 탐색

## 풀이

<br/>

배열의 크기를 n, 원소의 최대값을 m으로 둘 때 (n: 200,000 / m: 200,000,000)<br/>
완전 탐색으로 답을 도출하려면 시간복잡도가 O(nm) 이 소요되므로 시간 내에 도달할 수 없다.<br/>

최대값을 물어보는 최적화 문제를 결정 문제로 바꾸고 이분탐색으로 풀이할 시 O(n log m)의 시간복잡도로 답을 도출할 수 있다. <br/>

여기서 구해야할 최적값은 최대 니니즈가 몇명까지 지나갈 수 있는가이다. <br/>

이를 니니즈가 x명 지나갈 수 있을 때, k칸으로 가능한가? 를 확인하는 함수를 만들고 <br/>
이 함수의 매개변수(x)를 이분탐색으로 구한다. <br/>

매개변수 x가 될 수 있는 범위는 [1 ~ stones 배열의 최대값]이다. <br/>


<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>

using namespace std;

int getStep(vector<int> stones, int t) {
    int result = 0;
    int count = 0;
    for(int i=0; i<stones.size(); i++) {
        if(stones[i] - t > 0) {
            result = max(result, count);
            count = 0;
        } else count++;
    }
    result = max(result, count);
    return result;
}

int solution(vector<int> stones, int k) {
    int answer = 0;
    
    int s = 1;
    int e = *max_element(stones.begin(), stones.end());
    while(s <= e) {
        int mid = (s + e) / 2;
        if(getStep(stones, mid) < k) s = mid + 1;
        else e = mid - 1;
    }
    answer = e + 1;
    return answer;
}
```

</details>

<br/>

```toc

```