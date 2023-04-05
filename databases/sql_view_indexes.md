# SQL: Views and Indexes


## View
* a view is a relation defined in termso f stored tables and other views
* two kinds:
    1. virtual = not stored in the database; just a query for constructing the relation
    2. materialized = actually constructed and stored

### Uses of view
* the uses of "views" include: 
    - provide logical data independence
    - serve as a unit of access control for security purposes
    - simplify common/complex queries by predefining useful "tables"
    - tailor DB schema to meet the needs of different applications

### Modifying Views
* how can we modify a view if it is supposedly virtual?
    - insert, delete, update
* many views cannot be modified, as we will soon see
* some views can be modified (called updatable views)

* insertion of a tuple into a view
    - insertion of corresponding tupes into its base table
    - missing column values lead to insertion of NULL or default values
    - the inserted base tuples should generate the new view tuples

* updatable views
    - and updatable view V(R)'s definition must satisfy certain requirments
        * FROM: consists of one occurance of R
        * WHERE: does not involve R in a subquery
        * SELECT: includes "enough" attributes, has only simple field references, and not DISTINCT
        * no GROUP BY or HAVING clauses
- a modification of V is translated to a corresponding modification of R
- note: some vendors support more or less in this area

### Deletes from Updatable Views
* when deleting tuples from a view, system should delete all tuples from base table that can potentially produce the deleted view tuples

### Dropping view
* DROP VIEW
* base tables are not affected in any way
* may impact other views/applications

## Indexes
* index: data structure used to speed access to types of a relation, given values of one or more attributes
* CREATE INDEX ___ ON

### Database Tuning
* a major problem in making a database run fast is deciding which indexes to create
* benefit: an index speeds up queries that can use it
* tradeoff: an index slows down all modifications (insert, delete, update) on its relation becuase the index must be modified too

### Useful indexes
* often, the most useful index on a relation is an index on the relation's key
    - the keys are ususaly used frequently in queries
    - since each tuple has a unique value for the key, the search on index returns either nothing or a single tuple
* on some occasions, an index can be effective, even if the index is not a key
    - if the attribute is almost a key, only a few tuples share the same value for the index attribute
    - if the tuples are clustered based on the index attributes

