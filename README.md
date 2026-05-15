# RV-Sparse-Coding-Challenge

## Overview

This implementation provides a sparse_multiply function that:

- Converts a dense row-major matrix into Compressed Sparse Row (CSR) format.
- Computes the matrix-vector multiplication: y=A×x

without using any dynamic memory allocation.

All buffers are pre-allocated by the caller.

The sparse matrix is stored using three arrays:

1. values: stores all non-zero matrix elements.
2. col_indices: stores the column index corresponding to each value.
3. row_ptrs: stores the starting index of each row in the values array.

## Parameters

1. rows: number of matrix rows
2. cols: number of matrix columns
3. A: input dense matrix (row-major)
4. x: input vector
5. out_nnz: output total non-zero count
6. values: CSR non-zero values buffer
7. col_indices: CSR column indices buffer
8. row_ptrs: CSR row pointer buffer
9. y: Output vector result

## Algorithm

For each matrix element:

1. Check whether the value is non-zero.
2. Store non-zero values into CSR arrays.
3. Accumulate the matrix-vector product.
4. Update row pointers after each row.

Time Complexity: O(rows×cols)

Space Complexity:O(nnz)

(where nnz is the number of non-zero elements.)

## Output

```Iter 0 [ 27x 28, density=0.26, nnz= 183]: PASS (Max error: 0.00e+00)
Iter  1 [ 16x 17, density=0.23, nnz=  72]: PASS (Max error: 0.00e+00)
Iter  2 [ 33x 31, density=0.14, nnz= 137]: PASS (Max error: 0.00e+00)
Iter  3 [  7x  9, density=0.09, nnz=   3]: PASS (Max error: 0.00e+00)
Iter  4 [ 34x 43, density=0.34, nnz= 520]: PASS (Max error: 0.00e+00)
Iter  5 [ 43x 37, density=0.18, nnz= 283]: PASS (Max error: 0.00e+00)
.
.
.
.
Iter 95 [ 36x  7, density=0.19, nnz=  54]: PASS (Max error: 0.00e+00)
Iter 96 [ 43x 38, density=0.23, nnz= 366]: PASS (Max error: 0.00e+00)
Iter 97 [ 11x 44, density=0.19, nnz=  95]: PASS (Max error: 0.00e+00)
Iter 98 [ 27x 15, density=0.09, nnz=  42]: PASS (Max error: 0.00e+00)
Iter 99 [ 21x  7, density=0.13, nnz=  13]: PASS (Max error: 0.00e+00)

All tests passed! (100/100 iterations passed)
```
