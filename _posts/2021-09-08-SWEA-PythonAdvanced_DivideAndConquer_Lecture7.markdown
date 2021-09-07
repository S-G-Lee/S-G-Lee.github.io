---
layout: post
title:  "SWEA - PythonAdvanced_DivideAndConquer_Lecture7 solution"
date:   2021-09-08 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[\5205. [파이썬 S/W 문제해결 구현] 4일차 - 퀵 정렬](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYFsQq11kDFAVT)

풀이

```python
def partition(arr, L, R):
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

def quicksort(arr, L, R):
    if L < R:
        p = partition(arr, L, R)
        quicksort(arr, L, p-1)
        quicksort(arr, p+1, R)

T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())
    numbers = list(map(int, input().split()))

    quicksort(numbers, 0, N-1)

    result = numbers[N//2]
    
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

