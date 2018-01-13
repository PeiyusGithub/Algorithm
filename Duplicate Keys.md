### Duplicate keys

Merge sort with duplicate keys: NlogN compares  
Quick sort with duplicate keys:
Algorithm goes quadratic unless partitioning stop on equal keys.  

**solution**

Stop scans on items equal to the partitioning item.  

Partition array into 3 parts so that:
・Entries between lt and gt equal to partition item v.  
・No larger entries to left of lt.  
・No smaller entries to right of gt.  

![](https://i.imgur.com/WNjK4nh.png)


Let v be partitioning item a[lo].  
・Scan i from left to right.  
– (a[i] < v): exchange a[lt] with a[i]; increment both lt and i  
– (a[i] > v): exchange a[gt] with a[i]; decrement gt  
– (a[i] == v): increment i  
```
private static void sort(Comparable[] a, int lo, int hi)
{
  if (hi <= lo) return;
  int lt = lo, gt = hi;
  Comparable v = a[lo];
  int i = lo;
  while (i <= gt)
  {
    int cmp = a[i].compareTo(v);
    if (cmp < 0) exch(a, lt++, i++);
    else if (cmp > 0) exch(a, i, gt--);
    else i++;
  }
  sort(a, lo, lt - 1);
  sort(a, gt + 1, hi);
}
```
Complexity:  
NlogN when all distinct
Linear when only a constant number of distinct keys
