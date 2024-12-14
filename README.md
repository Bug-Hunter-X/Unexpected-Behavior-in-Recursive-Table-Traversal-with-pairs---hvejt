# Lua Recursive Table Traversal Bug

This repository demonstrates a subtle bug in Lua related to modifying a table while iterating over it using `pairs`.  The `pairs` iterator can exhibit unexpected behavior when the table's structure is altered during iteration.

The `bug.lua` file contains a recursive function that aims to traverse a nested table.  However, due to the interaction between `pairs` and table modification, the function might not process all elements as expected.

The `bugSolution.lua` file provides a corrected version that uses a different iteration approach to avoid this issue.

## Bug Explanation

The original `foo` function uses `pairs` to iterate through the nested table. If it modifies the table, such as removing or adding elements, `pairs`'s behavior becomes unpredictable.  This is because the internal state of `pairs` might be invalidated.

## Solution

The solution uses a different iteration approach by creating a copy of the keys to iterate through. It ensures the keys are not affected by changes made during the iteration process.