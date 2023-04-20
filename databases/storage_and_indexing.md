# Storage and Indexing

FILE: a collection of pages, each containing a number of records. The file API must support:
* insert/delete/modify record
* fetch a particular record
* scan all records

PAGE: fixeed number of bytes

## Records
* record represent tuples of a relation
* records are stored pages
* record id = RID

* when a record needs to be accessed or updates, the entire page (disk block) that the record is stored needs to be moved into main memory

Fixed-length records -> each field has the same length in all the records
Fariable length records
* remarks: NULLs require no space at all; there is some directory overhead

### Fixed Length Records
* a page is a collections of slots, each containing a record
* in first alternative (left), free space management records movement

### Variable Length Records
* slot directory to store entry index(offset) and length

### Alternative File Organizations
* heap files: unordered. Fine for file scan retrieving all records
* sorted files: best for retrieval in search key order, or if only a 'range' of records is needed. Expensive to maintain
* indexes: data structures to organize records via trees or hashing

## Unordered Heap Files
* simples file structure contains records in no particular order
* as file grosw and shrinks, pages are allocated and deallocated
* to support record level operations, we must:
    * keep track of pages in a file
    * keep track of free space on pages
    * keep track of records on a page
Methods for heap files:
Linked list, page directory

## Cost Model for Analysis
* average-case analysis; based on several simplistic assumptions
* we ignore CPU cost, for simplicity:
D: the average time to read or write a disk page
B: the number of pages
R: number of records per block

* initially, we simply count number of disk blocks

### Operations to compare
* scan: fetch all records from disk
* equality search: fetch the pages that contain qualifying records from disk
* range selection: fetch the pages that contain the records that satisfy a range selection
* insert a record: identify the page where record should be inserted, fetch that page, write back to disk
* delete a record


Sorted Files
* heap files are lazy on update - you end up paying on searching
* sorted files eagerly maintain the file on update
    * the opposite choice in the trade-off

# Indexes
* an index on a file speeds up selections on the search key fields for the index
    * any subset of the fields of a relation can be the search key

Works in a similar fashion as hash map 

## Alternatives for Data entries
* alternative 1:
    - if this is used, index structure is a file organization for data records
    - at most one index on a given collection of data records can use alternative 1
* alternative 2 and 3: 
    - data entries typically much smaller than data records. So, better than alternative 1 with large data records, especially if search keys are small
    - alternative 3 more compact that alternative 2, but leads to variable sized data entries even if search keys are of fixed length

## Index classifications
1. primary vs secondary
- if search key is the primary key, then called primary index. The index is guaranteed not to have duplicate search key values
- otherwise called secondary key. May have duplicates
- unique index: a secondary index with no duplicate search keys

2. clustered vs unclustered
- if order of data records is the same as, or 'close to', order of data entries, then called cluster index
    - a file can be clustered on at most one search key
    - alternative 1 implies clustered; in practice; clustered

### Understanding the Workload
* for updates in the workload:
    - the type of update (insert/delete/update), and the attributes that are affected
    - frequency of the updates

# Choice of Indexes
* one approach: consider the most important queries in turn. Consider the best plan using current indexes, and see if a better plan is possible with an additional index

## Guidelines
1. attributes in where clause are candidates for index keys
    - exact match condition suggests hash index
    - range query suggests tree index
        - clustering is especially useful for range queries; can also help on equality queries if there are many duplicates
2. multi-attribute search keys should be considered when a WHERE clause contains several conditions
    - order of attributes is is important for range queries 
    - such indexes can sometimes enable index-only strategies for important queries
        - for index-only strategies, clustering is not important 
3. try to choose indexes that benefit as many queries as possible. Since only one index can be clustered per relation, choose it based on important queries that would benefit the most from clustering

