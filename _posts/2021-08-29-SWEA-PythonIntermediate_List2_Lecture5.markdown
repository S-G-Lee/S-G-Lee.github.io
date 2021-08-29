---
layout: post
title:  "SWEA - PythonIntermediate_List2_Lecture5 solution"
date:   2021-08-29 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4836. [파이썬 S/W 문제해결 기본] 2일차 - 색칠하기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVF-WqqecDFAWg#)

풀이

```python
casenum = int(input())

for case in range(1, casenum+1):
    
    recnum = int(input())
    field = [[0 for col in range(10)] for row in range(10)] # field that have color information, 1 : red, 2 : blue, 3 : purple
    
    for i in range(recnum):
        r1, c1, r2, c2, color = list(map(int, input().split()))
        for i in range(r1, r2+1):
            for j in range(c1, c2+1):
                if field[i][j] == 0:
                    field[i][j] = color
                elif field[i][j] != color:
                    field[i][j] = 3

    purplearea = 0
    for i in range(10):
        for j in range(10):
            if field[i][j] == 3:
                purplearea += 1

    print(f'#{case} {purplearea}')
```

