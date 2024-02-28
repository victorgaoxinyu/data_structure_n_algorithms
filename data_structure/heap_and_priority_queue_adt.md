Priority Queue ADT
- aka Heap


- Max-oriented
  - insert
  - delete_max
- Min-oriented
  - insert
  - delete_min

ADT-implementation 1 (Array)
- insert
- search for the largest one and remove
- shift all elements back

Time-complexity
- insert: O(1)
- delete_max: O(n)

ADT-implementation 2 (Sorted Array)
- insert: O(n)
  - use binary search to insert to right position
  - shift all elements
- delete_max: O(1)
  - last item in array should be highest

ADT-implementation 3 (Max Heap)
- Binary Tree
- Structural Property
  - levels completely filled from left to right
- Head-order Property
  - parent key larger or equal to children


Tree vs Arrays:
- Tree uses more time and memory
- Asymptotically same time/space complexity
- Node allocation takes longer


Heap Implementation
- insert
- delete_max
- fix_up
  - this is to fix the heap after insert
- fix_down
  - this is to fix the heap after delete_max (root node)
- get_child
  - helper function to get index of left child, 2 * i + 1
  - right child index will be left child index + 1
- get_parent
  - helper function to get index of parent index, floor((i-2) / 2)
- swap
```
function swap(a,b){
    tmp = a
    a = b
    b = tmp
  }
```

```
struct MaxHeap {
    int arr[]
    int n
}
```
```
function insert(maxheap, x){
    maxheap.n += 1
    maxheap.arr[maxheap.n-1] = x
    fix_up(maxheap.arr, maxheap.n-1)
}

function fix_up (A, i){
    while parent(i) exists and A[parent(i)] < A[i]
        swap(A[i], A[parent(i)])
        i = parent(i)
}

function delete_max(maxheap) {
    swap(maxheap.arr[0], maxheap.arr[maxheap.n - 1]) # swap root with last element
    maxheap.n -= 1
    fix_down(maxheap.arr, maxheap.n, 0)
    return arr[maxheap.n]
}

function fix_down(A, n, i) {  # array A, size n, i index to perform fix_down on
    while i is not a leaf
        j = left_child(i)
        if A[j] < A[j + 1] and j != n -1 # right larger than left and right exist
        j += 1
        if A[i] >= A[j]
          break
        swap(A[i], A[j])
        i = j
}
```
