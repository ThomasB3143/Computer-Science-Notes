Section: [[Fundamental Data Structures (root)]]
## Key-Value Pairs

We can store data consisting of pairs of **keys** and **values**, where we can **look up** the value using the paired key
# Hash Tables

A hash table consists of a bucket array and a hash function
## Bucket Arrays

A **bucket array** is an array where each cell stores a collection of key-value pairs. The size of this array is the **capacity** of the hash table
## Hash Functions

A **hash function** $h$ is a function mapping each key $k$ to an integer in the range $[0,N-1]$ (where $N$ is the capacity)

We aim to use $h(k)$ as an index into the [[Hash Tables#Bucket Arrays|bucket array]] $A$. So the key-value pair $(k,v)$ will be stored in the bucket $A[h(k)]$

When two keys map to the same index, a **collision** has occurred

Hash functions are typically comprised of two functions, the mapping of **keys to integers** and the mapping of **integers to integers in the range $[0,N-1]$** applied sequentially

The latter is often done through modular $N$ arithmetic

The goal of a hash function is to **disperse** the keys in an apparently **random** way. It should be **efficiently computable** and each index should be **equally likely** for the set of all possible keys.
## Collisions

A large number of collisions will reduce the performance of a hash table, hence a good hash function seeks to minimise the number of collisions. Let's discuss four methods for **handling** collisions

All besides [[Hash Tables#Separate Chaining|separate chaining]] are examples of **open addressing schemes**. Meaning they store at most **one entry per bucket**
### Separate Chaining

Each bucket stores a **list** of all entries that map to said bucket. The cost is proportional to the length of the list, and the average length is $N/M$ where $N$ is the amount of data and $M$ is the capacity of the [[Hash Tables#Bucket Arrays|bucket array]]

In the worst case, all keys hash to the same list
### Linear Probing

If we try to insert an entry $(k,v)$ into a bucket $A[i]$ that is already occupied, we try again at the next bucket $A[(i+1)\mod N]$ 

This is iterative, as we try $A[(i+2)\mod N]$ and so on, until finding an empty bucket

Insert and search cost depends on the length of the cluster, with the average length being $N/M$. In the worst case, all keys hash to the **same cluster**
### Quadratic Probing

Much like linear probing, we iteratively try buckets:

$A[(i+f(j))\mod N]$ for $j=0,1,2,\dots$ where $f(j)=j^2$

until an empty bucket is found

This avoids the clustering patterns in [[Hash Tables#Linear Probing|linear probing]] however can create its own kind of clustering (**secondary clustering**)

This may not find an empty bucket, even if one exists!
### Double Hashing

We iteratively try the buckets:

$A[(i+f(j))\mod N]$ for $j=0,1,2,\dots$ where $f(j)=j\times h^\prime(k)$

where $h^\prime$ is dubbed the **secondary hash function**. A common choice is $h^\prime(k)=q-(k\mod q)$ for some prime number $q<N$. This function should **not evaluate to zero**

We use a prime number as the size of the array will ensure a better **distribution** of keys are tried and reduces the chance of looping through a small set of indexes (an issue with quadratic probing)
### Comparisons

Open addressing schemes are more **memory efficient** compared to [[Hash Tables#Separate Chaining|separate chaining]] 

As for run times, separate chaining is often on-par or faster than other methods (preferred when memory is not an issue)
## Deletions and Tombstones

Deletions must not hinder future searches, if a bucket is just left empty then it will hinder further probes. We don't want to leave the bucket unusable thought

We use **tombstones** to solve this, markers left in a bucket after deletion

When a tombstone is encountered during **probing**, we know to continue

If a tombstone is encountered during **insertion**, then we may continue probing to avoid creating duplicates. Once we find an empty space we can go back to the tombstone and insert! (if we find the data is already stored then we do not)

The use of tombstones lengthens the average probe sequence, we have two ways to fix this:

### Local Reorganisation

After deleting a key, continue to follow the probe sequence of the key and move records into the vacated bucket (does not work for all collision resolution policies)
#### Periodically Rehash

We can reinsert all records into a new hash table. If we have a record of which keys are accessed most then they can be placed somewhere easier to find!