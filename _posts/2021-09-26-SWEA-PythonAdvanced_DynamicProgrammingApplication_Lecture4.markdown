---
layout: post
title:  "SWEA - PythonAdvanced_DynamicProgrammingApplication_Lecture3 solution"
date:   2021-09-26 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5260. [파이썬 S/W 문제해결 최적화] 3일차 - 부분 집합의 합](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYNxvq3BIDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    N, K = map(int, input().split())

    numbers = list(range(1, N+1))

    # dp[i][j] : 1 ~ i의 숫자의 집합 중 합이 j인 부분집합의 개수
    dp = [[0 for _ in range((N*(N+1)//2)+1)] for _ in range(N+1)]
    dp[0][0] = 1

    for i in range(1, N+1):
        dp[i][0] = 1
        max_sum = i*(i+1)//2
        for j in range(1, max_sum+1):
            if j < i:                
                dp[i][j] = dp[i-1][j]
            else:
                dp[i][j] = dp[i-1][j] + dp[i-1][j-i]

    result = dp[N][K]
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

