Writing data to Main Memory
==

# Writing to the cache
In a cache, each block within it should have a cache memory address.

Last week we discussed the cache read,
which there could be a cache hit, miss, or eviction (not discussed).

**Eviction**  
When a block is full, we clear the block to allocate space for new information.

Now we will be talking about the writing.
When writing, it would be either a:

1. hit:
    * write through -> immediately write block to memory.
    * write back -> cache wait, to write block only when the cache block is evicted.
2. miss:
    * write allocate -> read a block into the cache, update the copy on the cache.
    * write no-allocate -> send the write to the main memory, but do not load into the cache.

# Typical approach

1. Write hit -> write through, write miss -> write-no-allocate
2. Write hit -> write back, write miss -> write-allocate

# Dirty Bit
A *dirty bit* means that a block has been modified.
If the dirty bit of a block is 1, it means it is modified, 0 otherwise.

# Cache Line
Things to know:  
1. Assume that a cache block has 8 bytes which is 2 cubed.
2. Addresses have 32 bits, which have to know the binary representation of the address.
3. The power determines the number of zeroes from the least significant bits.
Apparently addresses end with zeros.

For example, a cache line has the following info  
Block Address: `AC B9 35 98`  
Dirty Bit: `0`  
Valid: `1`  
Word addresses: `E4, 38, 05, ...`  

# Types of Cache Mapping to Main Memory
There are two: associative and direct mapped

Let's take a look at the traditional cache memory.
The TCM has address and content.
Address is requested, and the value is fetched.

## Associative 
In ACM, we have key and values, analogous to the TCM's address and content.
Here. however, you can request for the key's value, but there may or may not be data contained in the address.

* The key can be any size (e.g. 29 bits)
* and there are a small number of lines (e.g. 32 lines) for each key address of the block value (8B).

Assume that the block size is $B \equiv 64 \text{bytes} = 2^6 \text{bytes}$, and the number of lines is $L \equiv 512 \text{bytes}$.
So the size of cache is $C = B \times L = 32 \text{KB}$ which does not include a dirty bit.
Therefore ACM does not have a dirty bit -- only data.

Number of set: 1 (default)  
The address size is 32 bits (4 bytes).

In TCM, we need to set the LSBs to zero.
We don't do it in ACM, we just call it the block offset.
In this case, we offset by $\log_{2}(B) = 6$ bits.
So we have 26 remaining bits for the address called "TAG".

The operation is all in the hardware -- fast!
The input is the 32 bit address, and we extract 26 bits, with the remaining 6 as the offset.
Then, the cache sends the tag to associative memory.

If there's a match, we retrieve a 64B data block from associative memory.
Then we use the offset to extract the desired word, then it is sent to the CPU.

If there's no match, we select a block to evict, which will be chosen based on LRU (Least recently used block).

### LRU
Replacement policy.
If the requested block is dirty, the cache send tag to main memory, get 64B back, and update the cache line.

## Direct mapping
Index 9b
address 32b
cache block: 64B
cache line: $512 \text{lines per block} = 2^9$

So for the address we have a 17-bit TAG, the index (9 bits), and the offset (6 bits).
The CPU sends the TAG to the cache line, if it exists, ...
