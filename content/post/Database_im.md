+++
title = "Database System Implementation"
date = "2022-12-09"
tags = [
    "database",
    "c++",
]
+++
 Examining the internal workings of modern database management systems, addressing core concepts and components utilized in high-performance transaction processing systems (OLTP) and large-scale analytical systems (OLAP). Emphasizing efficiency and correctness, covers key topics like the introduction to relational databases, storage management, access paths, and query execution. The focus is on understanding the intricate mechanisms behind the effective functioning of contemporary database systems, with an emphasis on practical implementation and optimization.
<!--more-->
### [HW1](https://github.com/le-que/Database-System-Implementation/tree/main/hw1)
Implement an external sort algorithm with a specified memory constraint. The algorithm involves dividing the input into smaller runs, each adhering to the memory limit, sorting these runs in memory, and finally applying a K-way merge algorithm to efficiently merge the sorted runs.

### [HW2](https://github.com/le-que/Database-System-Implementation/tree/main/hw2)
 Implement a buffer manager using the 2Q replacement strategy, allowing the locking, reading, and writing of pages identified by 64-bit page ids, which are divided into segment id and segment page id components. The implementation supports variable page and buffer sizes, stores written pages in segment-specific files, and enables concurrent fixing and unfixing of pages from different threads.

### [HW3](https://github.com/le-que/Database-System-Implementation/tree/main/hw3)
Implement a B+-Tree index for a database. The B+-Tree implementation must support lookup, insert, and erase operations, utilizing page IDs and the buffer manager instead of pointers to handle child nodes in the tree.

### [HW4](https://github.com/le-que/Database-System-Implementation/tree/main/hw4/src)
implement physical operators for a database, supporting operations such as Print, Projection, Select (with relational operators), Sort, HashJoin, HashAggregation, Union, UnionAll, Intersect, IntersectAll, Except, and ExceptAll. The code should handle tuples, attributes, predicates, sorting, joining, aggregation, and set operations with both set and bag semantics.

