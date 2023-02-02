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




