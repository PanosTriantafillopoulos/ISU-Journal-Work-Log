```python
def heapsort(arr):
    # Build the max heap
    build_max_heap(arr)

    # Extract elements one by one from the heap
    for i in range(len(arr) - 1, 0, -1):
        # Swap the root (maximum element) with the last element
        arr[0], arr[i] = arr[i], arr[0]
        # Restore the heap property for the remaining elements
        heapify(arr, i, 0)


def build_max_heap(arr):
    # Starting from the last non-leaf node and moving up to the root
    for i in range(len(arr) // 2 - 1, -1, -1):
        # Perform heapify operation on each node
        heapify(arr, len(arr), i)


def heapify(arr, n, root):
    largest = root  # Initialize the largest as the root
    left = 2 * root + 1  # Left child
    right = 2 * root + 2  # Right child

    # Check if the left child exists and is greater than the current largest
    if left < n and arr[left] > arr[largest]:
        largest = left

    # Check if the right child exists and is greater than the current largest
    if right < n and arr[right] > arr[largest]:
        largest = right

    # If the largest is not the root, swap the root with the largest
    if largest != root:
        arr[root], arr[largest] = arr[largest], arr[root]
        # Recursively heapify the affected sub-tree
        heapify(arr, n, largest)
```
