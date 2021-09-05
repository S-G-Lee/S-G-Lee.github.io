---
layout: post
title:  "SWEA - PythonAdvanced_Greedy_Lecture7 solution"
date:   2021-09-06 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5202. [파이썬 S/W 문제해결 구현] 3일차 - 화물 도크](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYEGw61n8DFAVT)

풀이

```python
def partition(arr, L, R, key=None):
    if key:
        if L < R:
            pivot = (L+R)//2
            while L < R:
                while L < R and key(arr[L]) < key(arr[pivot]):
                    L += 1
                while L < R and key(arr[R]) >= key(arr[pivot]):
                    R -= 1
                if L < R:
                    if L == pivot:
                        pivot = R
                    arr[L], arr[R] = arr[R], arr[L]
            arr[R], arr[pivot] = arr[pivot], arr[R]
            return R

    else:
        if L < R:
            pivot = (L+R)//2
            while L < R:
                while L < R and arr[L] < arr[pivot]:
                    L += 1
                while L < R and arr[R] >= arr[pivot]:
                    R -= 1
                if L < R:
                    if L == pivot:
                        pivot = R
                    arr[L], arr[R] = arr[R], arr[L]
            arr[R], arr[pivot] = arr[pivot], arr[R]
            return R

def quicksort(arr, L, R, key=None):
    if L < R:
        p = partition(arr, L, R, key)
        quicksort(arr, L, p-1, key)
        quicksort(arr, p+1, R, key)

T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())
    request = []
    for _ in range(N):
        s, e = map(int, input().split())
        request.append([s, e])
    
    quicksort(request, 0, N-1, key=lambda x: x[1])
    idx = 0
    start = -1
    while idx < len(request):
        if start <= request[idx][0]:
            start = request[idx][1]
            idx += 1
        else:
            request.pop(idx)
    
    result = len(request)
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

