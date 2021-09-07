---
layout: post
title:  "SWEA - PythonAdvanced_DivideAndConquer_Lecture6 solution"
date:   2021-09-08 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5204. [파이썬 S/W 문제해결 구현] 4일차 - 병합 정렬](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYFsQq11kDFAVT)

풀이

```python
def conquer(arr1, arr2):
    global count
    result = []
    idx1 = 0
    idx2 = 0
    len1 = len(arr1)
    len2 = len(arr2)
    while idx1 < len1 or idx2 < len2:
        if idx1 < len1 and idx2 < len2:
            if arr1[idx1] < arr2[idx2]:
                result.append(arr1[idx1])
                idx1 += 1
            else:
                result.append(arr2[idx2])
                idx2 += 1
        else:            
            if idx1 >= len1:
                result.append(arr2[idx2])
                idx2 += 1
            elif idx2 >= len2:
                result.append(arr1[idx1])
                idx1 += 1
    if arr1[-1] > arr2[-1]:
        count += 1 
    return result

def divide(arr):

    N = len(arr)
    if N <= 1:
        return arr
    else:
        arr1 = divide(arr[0:N//2])
        arr2 = divide(arr[N//2:N])
        return conquer(arr1, arr2)

T = int(input())

count = 0
answer = []
for tc in range(1, T + 1):

    N = int(input())
    numbers = list(map(int, input().split()))

    count = 0
    numbers_sorted = divide(numbers)

    result = ' '.join(map(str, [numbers_sorted[N//2], count]))
    
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

