### Elementary sort

A **total order** is a binary relation ≤ that satisfies:   
・Antisymmetry: if v ≤ w and w ≤ v, then v = w.   
・Transitivity: if v ≤ w and w ≤ x, then v ≤ x.  
・Totality: either v ≤ w or w ≤ v or both.

#### selectoin sort  
for each element in array, find the smallest element from the rest of array

time complexity: O(n^2)
```
public class Selection
{
   public static void sort(Comparable[] a)
   {
      int N = a.length;
      for (int i = 0; i < N; i++)
      {
         int min = i;
         for (int j = i+1; j < N; j++)
            if (less(a[j], a[min]))
               min = j;
         exch(a, i, min);
      }
   }
   private static boolean less(Comparable v, Comparable w)
   {  /* as before */  }
   private static void exch(Comparable[] a, int i, int j)
   {  /* as before */  }
}
```

#### insertion sort
for each element in array, swap a[i] with each larger entry to its left.  

time complexity: O(n^2)

```
 
public class Insertion
{
   public static void sort(Comparable[] a)
   {
      int N = a.length;
      for (int i = 0; i < N; i++)
         for (int j = i; j > 0; j--)
            if (less(a[j], a[j-1]))
               exch(a, j, j-1);
            else break;
   }
   private static boolean less(Comparable v, Comparable w)
   {  /* as before */  }
   private static void exch(Comparable[] a, int i, int j)
   {  /* as before */  }
}
```


#### array shuffle 
assign a random number for each entry in array, then sort it.

