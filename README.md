# Unordered Iteration and Table Modification in Nested Lua Tables

This repository demonstrates a subtle bug that can occur in Lua when iterating over nested tables and modifying them concurrently.  Lua's `pairs` iterator does not guarantee any particular order of iteration, and attempting to modify the table during iteration can lead to elements being skipped or unexpected behavior.

The `bug.lua` file contains code that exhibits this issue. The `bugSolution.lua` file provides a corrected version that demonstrates best practices for safe iteration and modification.

## How to reproduce

1. Clone the repository.
2. Run `bug.lua`. Observe that the output is not as expected, demonstrating that the inner table elements were not properly processed. 
3. Run `bugSolution.lua` to see corrected behavior.

## Solution

The solution involves creating a copy of the table to iterate, avoiding in-place modification during traversal and ensuring all elements are visited.