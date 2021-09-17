---
layout: post
title:  "SWEA - PythonAdvanced_DynamicProgramming_Lecture6 solution"
date:   2021-09-17 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5256. [파이썬 S/W 문제해결 최적화] 2일차 - 이항계수](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYNNbK29EDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    n, a, b = map(int, input().split())

    dp = [[1 for _ in range(n+1)] for _ in range(n+1)]
    
    # nCr = n-1Cr-1 + n-1Cr
    for i in range(1, n+1):
        for j in range(1, i):
            dp[i][j] = dp[i-1][j-1] + dp[i-1][j]

    result = dp[n][a]
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

