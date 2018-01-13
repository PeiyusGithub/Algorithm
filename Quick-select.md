### Selection Algorithms

#### Quick-select

Partition array exactly like quick sort:  
・Entry a[j] is in place.  
・No larger entry to the left of j.  
・No smaller entry to the right of j.  
```
public static Comparable select(Comparable[] a, int k)
{
  StdRandom.shuffle(a);
  int lo = 0, hi = a.length - 1;
  while (hi > lo)
  {
    int j = partition(a, lo, hi);
    if (j < k) 
    	lo = j + 1;
    else if (j > k) 
    	hi = j - 1;
    else
    	return a[k];
  }
  return a[k];
}
```
Intuitively, each partitioning step splits array approximately in half:  
N + N / 2 + N / 4 + … + 1 ~ 2N compares. Quick-select takes linear time on average.  