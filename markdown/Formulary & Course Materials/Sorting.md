# Sorting

# Bubble Sort

## Runtime

$O(n^2)$ comparisons, $O(n^2)$ swaps

## Pseudocode

```python
def bubble_sort(a):
    for j in range(1, len(a) - 1):
        for i in range(1, len(a) - 1):
            if a[i] > a[i + 1]:
                swap(a[i], a[i + 1])
```

## Further Resources

[Bubble sort - Wikipedia](https://en.wikipedia.org/wiki/Bubble_sort)

# Selection Sort

## Runtime

$O(n)$ comparisons, $O(n^2)$ swaps

## Pseudocode

```python
def selection_sort(a):
    for i in range(len(a), 2, -1):
        j = 0
        for h in range(len(a)):
            if a[h] < a[j]:
                j = h
        swap(a[i], a[j])
```

## Further Resources

[Selection sort - Wikipedia](https://en.wikipedia.org/wiki/Selection_sort)

# Insertion Sort

## Runtime

$O(n \log n)$ comparisons, $O(n^2)$ swaps

## Pseudocode

```python
def insertion_sort(a):
    for i in range(1, len(a)):
        k = a[i]
        j = i - 1
        while j >= 0 and key < a[j]:
            j -= 1
        a[j + 1] = k
```

## Further Resources

[Insertion sort - Wikipedia](https://en.wikipedia.org/wiki/Insertion_sort)

# Heap Sort

## Runtime

$O(n \log n)$

## Pseudocode

```python
def heapify(unsorted, index, heap_size):
    largest = index
    left_index = 2 * index + 1
    right_index = 2 * index + 2
    if left_index < heap_size and unsorted[left_index] > unsorted[largest]:
        largest = left_index

    if right_index < heap_size and unsorted[right_index] > unsorted[largest]:
        largest = right_index

    if largest != index:
        unsorted[largest], unsorted[index] = unsorted[index], unsorted[largest]
        heapify(unsorted, largest, heap_size)

def heap_sort(unsorted):
    n = len(unsorted)
    for i in range(n // 2 - 1, -1, -1):
        heapify(unsorted, i, n)
    for i in range(n - 1, 0, -1):
        unsorted[0], unsorted[i] = unsorted[i], unsorted[0]
        heapify(unsorted, 0, i)
    return unsorted
```

## Further Resources

[Heapsort - Wikipedia](https://en.wikipedia.org/wiki/Heap_sort)

# Quick Sort

## Runtime

$O(n \log n)$

## Pseudocode

```python
def quick_sort(collection: list) -> list:
    if len(collection) < 2:
        return collection
    pivot = collection.pop()
    greater: list[int] = []
    lesser: list[int] = []
    for element in collection:
        (greater if element > pivot else lesser).append(element)
    return quick_sort(lesser) + [pivot] + quick_sort(greater)
```

## Further Resources

[Quicksort - Wikipedia](https://en.wikipedia.org/wiki/Quick_sort)

# Merge Sort

## Runtime

$O(n \log n)$

## Pseudocode

```python
def merge_sort(collection: list) -> list:
    def merge(left: list, right: list) -> list:
        def _merge():
            while left and right:
                yield (left if left[0] <= right[0] else right).pop(0)
            yield from left
            yield from right

        return list(_merge())

    if len(collection) <= 1:
        return collection
    mid = len(collection)
    return merge(merge_sort(collection[:mid]), merge_sort(collection[mid:]))
```

## Further Resources

[Merge sort - Wikipedia](https://en.wikipedia.org/wiki/Merge_sort)

# Lower Bound for Comparison-Based Sorting

Is it possible to sort in under $\Theta(n\log n)$ comparisons?

Every comparison-based sorting algorithm corresponds to some binary decision tree. Then the number of leaves of that tree gives the number of possible sort states of the underlying data ($n!$ many). The worst-case runtime corresponds to the height of the tree, denoted by $h$.

A tree that has height $h$ must have more than $2^h$ leaves, thus 

$$
\begin{align*}
& 2^h \geq n! \\
\iff & h \geq \log_2(n!) \geq \Omega(n \log n)
\end{align*}
$$

The inequality $\log_2(n!) \geq \Omega(n \log n)$ stems from the fact that $(\frac{n}{2})^{\frac{n}{2}} \leq n! \leq n^n$ and that $\log(a^b) = b \log a$ of course.

# Topological Sort using Depth-First Search (DFS)

A directed graph $G = (V,E)$ has a topological sort if and only if it contains no directed cycles.

<aside>
💡 There exists a directed cycle if and only if there exists a back-edge in the DFS tree of $G$.

</aside>

<aside>
💡 For all edges $(u, v) \in E$ in the DFS tree that are not a back-edge it holds that $\text{post}(u) \geq \text{post}(v)$.

</aside>

<aside>
💡 From the above observations it follows that if there does not exist a directed cycle then there does not exist a back edge in the DFS tree. Since for all non-back-edges $(u,v) \in E$ of the DFS tree it holds that $\text{post}(u) \geq \text{post}(v)$ it follows that the reverse post-ordering corresponds to a topological sort of $G$.

</aside>

## Runtime

Adjacency-Matrix: $O(n^2)$

Adjacency-List: $O(\lvert V \rvert + \lvert E \rvert)$

## Pseudocode

```python
pre = []
post = []
t = 0

def visit(u):
    pre[u] = t
    t = t + 1
    mark(u)
    for v in u.children:
        if !marked(v):
            visit(v)
    post[u] = t
    t = t + 1

def dfs(graph):
    pre = [None] * len(graph.nodes)
    post = [None] * len(graph.nodes)
    t = 1
    unmarkAll(graph.nodes)
    for u in graph.nodes:
        if !marked(u):
            visit(u)

# reverse(post) gives a topological sort
```

## Further Resources

[Topological sorting - Wikipedia](https://en.wikipedia.org/wiki/Topological_sorting)