---
layout: post
title:  "SWEA - PythonAdvanced_DynamicProgrammingApplication_Lecture3 solution"
date:   2021-09-26 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5258. [파이썬 S/W 문제해결 최적화] 3일차 - 해피박스](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYNxvq3BIDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M = map(int, input().split())
    knapsack = [list(map(int, input().split())) for _ in range(M)]

    dp = [[set(), 0] for _ in range(N+1)] 

    for i in range(N+1):
        temp_max = 0
        temp_idx = -1
        if i > 8:
            a=0
        for j in range(M):
            if i - knapsack[j][0] >= 0:
                if j not in dp[i-knapsack[j][0]][0]:
                    if temp_max < dp[i-knapsack[j][0]][1] + knapsack[j][1]:
                        temp_max = dp[i-knapsack[j][0]][1] + knapsack[j][1]
                        temp_idx = j
        if temp_idx != -1:
            dp[i][0] = set(dp[i-knapsack[temp_idx][0]][0])
            dp[i][0].add(temp_idx)
            dp[i][1] = temp_max

    result = max(map(lambda x: x[1], dp))
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

