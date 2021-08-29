---
layout: post
title:  "SWEA - PythonIntermediate_List2_Lecture8 solution"
date:   2021-08-29 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4843. [파이썬 S/W 문제해결 기본] 2일차 - 특별한 정렬](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVF-WqqecDFAWg#)

풀이

```python
T = int(input())

for tc in range(1, T+1):

    amount = int(input())
    numberlist = list(map(int, input().split()))
    length = len(numberlist)

    pivot = 0 # index that points the current end point of sorted sublist
    while pivot < length:
        
        current_idx = pivot
        for i in range(pivot, length):
            if pivot % 2:
                if numberlist[current_idx] > numberlist[i]:
                    current_idx = i
            else:
                if numberlist[current_idx] < numberlist[i]:
                    current_idx = i
        
        numberlist[current_idx], numberlist[pivot] = numberlist[pivot], numberlist[current_idx]

        pivot += 1
    
    resultstr = ''
    for i in range(min(10, length)):
        resultstr = resultstr + str(numberlist[i]) + ' '
    resultstr = resultstr[:-1]
    print(f'#{tc} {resultstr}')
```

