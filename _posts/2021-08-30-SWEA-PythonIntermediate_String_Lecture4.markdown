---
layout: post
title:  "SWEA - PythonIntermediate_String_Lecture4 solution"
date:   2021-08-30 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4861. [파이썬 S/W 문제해결 기본] 3일차 - 회문](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVGOEKqeoDFAWg#)

풀이

```python
def is_pal(word):

    if len(word) < 2:
        return True
    
    if word[0] == word[-1]:
        return is_pal(word[1:-1])
    else:
        return False


def get_pal(matrix, N, M):

    for i in range(N):
        for j in range(N):
            if j < N-M+1:
                if is_pal(matrix[i][j:j+M]):
                    return matrix[i][j:j+M]
            if i < N-M+1:
                if is_pal(''.join(list(map(lambda x: x[j], matrix[i:i+M])))):
                    return ''.join(list(map(lambda x: x[j], matrix[i:i+M])))


T = int(input())

for tc in range(1, T + 1):   

    N, M = list(map(int, input().split()))
    lettermatrix = [input() for _ in range(N)]

    result = get_pal(lettermatrix, N, M)

    print(f'#{tc} {result}')
```

