#### Priority Queue  
Max priority queue delete: remove the largest element in queue.  

Find the largest M items in a stream of N items: use min queue, keep inserting until the # of element larger than M, we use min queue delete to delete the smallest one, this will only use M space.

Priority queue: unordered and ordered array implementation -> slow, it could take up to linear time for basic operation, the goal is logN.  

**Binary heaps**
complete binary tree (prefect balanced, expect for bottom level)  
Height = lgN   

We use array to represent the heap-ordered complete binary tree  
Parent's key no smaller than children's key  
Indexes start at 1, the largest key is a[1].

**insert**: add node at the end and swim it up with its parents recursively.  **logN**
**demotion in a heap**: parent's key become smaller than one or both of its children's   
Exchange key in parent with key in larger child, repeat until heap order restored.  
**delete max**: exchange root with node at end, then sink it down **logN**


#### Heap Sort

heap sort in place sort: 
1. create  a max heap with all N keys  
 Build max heap using bottom up method: 
we start with one node heap, and examine if it is in heap ordered
```
for (int k = N/2; k >= 1; k--)
	sink(a, k, N);
```
2. repeatedly remove the maximum key to the end of array   

```
while (N > 1)
{
 exch(a, 1, N--);
 sink(a, 1, N);
}
```
**analysis**  
Proposition. Heap construction uses ≤ 2 N compares and exchanges.  
Proposition. Heapsort uses ≤ 2 N lg N compares and exchanges.  
Significance. In-place sorting algorithm with N log N worst-case.

Bottom line. Heapsort is optimal for both time and space, but:  
・Inner loop longer than quicksort’s.  
・Makes poor use of cache memory.  
・Not stable.  

