#### Hash Table  
Save items in a key-indexed table(index is a function of the key)  
Hash function: Method for computing array index from key.

Issues  
・Computing the hash function.  
・Equality test: Method for checking whether two keys are equal.  
・Collision resolution: Algorithm and data structure to handle two keys that hash to the same array index.  

Classic space-time tradeoff  
・No space limitation: trivial hash function with key as index.  
・No time limitation: trivial collision resolution with sequential search.  
・Space and time limitations: hashing (the real world).  

**hash function**  
Idealistic goal. Scramble the keys uniformly to produce a table index.  
・Efficiently computable.  
・Each table index equally likely for each key.  

Java implementation: all java classes inherit a method hashCode(), which return a 32 - bit int. Then do the modular to decide the index.

**collisions**: two distinct keys hashing to same index  

solution1 : separate chaining

Use an array of M < N linked lists. [H. P. Luhn, IBM 1953]  
・Hash: map key to integer i between 0 and M - 1.  
・Insert: put at front of ith chain (if not already there).  
・Search: need to search only ith chain.  

![](https://i.imgur.com/y5i3dPg.png)  


solution 2: linear probing(open addressing)  

When a new key collides, find next empty slot, and put it there.

Hash. Map key to integer i between 0 and M-1.  
Insert. Put at table index i if free; if not try i+1, i+2, etc.  
Search. Search table index i; if occupied but no match, try i+1, i+2, etc.  
Note. Array size M must be greater than number of key-value pairs N.    

Comparison:

Separate chaining.  
・Easier to implement delete.  
・Performance degrades gracefully.  
・Clustering less sensitive to poorly-designed hash function.  

Linear probing.  
・Less wasted space.  
・Better cache performance.  

There are many other hashing structure base on separate chaining and linear probing