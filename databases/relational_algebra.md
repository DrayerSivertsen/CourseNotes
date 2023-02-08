# Relational Algebra

* an algebra whose operands are relations or variables that represent relations
* operators are designed to do the most common things that we need to do with relations in a database


* queries return relations
    * closure
    * compositionality - query returns a relation which can be used to query again

## Core Relational Algebra

### Union, Intersection, Difference
set operators. Relations must have the same schema

### Selection
- C is a condition that reers to attributes of R
- schema of result is the same as that of the input relation R

### Projection
pick columns of attributes, eliminate duplicate tuples, if any

### Extended Projection
the attribute list may contain arbitrary expression involving attributes:
- arithmetic operations on attributes
- duplicate occurences of the same attribute

### Cartesian Product
pair each tuple r in R with each tuple s in S

### Join
take the product R x S, then apply selection to the result

types: 
- theta-join
- equi-join
- natural join
- semi join

#### Theta-join
selection involves a condition or multiple conditions

#### Natural-join
* connects two relations by:
    - equating attributes of the same name
    - projecting out one copy of each pair of equated attributes

join with attributes that are present (same keys)

### Renaming
disambiguate relation and attribute names, different attributes are renamed for conhesion

refer to the same relation in the same statement rename on of the attributes for clarity

## Notations

### Expressions with several operators
precedence of relational operators
1. parenthesis
2. union, selection
3. join, cartesian
4. intersection

### Sequences of Assignments
* introduce names for intermediate relations using the assignment operator
* then a query can be written as a sequential program consisting of a series of assignments

### Expression Trees
* leaves are operands -- variables standing for relation
* interior nodes are operators, applied to their child

## Bag Semantics
* set semantics: no duplicates
* bag semantics: duplicates possible, no order
    - SQL uses the bad semantics: a table could have duplicated tuples

### Operations on bags
* bag union, combine elements from two relations
* bag intersection, take the minimum of the number of occurences in each bag
* bag difference, proper subtract the number of occurences in the two bags

* selection and project, is applied to each tuple independently. duplicates are not eliminated in the result

### Laws for bags
* some laws for sets still hold for bags
    - union intersection are still communtative and associative
* some laws for sets might not hold for bags

### Duplicate elimination
relation with one copy of each tuple that appears one or more times in R

### Sorting
sort the records in R according to attributes on list L 

### Aggregation
takes a collection of values and returns a single value as a result
e.g. avg, max, min, sum, count

### Grouping
* aggregation operation applied to an attribute calculates the value for the entire column

## Outer Join
* extension o fthe natural join operation that avoids loss of information
* computes the join and then adds "dangling" tupes from the rest of the data

Types:
* full outer joing
* left outer join
* right outer join

## Limitation of Relational Algebra
* some queries cannot be represented
* example: recursion
* more expressive languages: Datalog

