---
layout: post
title:  "SWEA - PythonAdvanced_DynamicProgrammingUtil_Lecture4 solution"
date:   2021-09-27 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5262. [파이썬 S/W 문제해결 최적화] 4일차 - 정렬된 부분 집합](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYODN63DsDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    numbers = list(map(int, input().split()))

    lis = [0] * (len(numbers)+1)
    lis[0] = -1000000
    lis_end = 0

    for i in range(len(numbers)):
        l, r = 0, lis_end
        while True:
            idx = (l + r) // 2
            if r == l:
                break
            if numbers[i] > lis[idx]:
                l = idx + 1
            else:
                r = idx
        if l == lis_end and numbers[i] > lis[lis_end]:
            l += 1
            lis_end += 1
        lis[l] = numbers[i]

    result = lis_end
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

