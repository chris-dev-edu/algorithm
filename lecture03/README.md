# Lecture 03

## 재귀함수 (Recursive Function)
- 재귀함수란 함수가 자기 자신을 호출하는 함수이다
- 재귀함수는 주어진 문제를 더 작은 부분 문제로 분할하여 해결하는 방식으로 동작한다
- 문제의 해결이 반복적으로 같은 알고리즘이 적용되는 경우에 재귀함수가 유용하게 사용된다

## 팩토리얼 (Factorial)
- 팩토리얼은 양의 정수 `n`에 대해 `n`부터 `1`까지의 모든 양의 정수를 곱하는 연산이다

**일반적인 함수로 구현한 팩토리얼**
```python
def factorial(n):
    result = 1
    for i in range(1, n+1):
        result *= i
    
    return result
```

**재귀 함수로 구현한 팩토리얼**
```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    else:
        return n * factorial(n-1)
```

## 피보나치 수열 (Fibonacci Sequence)
- 피보나치 수열은 첫째 항이 0, 둘째 항이 1 이며, 이후의 모든 항이 바로 앞 두 항의 합인 수열이다
- 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ...
```python
def fibonacci(n):
    if n == 1:
        return 0
    elif n == 2:
        return 1
    else:
        return fibonacci(n-1) + fibonacci(n-2)
```