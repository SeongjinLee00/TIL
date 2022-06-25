# Algorithm

[TOC]

## 자료구조

### 스택

pop() : 맨위원소 반환하면서 제거, 파이썬엔 리스트 메소드로 있음

push() : 스택에 원소 집어넣음, append()

top() : 맨 위에 있는 수 출력, list[-1], 비어있으면 -1 출력

isEmpty() : 비어있으면 1, 아니면 0 출력

size() : 스택 크기 출력, 파이썬엔 len()



#### Stack-후위표기법 계산기

**후위표기법으로 만들기**

1. 토큰을 하나씩 순회
2. 숫자는 출력
3. 토큰의 우선순위가 높으면 출력, 그렇지 않다면 토큰이 더 커질때까지 top을 결과에 붙여나감

4. 토큰이 )면 (를 만날때까지 top을 결과에 붙여나가다가, )과 서로 상쇄시킴
5. 계속 반복한 후 남아있는 연산자 모두 붙임

**계산기**

숫자->push

연산자->스택에서 pop 두번 하여 연산 후 push

| 토큰 | isp  | icp  |
| :--: | :--: | :--: |
|  )   |  -   |  -   |
| *, / |  2   |  2   |
| +, - |  1   |  1   |
|  (   |  0   |  3   |

permutation

```python
def perm(i):
    if i == len(p):
        print(p)
    else:
        for j in range(i, len(p)):
            p[i], p[j] = p[j], p[i]  # swap
            perm(i + 1)
            p[i], p[j] = p[j], p[i]


p = [1, 2, 3]

perm(0)
```





### 큐

push() : 원소 집어넣음, append()

pop() : 가장 앞에있는 원소 반환하면서 제거, .pop(0)

size() : len()

isEmpty() : 비어있으면 1, 아니면 0 출력

front() : 가장 앞에 있는 수 출력, list[0], 비어있으면 -1출력

back() : 가장 뒤에 있는 수 출력, list[-1], 비어있으면 -1 출력



### 덱

`from collections import deque`

push_front() : .appendleft()

push_back() : .append()

pop_front() : .popleft()

pop_back() : pop()

size() : len

isEmpty() : 

front() : 인덱싱 가능

back() : 인덱싱 가능

1. 리스트처럼 insert, remove, indexing도 가능
2. extend, extendleft, rotate 도 있음 파이썬엔
3. reverse도있음



### 트리

모든 트리는 left-child right-sibling을 통해 2진 트리로 나타낼 수 있으므로, 트리의 기본은 2진 트리

- 정 이진 트리(full binary tree) : 모든 자식이 0개나 2개

- 포화 이진 트리(perfect binary tree) : 모든 리프 노드가 아닌 노드는 2개의 자식을 갖는 트리

- 완전 이진 트리(complete binary tree) : 마지막 레벨 바로 전까지는 꽉 차있어서, 리프의 높이가 최대 1 차이 나고 모든 노드의 오른쪽 자식이 있으면 왼쪽 자식이 있는 트리, 다시 말해서 왼쪽부터 오른쪽까지 채워나간 형태

 

순회 방법

- 중위 순회 : 왼쪽 자손-자신-오른쪽 자손 순서로 방문, 중위 순회하면 정렬된 결과를 얻을 수 있음
- 전위 순회 : 자신-왼쪽 자손-오른쪽 자손 순서로 방문->root에서 시작하는 DFS
- 후위 순회 : 왼쪽 자손-오른쪽 자손-자신 순서로 방문->아래에서 위로 올라감(Symmetric)
- 레벨 순서 순회 : 레벨 순서로 방문. 위의 세개는 스택을 활용하여 구현하는 반면 레벨 순서 순회는 큐를 활용해 구현할 수 있음.





## 알고리즘

이진탐색

upperbound, lowerbound



카프-라빈 알고리즘

KMP 알고리즘

보이어-무어 알고리즘 horspool 알고리즘



### 패턴검색

1. 브루트포스

   ```python
   pattern="is"
   text="This is a book"
   M=len(pattern) # 2
   N=len(text) # 14
   
   def BruteForce(pattern, text):
       j=0
       i=0
       while j<M and i<N:
           if text[i] != pattern[j]:
               i = i-j
               j = -1
           i = i+1
           j = j+1
       if j==M : return i-M # 검색 성공(j=M이 되어 루프 빠져나온경우)
       else: return -1 # 검색 실패(i=N이 되어 루프 빠져나온경우)
   ```

   
