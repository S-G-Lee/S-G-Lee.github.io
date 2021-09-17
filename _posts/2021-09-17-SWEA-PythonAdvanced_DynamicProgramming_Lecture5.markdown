---
layout: post
title:  "SWEA - PythonAdvanced_DynamicProgramming_Lecture5 solution"
date:   2021-09-17 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5255. [파이썬 S/W 문제해결 최적화] 2일차 - 타일 붙이기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYNNbK29EDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())

    dp = [0] * (N+1)
    dp[1] = 1
    dp[2] = 3
    dp[3] = 6

    for i in range(4, N+1):
        dp[i] = dp[i-1] + (2 * dp[i-2]) + dp[i-3]

    result = dp[N]

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

