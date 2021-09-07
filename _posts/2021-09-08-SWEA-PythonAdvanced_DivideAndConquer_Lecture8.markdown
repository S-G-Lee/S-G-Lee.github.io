---
layout: post
title:  "SWEA - PythonAdvanced_DivideAndConquer_Lecture8 solution"
date:   2021-09-08 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5207. [파이썬 S/W 문제해결 구현] 4일차 - 이진 탐색](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYFsQq11kDFAVT)

풀이

```python
def partition_lomuto(arr, L, R):
    pivot = R
    i = L
    j = L
    flag = False
    while j < R:
        if arr[j] <= arr[pivot]:
            if not flag:
                i += 1
                j += 1
            else:
                arr[i], arr[j] = arr[j], arr[i]
                i += 1
                j += 1
        else:
            j += 1
            flag = True
    arr[i], arr[pivot] = arr[pivot], arr[i]
    return i

def quicksort(arr, L, R):
    if L < R:
        p = partition_lomuto(arr, L, R)
        quicksort(arr, L, p-1)
        quicksort(arr, p+1, R)

def cross_binary_search(arr, n, L, R):

    prev = 0
    while True:
        m = (L + R) // 2
        if n == arr[m]:
            return True
        if L >= R:
            break            
        elif n < arr[m]:
            if prev == 'l':
                break
            else:
                R = m - 1
                prev = 'l'
        else:
            if prev == 'r':
                break
            else:
                L = m + 1
                prev = 'r'
    return False
    

T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M = map(int, input().split())
    numbers = list(map(int, input().split()))
    number_to_find = list(map(int, input().split()))
    # quicksort(numbers)
    numbers.sort()

    result = 0
    for num in number_to_find:
        if cross_binary_search(numbers, num, 0, N-1):
            result += 1
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

