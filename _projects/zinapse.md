---
layout: default
title: Zinapse
---

## Protein-Protein Interaction Profiling
Traditional PPI analysis often suffers from the overhead of high-level languages. **Zinapse** leverages Zig's manual memory management and "Comptime" to optimize the traversal of sparse protein matrices.

### The Algorithm
The prioritization of disease genes within the PPI network is calculated using a weighted adjacency score:

$$S_{uv} = \frac{|\mathcal{N}(u) \cap \mathcal{N}(v)|}{\sqrt{|\mathcal{N}(u)| \cdot |\mathcal{N}(v)|}}$$

### Implementation
By utilizing a **Compressed Sparse Row (CSR)** format, Zinapse achieves significant cache efficiency over standard adjacency lists.

```zig
const PPI_Network = struct {
    values: []f32,
    col_indices: []u32,
    row_ptr: []u32,

    pub fn deinit(self: *PPI_Network, allocator: Allocator) void {
        allocator.free(self.values);
        allocator.free(self.col_indices);
        allocator.free(self.row_ptr);
    }
};
