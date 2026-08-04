The following table summarizes the results of the 4-Way BSA LRU (Least Recently Used) vs 4-Way BSA MRU (Most Recently Used) program.

|   Sequential (64 accesses)  |
| -------------- |
|  LRU    |  MRU  |
| -------|------ |
| Hit Rate: 0.00%  | Hit Rate: 25.00%    |
| AMAT (Non Load-Through):  41.00 cycles    | AMAT (Non Load-Through):  31.00 cycles   |
| AMAT (Load-Through):  11.00 cycles  | AMAT (Load-Through):  8.50 cycle |
| -------------- |
|     Mid-Repeat (160 accesses)   |
| -------------- |
|  LRU    |  MRU  |
| -------|------  |
| Hit Rate: 10.00%   | Hit Rate: 42.50%     |
| AMAT (Non Load-Through):  37.00 cycles    | AMAT (Non Load-Through):  24.00 cycles   |
| AMAT (Load-Through):  10.00 cycles   | AMAT (Load-Through):  6.75 cycles        |
| --------------- |
|    Random (64 accesses)  | 
| -------------- |
| LRU    |    MRU     |
| ---------|-------- |
| Hit Rate: 10.00%    | Hit Rate: 42.50%  |
| AMAT (Non Load-Through):  37.00 cycles    | AMAT (Non Load-Through):  24.00 cycles   |
| AMAT (Load-Through):  10.00 cycles        | AMAT (Load-Through):  6.75 cycles        |

Random (64 accesses)
LRU
MRU
Hit Rate: 1.56%
AMAT (Non Load-Through):  40.38 cycles
AMAT (Load-Through):  10.84 cycles
Hit Rate: 1.56%
AMAT (Non Load-Through):  40.38 cycles
AMAT (Load-Through):  10.84 cycles


Observations:
Sequential: 
MRU achieves a higher hit rate than LRU as it evicts the most recently accessed item, rather than LRU which evicts the least recently accessed one. Both AMATs for MRU are lower than LRU since older blocks are kept and can be referenced again faster. 
Mid-Repeat:
Similar to the sequential sequence, the hit rate for MRU is higher and its AMATs are lower. Since mid-repeat sequences have loops that are bigger than the cache’s capacity, one on hand, the LRU has to update its storage and replace the older blocks that are needed for the next loop. On the other hand, MRU only evicts the most recently used block during loops therefore increasing the chances of getting the needed blocks for the next loop.
Random:
The hit rates and AMATS for both LRU and MRU are the same. Since the addresses are random, they both hit only once out of the 64 accesses.


Based on the results given by the program, MRU performs better for sequential accessing, mid-repeat accessing, and handling loops that could be larger than the cache capacity because it preserves older cache blocks and removes the newest ones. This led to higher hit rates and lower AMATs. 
The hit rates are identical regardless of read policy. However, the AMAT results for all test cases that use Load-Through are lower than Non Load-Through. The Load-Through read policy sends the word being requested directly to the CPU. This is executed while the other blocks fill other cache blocks. 
