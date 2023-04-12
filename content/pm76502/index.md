---
emoji: 🧢
title: 프로그래머스 Lv2 괄호 회전하기
date: '2023-04-12 18:25:00'
author: jglee
tags: programmers 프로그래머스 PS Lv2
categories: PS
---

## 문제 링크

[https://school.programmers.co.kr/learn/courses/30/lessons/76502](https://school.programmers.co.kr/learn/courses/30/lessons/76502)

## 문제 출처

프로그래머스 월간 코드 챌린지 시즌 2

## 사용 알고리즘

스택, 구현

## 풀이

<br/>

1. substr 로 문자열을 회전
2. 회전된 문자열의 괄호를 체크

<details>
<summary>코드 보기</summary>

```C
#include <bits/stdc++.h>
using namespace std;

bool check(string s) {
    stack<char> st;
    for(char c : s) {
        if(c == ')') {
            if(st.empty() || st.top() != '(') return 0;
            else st.pop();
        } else if(c == '}') {
            if(st.empty() || st.top() != '{') return 0;
            else st.pop();
        } else if(c == ']') {
            if(st.empty() || st.top() != '[') return 0;
            else st.pop();
        } else st.push(c);
    }
    if(!st.empty()) return 0;
    return 1;
}

int solution(string s) {
    int answer = 0;
    int n = s.length();
    for(int i=0; i<n; i++) {
        if(check(s.substr(i) + s.substr(0, i))) answer++;
    }
    return answer;
}
```

</details>

<br/>

```toc

```
