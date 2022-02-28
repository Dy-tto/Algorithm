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
```c++
public static index SeqSearch(int n,
                              keyType[] S,
                              keyType x){
    index location = 1;
    while(location <= n && S[location] != x)
        location++;
    if(location>n)
        location = 0;
    return location;

}
```
