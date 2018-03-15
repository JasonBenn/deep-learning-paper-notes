## [The Case for Learned Index Structures](https://arxiv.org/abs/1712.01208)

### Insight
* Indexes are models.
* We use general-purpose models, even for situations tht mihgt have unusual access patterns.
* More computers in the future will have GPUs/TPUs/CPUs with SIMD, so NNs could be more plentiful.

### Methods
* read-only, in-memory analytical workloads.  No insertions.
* B-tree index maps lookup key to position in array of records

*2.1 Budget of typical B-Trees*:
Go from key to location of page, traverse page looking for key
Page is size 100, so average traversal is 50 cycles
1M NN ops in 30 cycles on Tesla V100 GPU

Last mile accuracy is a problem: nets inherently avoid overfitting.
Solution: Kind of like a mixture of experts. Recursive Model Index, where many smaller models are trained as experts on subdivisions of the key space. Don't have to be NNs - could be regression.

### Findings
2-3x speed improvement, 4-100x space savings

### Context
* Many of the related work is starting to be released- learned bloom filters
* Some authors took issue iwth the B-Tree - cuckoo indexes perform on par with RMI, and are simpler to understand
* NVIDIA predict a 1000x increase in GPU speed by 2025. With closer integration of CPU/GPU/TPU units to reduce the handover costs, the GPU/TPU performance curve looks to be the one to ride to achieve maximum performance into the next decade

### Conclusion
Their conclusion: "we believe that the idea of replacing core components of a data management system through learned models has far reaching implications for future systems designs and that this work just provides a glimpse of what might be possible."

### Looking forward
Where else might learned models be useful? Anything where a workload might be personalized to your usage patterns.
