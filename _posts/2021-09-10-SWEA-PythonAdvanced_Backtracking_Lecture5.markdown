---
layout: post
title:  "SWEA - PythonAdvanced_Backtracking_Lecture5 solution"
date:   2021-09-10 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5208. [파이썬 S/W 문제해결 구현] 5일차 - 전기버스2](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYGf7K180DFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    input_seq = list(map(int, input().split()))

    N = input_seq[0]
    battery = []
    for i in range(1, len(input_seq)):
        battery.append(input_seq[i])
    battery.append(0)

    count = 0
    pos = 0
    final = len(battery) - 1
    while pos < final:
        if pos + battery[pos] >= final:
            break
        next = 0
        for i in range(battery[pos], 0, -1):
            if next + battery[pos+next] < i + battery[pos+i]:
                next = i
        pos += next
        count += 1   

    result = count
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

