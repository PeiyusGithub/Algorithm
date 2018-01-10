### Merger sort
Basic plan.  
・Divide array into two halves.  
・Recursively sort each half.  
・Merge two halves.  

**Merge Implementation**
```
private static void merge(Comparable[] a, Comparable[] aux, int lo, int mid, int hi)
{
  assert isSorted(a, lo, mid); // precondition: a[lo..mid] sorted
  assert isSorted(a, mid+1, hi); // precondition: a[mid+1..hi] sorted
  for (int k = lo; k <= hi; k++)
  	aux[k] = a[k];
  int i = lo, j = mid+1;
  for (int k = lo; k <= hi; k++)
  {
    if (i > mid) 					a[k] = aux[j++];
    else if (j > hi) 				a[k] = aux[i++];
    else if (less(aux[j], aux[i])) 	a[k] = aux[j++];
    else 							a[k] = aux[i++];
  }
  assert isSorted(a, lo, hi); // postcondition: a[lo..hi] sorted
}
```

**Sort Implementation**

```
public class Merge
{
	private static void merge(...)
	{ /* as before */ }
    private static void sort(Comparable[] a, Comparable[] aux, int lo, int hi)
    {
      if (hi <= lo) return;
      int mid = lo + (hi - lo) / 2;
      sort(a, aux, lo, mid);
      sort(a, aux, mid+1, hi);
      merge(a, aux, lo, mid, hi);
    }
    public static void sort(Comparable[] a)
    {
      aux = new Comparable[a.length];
      sort(a, aux, 0, a.length - 1);
    }
}
```
**Time Complexity**  
O(NlogN): logN for spliting and N for merging  
proof by picture:  
![proof](https://i.imgur.com/FWyB78J.png?1)  
proof by expansion:  
![proof2](https://i.imgur.com/q0l2lq5.png?1)

for small scale of input, insertion sort is faster than merge sort

**Improvements**  
Use insertion sort for small subarrays.  
Stop if already sorted.  
Eliminate the copy to the auxiliary array. Save time (but not space)
by switching the role of the input and auxiliary array in each recursive call.


