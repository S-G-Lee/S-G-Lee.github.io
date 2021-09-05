---
layout: post
title:  "SWEA - PythonAdvanced_Greedy_Lecture6 solution"
date:   2021-09-06 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5201. [파이썬 S/W 문제해결 구현] 3일차 - 컨테이너 운반](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYEGw61n8DFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M = map(int, input().split())
    container = list(map(int, input().split()))
    truck = list(map(int, input().split()))

    container.sort(reverse=True)
    truck.sort(reverse=True)

    container_idx = 0
    truck_idx = 0
    truck_num = len(truck)
    container_num = len(container)
    result = 0
    while truck_idx < truck_num and container_idx < container_num:
        if container[container_idx] > truck[truck_idx]:
            container_idx += 1
        else:
            result += container[container_idx]
            container_idx += 1
            truck_idx += 1
            
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

