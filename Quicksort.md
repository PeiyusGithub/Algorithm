### Quick sort
Basic plan.  
・Shuffle the array.  (in order to guarantee the efficiency)
**if the array is sorted, it will take qudractic time fot quick sort**4444
・Partition so that, for some j  
	– entry a[j] is in place  
	– no larger entry to the left of j  
	– no smaller entry to the right of j  
・Sort each piece recursively.  

**Partition**  
Repeat until i and j pointers cross.  
・Scan i from left to right so long as (a[i] < a[lo]).  
・Scan j from right to left so long as (a[j] > a[lo]).  
・Exchange a[i] with a[j].  
When pointers cross.  
・Exchange a[lo] with a[j].
```
private static int partition(Comparable[] a, int lo, int hi)
{
  int i = lo, j = hi+1;
  while (true)
  {
  	while (less(a[++i], a[lo]))
  		if (i == hi) break; 
        
  	while (less(a[lo], a[--j]))
    	if (j == lo) break;
        
    if (i >= j) break;
    exch(a, i, j);
  }
  exch(a, lo, j);
  return j;
}
```
**Quick sort**
```
public class Quick
{
  private static int partition(Comparable[] a, int lo, int hi)
  { /* see previous slide */ }
  
  public static void sort(Comparable[] a)
  {
    StdRandom.shuffle(a);
    sort(a, 0, a.length - 1);
  }
  private static void sort(Comparable[] a, int lo, int hi)
  {
    if (hi <= lo) return;
    int j = partition(a, lo, hi);
    sort(a, lo, j-1);
    sort(a, j+1, hi);
  }
}
```

**Properties**
1. Quick sort is in-place sorting algorithm.
2. Quick sort is not stable. (long range exchange)

**Improvements**
1. Insertion sort for tiny array
2. Median of sample

















