# Machine 7: 4-Way BSA + LRU vs. 4-Way BSA + MRU


The group was tasked to create a web-based application of a 4-Way BSA + Least Recently Used cache vs. 4-Way BSA + Most Recently Used cache with the following specifications:
## Specifications & Parameters

| Parameter | Value |
| :--- | :--- |
| Associativity | 4-Way Block Set Associative (BSA) |
| Block Size | 4 words (parameterized, power of 2, min 2) |
| Number of Cache Blocks | 16 (parameterized, power of 2, min 4) |
| Main Memory Size | 1024 blocks (fixed) |
| Read Policy | Non-Load-Through and Load-Through (parameterized, both shown below) |
| Cache Hit Time | 1 cycle |
| Miss Penalty per Word | 10 cycles |
| Replacement Policies Compared | LRU (Least Recently Used) vs. MRU (Most Recently Used) |

The results below were produced using the parameters above. Block Size, Number of Cache Blocks, Hit Time, and Miss Penalty per Word are all adjustable in the UI; these are the values used for this run.

### The following table summarizes the results of the 4-Way BSA LRU (Least Recently Used) vs 4-Way BSA MRU (Most Recently Used) program.
Note that these cases share the following settings:

Block Size: 4
Number of Cache Blocks: 16
Cache Hit Time (cycles): 1
Miss Penalty per Word (cycles): 10
Base Sequence Pool: default (1, 2, 3, 4, 5, 6, 7, 8, …)

## Specifications & Parameters
| Test Case | Accesses | Hit Rate (LRU) | Hit Rate (MRU) | AMAT Non-LT (LRU) | AMAT Non-LT (MRU) | AMAT LT (LRU) | AMAT LT (MRU) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Sequential | 64 | 0.00% | 25.00% | 41.00 | 31.00 | 11.00 | 8.50 |
| Mid-Repeat | 160 | 10.00% | 42.50% | 37.00 | 24.00 | 10.00 | 6.75 |
| Random | 64 | 1.56% | 1.56% | 40.38 | 40.38 | 10.84 | 10.84 |

*AMAT values are in cycles. Non-LT = Non-Load-Through, LT = Load-Through.*


## **Observations**:

**1. Sequential:** 
MRU achieves a higher hit rate than LRU as it evicts the most recently accessed item, rather than LRU which evicts the least recently accessed one. Both AMATs for MRU are lower than LRU since older blocks are kept and can be referenced again faster. 


**2. Mid-Repeat:**
Similar to the sequential sequence, the hit rate for MRU is higher and its AMATs are lower. Since mid-repeat sequences have loops that are bigger than the cache’s capacity, one on hand, the LRU has to update its storage and replace the older blocks that are needed for the next loop. On the other hand, MRU only evicts the most recently used block during loops therefore increasing the chances of getting the needed blocks for the next loop.


**3. Random:**
The hit rates and AMATS for both LRU and MRU are the same. Since the addresses are random, they both hit only once out of the 64 accesses.


Based on the results given by the program, MRU performs better for sequential accessing, mid-repeat accessing, and handling loops that could be larger than the cache capacity because it preserves older cache blocks and removes the newest ones. This led to higher hit rates and lower AMATs. 

The hit rates are identical regardless of read policy. However, the AMAT results for all test cases that use Load-Through are lower than Non Load-Through. The Load-Through read policy sends the word being requested directly to the CPU. This is executed while the other blocks fill other cache blocks. 
