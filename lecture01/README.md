# Lecture 01

## 알고리즘이란
- 알고리즘은 주어진 문제를 해결하기 위해 수행해야 할 일련의 단계나 절차를 기술한 것이다
- 명확하게 정의된 입력과 출력이 있으며, 입력을 출력으로 변환하는 과정을 단계별로 설명한다
- 알고리즘의 평가는 일반적으로 시간복잡도, 공간복잡도, 정확성, 효율성을 고려하여 이루어진다

## 시간복잡도 - Time Complexity

### 개념
- 알고리즘의 실행 시간이 입력 크기에 대해 어떻게 증가하는지 나타내는 개념이다
- 알고리즘이 문제를 해결하는데 걸리는 시간을 측정하는데 사용된다
- 입력 크기 n에 대한 함수로 나타내며, 대개 Big O 표기법으로 표현한다

### Big O 표기법 - Big O Notation
- Big O 표기법은 알고리즘의 상한을 나타내는 수학적 표기법이다
- 알고리즘이 최악의 경우에 얼마나 많은 자원을 사용하는지 나타낸다
- Big O 표기법에서는 주어진 함수의 상수 계수, 낮은 차수 항, 상수 항을 무시하여 가장 큰 영향을 주는 항만을 고려한다

**일반적으로 사용되는 몇가지 시간 복잡도의 예**
- **O(1)**
- **O(log n)**
- **O(n)**
- **O(n<sup>2</sup>)**

### Big O Notation으로 계산해보기
```python
number = 1
number += 3
```
- Big O : <span style="color:white; background-color: white">O(2)</span>

```python
result = 0

for i in range(n):
    result += i

print(i)
```
- Big O : <span style="color:white; background-color: white">O(n)</span>

```python
result = 0

for i in range(n):
    for j in range(i):
        result += 1

print(result)
```
- Big O : <span style="color:white; background-color: white">O(n<sup>2</sup>/2)</span>

## 공간복잡도
- 알고리즘이 실행되는 동안 필요한 메모리 공간의 양을 나타낸다
- 공간복잡도는아래 두가지 주요 요소로 구성된다

**고정공간**
- 알고리즘이 실행되는 동안 상수 크기의 메모리를 사용하는 경우의 공간
- 알고리즘이 실행되기 전 할당된 고정 메모리로, 입력 크기와 관계없이 일정한 크기를 차지한다

**가변공간**
- 알고리즘이 실행되는 동안 입력 크기에 따라 변하는 메모리 공간
- 주로 동적으로 할당되는 데이터 구조(ex. 리스트, 트리 등)나 임시 변수, 재귀 호출 등에 의해 결정된다

## 알고리즘 문제 풀기
