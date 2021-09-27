---
layout: post
title:  "SWEA - PythonAdvanced_DynamicProgrammingUtil_Lecture5 solution"
date:   2021-09-27 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5263. [파이썬 S/W 문제해결 최적화] 4일차 - 그래프 최소 비용](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYODN63DsDFAVT)

풀이

```python
import copy

def Floyd_Warshall(N, graph):

    dp = copy.deepcopy(graph)
    for i in range(N):
        for j in range(N):
            if i != j and dp[i][j] == 0:
                dp[i][j] = 100000

    for k in range(N):
        for i in range(N):
            for j in range(N):
                if i != j and j != k and i != k:
                    if dp[i][j] > dp[i][k]+dp[k][j]:
                        dp[i][j] = dp[i][k]+dp[k][j]

    return dp

T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())

    graph = [list(map(int, input().split())) for _ in range(N)]

    dp = Floyd_Warshall(N, graph)
    
    result = max(map(max, dp))
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

