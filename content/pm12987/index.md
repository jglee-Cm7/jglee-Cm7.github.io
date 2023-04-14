---
emoji: 🧢
title: 프로그래머스 Lv.3 숫자 게임
date: '2023-04-14 19:21:33'
author: jglee
tags: Programmers 프로그래머스 Lv.3 PS
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/12987](https://school.programmers.co.kr/learn/courses/30/lessons/12987)

## 문제 출처

- 프로그래머스 Summer/Winter Coding(~2018)

## 사용 알고리즘

- 투포인터

## 풀이

<br/>

A의 가장 큰 수를 B의 가장 작은 수에 허비하게 만든다고 생각하면 <br/>
(혹은 B의 가장 큰 수를 가장 효과적으로 이기는 경우만을 생각하면) 다음과 같이 해결할 수 있다.

다음과 같은 예제를 생각해보자 <br/>

A : 7 5 <span style="color:red">2</span> <span style="color:orange">1</span> <br/>
B : <span style="color:red">5</span> <span style="color:orange">4</span> 4 4 <br/>

B의 5와 A의 2 <br/>
B의 4와 A의 1 <br/>

이 경우가 무조건 일어나야한다. <br/>



1. A 와 B 배열 모두 내림차순으로 정렬
2. A팀 팀원이 이길 땐 A의 index만 진행
3. B팀 팀원이 이길 땐 A와 B index 모두 진행

<br/>

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

int solution(vector<int> A, vector<int> B) {
    int answer = 0;
    int n = A.size();
    sort(A.begin(), A.end(), greater<>());
    sort(B.begin(), B.end(), greater<>());
    int j = 0;
    for(int i = 0; i < n; i++) {
        if(A[i] >= B[j]) continue;
        else {
            answer++;
            j++;
        }
    }
    return answer;
}
```

</details>

<br/>

```toc

```