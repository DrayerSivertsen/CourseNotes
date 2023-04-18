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