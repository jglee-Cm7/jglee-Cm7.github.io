---
emoji: 🧢
title: 프로그래머스 Lv.3 불량 사용자
date: '2023-04-17 08:55:00'
author: jglee
tags: 프로그래머스 Lv.3 PS 백트래킹 순열과조합
categories: PS
---

## 문제 링크

- [https://school.programmers.co.kr/learn/courses/30/lessons/64064](https://school.programmers.co.kr/learn/courses/30/lessons/64064)

## 문제 출처

- 2019 카카오 개발자 겨울 인턴십

## 사용 알고리즘

- 백트래킹, 순열과 조합

## 풀이

<br/>

해시만 가지고 해결하려다가 실패하고 잊혀져가던 백트래킹을 다시 복기하게된 문제이다. <br/>

1. 유저리스트를 n 개, 제재리스트랑 m 개로 볼 때, n 개 중 m 개를 뽑는다. <br/>
    - 뽑힌 조합의 순서를 바꾸면 가능한 경우가 생기기 때문에 이를 순열로 확인한다. <br/>
2. 뽑은 유저 리스트가 차단 리스트의 순서에 맞게 매칭이 되면 카운트 증가 <br/>
3. 중복되는 모든 경우를 제거한다. (가지치기) <br/>

<br/>

<details>
<summary>백트래킹 코드 보기</summary>

```C
#include <bits/stdc++.h>

using namespace std;

bool used[10];
set<string> cs;
set<string> ans;

bool match(string a, string x) {
    bool result = true;
    if(a.length() != x.length()) return false;
    for(int i=0; i<a.length(); i++) {
        if(x[i] == '*') continue;
        if(a[i] != x[i]) return false;
    }
    return true;
}

void func(int k, vector<string> user_id, vector<string> banned_id) {
    if(k == banned_id.size()) {
        string s = "";
        for(string c : cs) s += c + " ";
        ans.insert(s); // 매칭된 유저 리스트의 중복 제거를 위해 set의 성질을 사용한다.
        return;
    }
    
    for(int i=0; i<user_id.size(); i++) {
        if(used[i]) continue;
        if(match(user_id[i], banned_id[k])) {
            used[i] = 1;
            cs.insert(user_id[i]);
            func(k+1, user_id, banned_id);
            cs.erase(user_id[i]);
            used[i] = 0;
        }
    }
}

int solution(vector<string> user_id, vector<string> banned_id) {
    int answer = 0;
    
    func(0, user_id, banned_id);
    answer = ans.size();
    
    return answer;
}
```
</details>

<br/>

<details>
<summary>C++ permutation 을 사용한 코드</summary>

```C

#include <bits/stdc++.h>

using namespace std;

bool match(string a, string x) {
    bool result = true;
    if(a.length() != x.length()) return false;
    for(int i=0; i<a.length(); i++) {
        if(x[i] == '*') continue;
        if(a[i] != x[i]) return false;
    }
    return true;
}

int solution(vector<string> user_id, vector<string> banned_id) {
    vector<int> comb(user_id.size() - banned_id.size(), 0);
    for(int i=0; i<banned_id.size(); i++) comb.push_back(1);
    int answer = 0;
    vector<vector<string>> picked;
    do {
        vector<string> candi;
        for(int i=0; i<comb.size(); i++)
            if(comb[i]) candi.push_back(user_id[i]);
        
        
        sort(candi.begin(), candi.end()); // 정렬하지 않으면, 일부 순열의 케이스가 누락된다.
        do {
            bool success = true;
            for(int i=0; i<candi.size(); i++) {
                if(match(candi[i], banned_id[i])) continue;
                success = false;
                break;
            }
            if(success) {
                answer++;
                break;
            }
        } while(next_permutation(candi.begin(), candi.end())); // 뽑힌 케이스의 모든 경우의 수(순열)을 확인해서 가능한지 체크한다.
        
    } while(next_permutation(comb.begin(), comb.end())); // banned 개수 만큼 선택
    
    return answer;
}
```

</details>

<br/>

```toc

```