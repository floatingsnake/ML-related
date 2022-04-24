##  Data Structure

- **Stack**: one port come and out
- **Queue**: one port come and other port out
- **Array**:   variable in same dtype
- **Linked List**: physical discontinuous

- **Tree**
- **Graph**
- **Heap**
- **Hash Table**

## Algorithm

- Retrieval
- Insert
- Delete
- Update
- Sort



### Sort

#### 1. Insertion Sort

```
void insertionSort(T arr[], int n){
	for (int i =1 ; i < n ; i ++){
		for (int j = i ; j > 0 ; j --)
			if arr[j-1] < arr[j]
				swap(arr[j-1],arr[j])
	}
}
v
```



Time : $o(n^2)$ Spatial: $o(1)$

insert a value into a ordered list

use dual-layer iteration

Best Case:  Ordered ->  compare $n-1$

Worst Case: Inverted -> compare $(n-1)n/2$

#### 2. Shell Sort







