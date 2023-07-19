# Lecture 02

## 정렬 알고리즘

### 버블 정렬 (Bubble Sort)
- 인접한 두 원소를 비교하며 크기 순서에 맞지 않는 경우 서로 교환하는 방식으로 정렬
- 특징: 가장 간단하지만 비효율적이다
- 시간복잡도
  - 평균: O(n<sup>2</sup>)
```python
def bubble_sort(my_list):
    n = len(my_list)
    for i in range(n):
        for j in range(0, n-i-1):
            if my_list[j] > my_list[j+1]:
                my_list[j], my_list[j+1] = my_list[j+1], my_list[j]
    return my_list
```

### 선택 정렬 (Selection Sort)
- 주어진 리스트에서 최솟값을 찾아 첫 번째 위치와 교환하고, 그 다음으로 작은 값을 찾아 두 번째 위치와 교환하는 정렬
- 시간복잡도
  - 평균: O(n<sup>2</sup>)
```python
def selection_sort(my_list):
    n = len(my_list)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if my_list[j] < my_list[min_idx]:
                min_idx = j
        my_list[i], my_list[min_idx] = my_list[min_idx], my_list[i]
    return my_list

```

### 삽입 정렬 (Insertion Sort)
- 정렬되지 않은 부분의 원소를 정렬된 부분의 올바른 위치에 삽입하는 정렬
- 특징: 작은 크기의 리스트에서 효과적이며, 데이터가 이미 거의 정렬되어 있는 경우에 빠르다
- 시간복잡도
  - 평균: O(n<sup>2</sup>)
```python
def insertion_sort(my_list):
    n = len(my_list)
    for i in range(1, n):
        key = my_list[i]
        j = i - 1
        while j >= 0 and my_list[j] > key:
            my_list[j + 1] = my_list[j]
            j -= 1
        my_list[j + 1] = key
    return my_list
```

### 퀵 정렬 (Quick Sort)
- 리스트를 분할하고, 분할된 부분 리스트를 재귀적으로 정렬
- 특징: 평균적으로 빠른 속도를 가지며, 가장 널리 사용된다
- 시간복잡도
  - 평균: O(n log n)
  - 최악: O(n<sup>2</sup>)
```python
def quick_sort(my_list):
    if len(my_list) <= 1:
        return my_list
    pivot = my_list[len(my_list) // 2]
    left = [x for x in my_list if x < pivot]
    middle = [x for x in my_list if x == pivot]
    right = [x for x in my_list if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

### 병합 정렬 (Merge Sort)
- 리스트를 반으로 나눈 후, 나눠진 부분 리스트를 정렬하고 병합하는 과정을 재귀적으로 수행
- 특징: 안정적인 속도를 제공하며, 큰 리스트에서도 효과적이다
- 시간복잡도
  - 평균: O(n log n)
```python
def merge_sort(my_list):
    if len(my_list) <= 1:
        return my_list
    mid = len(my_list) // 2
    left = my_list[:mid]
    right = my_list[mid:]
    left = merge_sort(left)
    right = merge_sort(right)
    return merge(left, right)

def merge(left, right):
    result = []
    while left and right:
        if left[0] <= right[0]:
            result.append(left.pop(0))
        else:
            result.append(right.pop(0))
    while left:
        result.append(left.pop(0))
    while right:
        result.append(right.pop(0))
    return result
```

### 힙 정렬 (Heap Sort)
- 힙 자료구조를 사용하여 최대/최소 값을 추출하여 정렬
- 시간복잡도
  - 평균: O(n log n)
```python
def heapify(my_list, n, i):
    largest = i  # 부모 노드
    left = 2 * i + 1  # 왼쪽 자식 노드
    right = 2 * i + 2  # 오른쪽 자식 노드

    # 왼쪽 자식 노드가 부모보다 큰 경우
    if left < n and my_list[left] > my_list[largest]:
        largest = left

    # 오른쪽 자식 노드가 부모보다 큰 경우
    if right < n and my_list[right] > my_list[largest]:
        largest = right

    # 부모 노드와 자식 노드를 교환하고, 힙을 재구성
    if largest != i:
        my_list[i], my_list[largest] = my_list[largest], my_list[i]
        heapify(my_list, n, largest)

def heap_sort(my_list):
    n = len(my_list)

    # 최대 힙 구성
    for i in range(n // 2 - 1, -1, -1):
        heapify(my_list, n, i)

    # 힙에서 하나씩 루트 노드를 제거하며 정렬
    for i in range(n - 1, 0, -1):
        my_list[i], my_list[0] = my_list[0], my_list[i]  # 루트 노드와 마지막 노드 교환
        heapify(my_list, i, 0)  # 힙 재구성

    return my_list
```