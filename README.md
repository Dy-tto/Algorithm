Algorithm
=========
전공 자료 정리
----------

# Chap 1. Algorithms: Efficiency, Analysis, and Order
* 챕터 1에서는 알고리즘의 효율성(efficiency)을 다룬다.
* "order" 라는 개념은 알고리즘의 efficiency를 나타낸다.

## 1-1.Some Definitions
* Problem : a question to which we seek an answer.
* Problem Instance : a problem where each parameter is assigned a specific value.
  - ex) Determine whether the number 5 is in the list [10, 7, 11, 5, 13, 8] of 6 numbers.
* Algorithm : 각각의 problem instance을 해결하기 위한 단계별 절차.
  - ex) Sequential Search Algorithm(순차 탐색)

## 1-2. 효율적인 알고리즘 개발의 중요성
* Sequential Search Algorithm

```java
# Java
public static index SeqSearch(int n, keyType[] S, keyType x){
    index location = 1;
    while(location <= n && S[location] != x)
        location++;
    if(location>n)
        location = 0;
    return location;
}
```

```python3
# python3
def seq_search(n:int, lst:list, target:int):
    for i in range(n):
        if lst[i]==target:
            return i
    return -1
lst=[1,5,7,9,2,4,3]
print(seq_search(len(lst),lst,10))
```

* Binary Search Algorithm

```java
// Java
public static index BinarySearch(int n, keyType[] S, keyType x){
    index location, low, high, mid;
    
    low = 1;
    high = n;
    location = 0;
    
    while(low <= high && location == 0){
        mid=(low+high)/2;
        if(x==S[mid])
            location = mid;
        else if(x < S[mid])
            high = mid - 1;
        else
            low = mid + 1;
    }
    return location;
}
```

```python3
# python3
def binary_search(lst,target): # Iterative
    start=0
    end=len(lst)-1

    while start<=end:
        mid=(start+end)//2

        if lst[mid]==target:
            return mid
        elif lst[mid]>target:
            end=mid-1
        else:
            start=mid+1

lst=[1,2,3,4,5,6]
print(binary_search(lst,4))    
```

```python3
# python3
def binary_search(lst,target,start,end): # Recursive
    while start<=end:
        mid=(start+end)//2

        if lst[mid]==target:
            return mid
        elif lst[mid]>target:
            return binary_search(lst,target,start,mid-1)
        else:
            return binary_search(lst,target,mid+1,end)

lst=[1,2,3,4,5,6]
print(binary_search(lst,4,0,len(lst)-1))
```

* Sequential Search vs Binary Search
  - worst case 비교
<img width="547" alt="스크린샷 2022-02-28 오후 7 25 29" src="https://user-images.githubusercontent.com/59719632/155966908-5f7f6041-b5f6-441e-80d4-4dedae6edcf7.png">

* Fibonacci Sequence
<img width="645" alt="스크린샷 2022-02-28 오후 7 27 59" src="https://user-images.githubusercontent.com/59719632/155967348-c210d34b-5a70-43f0-8a52-bae93dfbe282.png">
  - Recursive Algorithm

```java
// Java
public static int Fib(int n){
    if(n<=1)
        return n;
    else
        return Fib(n-1) + Fib(n-2);
}
```
```python3
# python3
def fib(n): # Recursive
    if n<=1:
        return 1
    else:
        return fib(n-1)+fib(n-2)
```


<img width="597" alt="스크린샷 2022-02-28 오후 7 30 38" src="https://user-images.githubusercontent.com/59719632/155967711-755dd478-5ca6-4325-9996-8b233a2069b7.png">

  - Iterative Algorithm

```java
// Java
public static int Fib2(int n){
    index i;
    int[] f=new int[n+1];
    
    f[0] = 0;
    if(n > 0){
        f[1] = 1;
        for(i=2 ; i<=n ; i++)
            f[i]=f[i-1]+f[i-2];
    }
    return f[n];
}
```

```python3
# python3
def fib(n): # Iterative ( Dynamic-Programming)
    dp=[0]*(n+1)
    dp[1]=1
    dp[2]=1
    for i in range(3,n+1):
        dp[i]=dp[i-1]+dp[i-2]
    return dp[n]
```

<img width="268" alt="스크린샷 2022-02-28 오후 7 48 48" src="https://user-images.githubusercontent.com/59719632/155970310-26fa2123-3206-4c8f-bff9-7df25a98dfef.png">

<img width="583" alt="스크린샷 2022-02-28 오후 7 49 30" src="https://user-images.githubusercontent.com/59719632/155970401-6a2c4955-91c8-4f66-99ed-cb9b5bdd435a.png">

## 1-3. Analysis of Algorithms
* Input Size
  - size of array
    + ex) **n**\-tuple
  - single number \- 
    + ex) **n**\-th Fibonacci Number
  - Graph에서는 vertices 수와 edges 수 둘 다 input size이다.

* Basic Operation
  - 알고리즘이 실행될 때 기본적으로 실행되는 연산
    + 정렬 또는 탐색 알고리즘의 비교 연산
    + 행렬 곱의 덧셈 연산
* Time Complexity (시간 복잡도)
  - The determination of how many times the basic operation is don for each value of the input size.
    + 순차 탐색 알고리즘의 worst case는 **n**번 비교하는 것이다.
    






