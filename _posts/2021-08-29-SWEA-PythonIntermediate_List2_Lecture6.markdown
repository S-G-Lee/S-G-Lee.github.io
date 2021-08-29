---
layout: post
title:  "SWEA - PythonIntermediate_List2_Lecture6 solution"
date:   2021-08-29 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4837. [파이썬 S/W 문제해결 기본] 2일차 - 부분집합의 합](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVF-WqqecDFAWg#)

풀이

```python
def findsubsetamount(total, elementnum, startnum, endnum):

    num = 0
    if total >= startnum:
        for i in range(startnum, endnum):
            if elementnum == 1:
                if i == total:
                    num = 1
            else:
                num += findsubsetamount(total - i, elementnum - 1, i+1, endnum)

    return num


casenum = int(input())

for case in range(1, casenum+1):

    N, K = list(map(int, input().split()))

    result = findsubsetamount(K, N, 1, 13)

    print(f'#{case} {result}')
```

