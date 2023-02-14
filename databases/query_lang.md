# SQL as a Query Language

standardized language for querying and manipulating relational data

* query capabilities of SQL are similar to those in relational algebra. 
* SQL language has several aspects:
    * data definition language (DDL)
    * query language

### What is special about SQL?
* you describe what you want
* the job of the DBMS is to figure out how to compute what you want efficiently
## SELECT

### Basic form
SELECT desired attributes
FROM one or more tables
WHERE condition on the rows of the tables

### "Select" Clause
specify attributes to project onto 
- use the star * to denote all attributes

if no where clause used it performs the cartesian product of the selected

### Eliminate Duplicates
"SELECT" does not automatically remove duplicates

### Allows renaming of returned results
"as" keyword allows you to provide a new name for the returned results

'temporary' as status adds a new column with temporary as default value

can perform operations on the SELECT and then save as new column

'' to show as a single quote in a string

## FROM
* specify relations
* renaming relations
    * use "as" to define "variables", disabiguate multiple reference to the same relation


rename attributes with long names using "as"


<> and != represent not equal to

## WHERE
* specify conditions
* optional 
* complex conditions
    * combination of AND, OR, NOT ...

* string patterns:
    * LIKE keyword uses a regular expression to contain the pattern that the values are matches against
    * "s LIKE p": string s matches pattern p

'%L&' L character in the middle
'L%' starts with L
'L___' wildcard characters

CONCAT concat attributes that are string

### Handling NULL
conditions involving NULL evaluate to unknown, rather than true or false
if one part of a conditions evaluates to unknown the rest of the condition may also have the same evaluation

How to include NULL:
* IS NULL
* IS NOT NULL

## ORDER BY
* allows you to order the returned attributes
default is acsending order
'desc' is used to sort in descending order
listed attributes are ordered based on precedence (highests left, lowest right)

NULLS last moves the null values to the end

# Set Operations
* duplicates are removed in the results

UNION, INTERSECT
- same operation as relational algebra

'distinct' keyword removes duplicates same as a set

adding the 'ALL' keyword to a operator 
- UNION ALL, INTERSECT ALL, EXCEPT ALL, includes duplicates

## Aggregations
* MIN, MAX, SUM, COUNT, AVG
    * input: collection of numbers/strings
    * output: relation with a single attribute with a single row

except "COUNT" all aggregations apply a single attribute
COUNT can except more than one or star

## GROUP BY clause
is used to apply aggregate funcation to a group of sets of tuples
- aggregation is applied to each group separately

SELECT attributes must also appear in the GROUP BY or it produces an error

## HAVING clause
used along with GROUP BY to select some groups 
- we can't define conditions to aggregate results in the WHERE clause
- predicate in having clause applied after formation of groups