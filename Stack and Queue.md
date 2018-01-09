## Stack and Queue

### Stack
Use **linked list** to simulate stack:  
>first in first out from the first node.

Use **array** to implement stack:  
>operation happen at the last element of array.  
>Defect: stack overflows when N exceeds capacity. So we can use resizing array, but how?  
>
>Efficient solution:  
・push(): double size of array s[] when array is full.  
・pop(): halve size of array s[] when array is one-quarter full.  
since we dont want push-pop-push-pop-… sequence when array is full, it will keep double and halve the array.

##### Trade off:   
![a](https://i.imgur.com/E1XejEn.png?1)

### Queue
Use **linked list** and **resizing array** to simulate queue.  
Java generic linked list implementation:   
![generic](https://i.imgur.com/fVCixIf.png?1)
