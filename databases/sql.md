# SQL


NOT NULL specifies that values cannot exist as NULL
CREATE DOMAIN - define new domains

## creating and modifying relations using SQL
### declaring keys - primary key
```
int Primary Key
```
```
Primary Key(ssn)
```
cannot have NULL

### UNIQUE constraint
```
int UNIQUE
```
```
UNIQUE (dno,name)
```
can have NULL values

### CHECK clause
allows you to define domain constrains
```
CHECK (salary>-0)
```

### foreign-key constraint
within attribute:
```
REFERENCES dept(dept#)
```
separate declaration:
```
FOREIGN KEY (dno) REFERENCES dept(dept#)
```
can include more than one foreign keys
might have circular references with circular keys (tend to be problematic)

* also called "referential integrity"

### giving names to constraints
* name a constraint
* userful for later altering
```
CONSTRAINT FK1 FOREIGN KEY ...
```

### enforcing foreign-key constraints
* modification (delete, update) of dept whose old "dept#" is referenced by a record in emp
strategies:
- default: reject
- cascade: change the emp tuple correspondingly
    * delete in dept: delete the referring records in emp
    * update in dept: update the dno of the referring records in emp to the new value
- set Null: change dno value in the records to NULL

### choosing a policy for modifications
* add "ON"
```
ON DELETE SET NULL
ON UPDATE CASCADE
```
if not assigned constraints will use the default policy

### deleting a table completely
```
DROP TABLE emp;
```
in contrast to clean a table simply update or delete certain values

### add or drop attributes from the relation
to add attributes:
```
ALTER TABLE relatonName ADD attribName attriDomain
```

to drop attributes:
```
ALTER TABLE relatonName DROP attribName attriDomain
```

the NOT NULL command is not allowed because when a table is altered the new attribute will be a NULL value right after the change!

work around: allow NULL values then change the values from NULL, then update back to not allowing NULL


## Database Modifications
* a modification command does not return a result, but changes the database in some way
* three kinds of modification
    - insert a tuple or tuples
    - delete a tuple or tuples
    - update the values of an existing tuple or tuples

### Tuple insertion
* can drop attribute names if we provide all values in order
* if we don't provide all attributes, they will be willed with NULL

Default Values
* in a CREATE TABLE statement, we can define a DEFAULT value for an attribute
* when an inserted tuple has no value for that attribute, the default will be used

Insertion of a query's result
* we may insert the entire result of a query into a relation using the form
```
INSERT INTO relation
(subquery);
```

Deletion
* to delete tupes satisfying a condition from some relation:
```
DELETE FROM relation
[WHERE condition];
```
* there is no way to delete only a single occurence of a tuple that appears twice in a relation

Deletion proceeds in two stages:
1. mark all tuples for which the WHERE condition is satisfied
2. Delete the marked tuples

## Updates
* to change certain attributes in certain tuples of a relation:
```
UPDATE relation
SET assignments
WHERE condition;
```

## Assertions
* so far most contraints are within one table
    - attribute-based checks
    - tuple based checks
* Assertions:
    - constraints over a table as a whole or multiple tables
    - it is a boolean valued SQL expression that must be true at all times
* an assertion must always be true at transaction boundaries
    - any modification that causes it to become false is rejected
* similar to tables, assertions can be dropped by a DROP command

