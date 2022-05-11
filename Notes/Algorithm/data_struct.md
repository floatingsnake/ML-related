##   Data Structure

- **Stack**: one port come and out
- **Queue**: one port come and other port out
- **Array**:   variable in same dtype
- **Linked List**: physical discontinuous
- **Tree**
- **Graph**
- **Heap**
- **Hash Table**

### Heap

### Trick

1. Two pointer





## Algorithm

- Retrieval
- Insert
- Delete
- Update
- Sort

### Sort

#### 1. Insertion / Bubble Sort

```
def insertionSort(arr:list):
  for i in range(len(arr)):
    j = i
    while(j - 1 >= 0 and arr[j] < arr[j-1]):
      arr[j],arr[j-1] = arr[j-1],arr[j]
      j -= 1
  return arr

def bubblesort(arr:[]):
	for i in range(len(arr)):
		for j in range(i:len(arr)):
			if arr[i] > arr[j]:
				arr[j],arr[j-1] = arr[j-1],arr[j]
```



Time :  $o(n^2)$  Spatial:  $o(1)$

insert a value into a ordered list

use dual-layer iteration

Best Case:  Ordered ->  compare $n-1$

Worst Case: Inverted -> compare $(n-1)n/2$

#### 2. Shell Sort

```
def shellSort(arr:list):
  gap = int(len(arr)/2)
  while(gap > 0):
    for i in range(gap):
      a[i::gap] = insertionSort(a[i::gap])
    gap = int(gap/2)
  return arr
```

Time :  $o(n^{1.3-2})$  Spatial:  $o(1)$

**Unstable**

sort within gap: 

gap = length/2 -> gap = gap/2



#### 3. Merge Sort

```

def mergesort(arr:list):
  
  def merge_2_ordered_list(arr1:list, arr2:list):
    i = 0
    j = 0
    res = []
    while(i < len(arr1) or j < len(arr2)):
      if i >= len(arr1):
        for value in arr2[j:]:
          res.append(value)
        break
      elif j >= len(arr2):
        for value in arr1[i:]:
          res.append(value)
        break
      elif arr1[i] < arr2[j]:
        res.append(arr1[i])
        i += 1
      else:
        res.append(arr2[j])
        j += 1
    return res

  merged_len = 2
  while(merged_len <= len(arr)):
    for i in range(0,len(arr),merged_len):
      left = int(i)
      mid = int(i+merged_len/2)
      right = int(i+merged_len)
      arr[left:right] = merge_2_ordered_list(arr[left:mid],arr[mid:right])
    merged_len *= 2
  return arr

```



Time :  $o(nlog(n))$  Spatial:  $o(n)$

**Stable**

#### 4. Fast Sort

```
def partition(arr,left,right):
  pivot = arr[left]
  i = left + 1
  next_partitionIdx = left + 1
  while i <= right:
    if arr[i] <= pivot:
      arr[i],arr[next_partitionIdx] = arr[next_partitionIdx],arr[i]
      next_partitionIdx += 1
    i += 1
  partitionIdx = next_partitionIdx - 1
  arr[left],arr[partitionIdx] = arr[partitionIdx],arr[left]
  return partitionIdx
  
def quickSort(arr:list,left=None,right=None):
  left = 0 if not isinstance(left,(int,float)) else left
  right = len(arr) - 1 if not isinstance(right,(int,float)) else right
  if left <= right:
    partitionIdx = partition(arr,left,right)
    quickSort(arr,left,partitionIdx - 1)
    quickSort(arr,partitionIdx + 1, right)
  return arr
    
```

Time :  $o(nlog(n))$  Spatial:  $o(nlog(n))$

**Unstable**

#### 5. Heap Sort

```
def heapify(arr,i):
  left = 2 * i + 1
  right = 2 * i + 2
  largest = i
  if left < len(arr) and arr[left] > arr[largest]:
    largest = left
  if right < len(arr) and arr[right] > arr[largest]:
    largest = right
  if largest != i:
    swap(arr,largest,i)
    heapify(arr,largest)
  return arr

def buildMaxHeap(arr):
  for i in range(int(len(arr)/2),-1,-1):
    heapify(arr,i)
  return arr

def heapSort(arr:list):
  arrlen = len(arr)
  arr = buildMaxHeap(arr) 
  for i in range(len(arr)-1, 0, -1):
    swap(arr,0,i)
    arrlen -= 1
    arr[0:arrlen] = heapify(arr[0:arrlen],0)
  return arr
```

Time :  $o(nlog(n))$  Spatial:  $o(1)$

**Unstable**



## Dynamic Program

https://www.zhihu.com/question/23995189





