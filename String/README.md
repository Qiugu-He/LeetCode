## Array && String

### Common Techniqu: HashTable

```
A hash table is a data structure that maps keys to values for highly efficient lookup. There are a number of ways of implementing this. Here, we will describe a simple but common implementation. 

In a simple implementation of hash table: an array of linked lists and a hash code function. To insert a key (which might be a string or essentially any other data type) and value, we do the following:

	○ First, compute the key's hash code, which will usually be an int or long. Note that two different keys could have the same hash code, as there may be an infinite number of keys and a finite number of ints. 
	
	○ Then, map the hash code to an index in the array. This could be done with something like hash (key) % array_length. Two different hash codes could, map to the same index. 
	
	○ At this index, there is a linked list of keys and values. Store the key and value in this index. We must use a linked list because of collisions: you could have two different keys with the same hash code, or two different hash codes that map to the same index. 

To retrieve the value pair by its key, repeat this process. Compute the hash code from the key  ->  compute the index from the hash code -> search through the linked list for the value with this key. 
Worst case  O( N ), N = # of keys

```
