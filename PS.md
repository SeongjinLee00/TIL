# Problem Solving

**2차원 리스트 transpose하거나, 열끼리 합 구할때**

`my_list=list(zip(*my_list))` 사용



```python
my_list=[[1,2,3],[4,5,6],[7,8,9]]

print(my_list) # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

my_list=list(zip(*my_list))

print(my_list) # [(1, 4, 7), (2, 5, 8), (3, 6, 9)]
```



이렇게 하면 x[0], x[1], x[2] 순으로 정렬 가능

```python
my_list=[[1,2,3],[1,2,2],[1,2,4],[2,3,1],[1,1,5],[4,3,1],[1,3,4],[2,2,3],[1,2,5]]

my_list.sort(key=lambda x:(x[0],x[1],x[2]),reverse=True)

print(my_list)
```



리스트 중간에 삽입쉽게하기

```python
lst=[1,2,3,4]
lst[2:2]=['a','b','c']
print(lst) # [1, 2, 'a', 'b', 'c', 3, 4]

lst=[1,2,3,4]
lst[1:3] = ["a", "b", "c", "d", "e"]
print(lst) # [1, 'a', 'b', 'c', 'd', 'e', 4]
```



```python
import sys

input = sys.stdin.readline

n, m = map(int, input().split())
```

이렇게 하고 원래 쓰던것처럼 input 쓰면 된다



` N, *numbers=map(int,input().split()) ` 이렇게하면 N에 맨앞숫자, numbers에 나머지



```python
a = [[1, 2], [3, 4], [5, 6]]
b = sum(a, [])
```

이렇게 하면 2차원 리스트를 1차원으로!



**비트연산자**

& | << >> ^ : 다 알고

i & (1<<j) : i의 j번째 비트가 1인지를 검사한다



부분집합 아름답게 생성하는 방법

```python
arr=[3,6,7,1,5,4]

n=len(arr) # 6

for i in range(1<<n): # 2^n
    for j in range(n): # 0 1 2 3 4 5
        if i & (1<<j): # i의 j번째 비트가 1이면
            print(arr[j], end=", ")
    print()
print()
```



**사이클 판별**

방향그래프의 사이클 판별은 DFS로 해야함

무방향 그래프의 사이클은 유니온파인드로 가능, DFS/BFS로도 물론 가능.

​									방향그래프				무방향그래프

BFS/DFS                            O                                  O

유니온파인드                    X                                   O

위상정렬                            O                                  X



