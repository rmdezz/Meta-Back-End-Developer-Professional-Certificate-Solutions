# Time and space complexity in sorting algorithms

# Introduction

In this reading, you will learn about the time and space complexity of two commonly used sorting algorithms: selection sort and quicksort. These concepts are important in evaluating the efficiency of sorting algorithms.

# Selection Sort

- Definition: Selection sort is a simple sorting algorithm that starts from the first index of the array and iterates over the entire array to find the lowest value. The lowest value is then swapped with the first value of the array. This process is repeated until the entire array is sorted.
- Time Complexity:
    - Worst case: O(N^2)
    - Average case: O(N^2)
    - Best case: O(N^2)
- Space Complexity:
    - O(1) Auxiliary
- Steps:
    - Find the smallest value in the array and swap it with the first value
    - Find the second smallest value and swap it with the second value
    - Repeat the process until all items are sorted from smallest to largest

Pseudocode:

```python
for i = 0 to n-1
    min_index = i
    for j = i+1 to n-1
        if List[j] < List[min_index]
            min_index = j
    swap(List[i], List[min_index])
```

# Quicksort

- Definition: Quicksort is a sorting algorithm that uses a divide-and-conquer method. An array is split into two arrays based on a pivot point. The same process is repeated on both arrays until there are no elements left to sort.
- Time Complexity:
    - Worst case: O(N^2)
    - Average case: O(N log N)
    - Best case: O(N log N)
- Space Complexity:
    - O(N)
- Steps:
    - Select a pivot point in the array
    - Split the array into two arrays based on the pivot point (left and right)
    - Recursively apply the quicksort algorithm on both arrays

Pseudocode:

```
QuickSort(List, low, high)
    if (low < high)
        pivot = partition(List, low, high)
        QuickSort(List, low, pivot-1)
        QuickSort(List, pivot+1, high)

Partition(List, low, high)
    pivot = List[high]
    i = low-1
    for j = low to high-1
        if (List[j] <= pivot)
            i = i + 1
            swap(List[i], List[j])
    swap(List[i + 1], List[high])
    return i + 1

```

# Conclusion

In this reading, you learned about the time and space complexity of two commonly used sorting algorithms: selection sort and quicksort. While selection sort is a simple and less code-heavy algorithm, it requires more time and space to generate results. On the other hand, quicksort is more complex in implementation but returns quicker results in terms of time and space.