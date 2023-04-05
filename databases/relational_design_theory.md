# Relational Design Theory

## Database design
1. requirements analysis: data requirements, critical operations on the data
2. conceptual DB design: high-level description of data and constraints - typically using ER model
3. logical DB design: conversion into a schema
    - pick a type of DBMS, relational DBMS is most popular and our focus
4. schema refinement: normalization (eliminating redundancy)
5. physical DB design: consider workloads, indexes and clustering of data
6. application/security design

Design anomalies
1. redundancy
2. update anomaly
3. deletion anomaly

### Design by decomposition
* start with 'mega' relations
* decompose into smaller, better relations with same info
* can do decomposition automatically

Automatic Decomposition
* 'mega' relations + properties of the data
* system decomposes based on properties
* final set of relations satisfy normal form

# Functonal Dependency
when two types agree on the attributes A1, A2 then they must also agree on the attributes B1, B2

* FDs are based on knowledge of real world. They generalize the concept of a key
* if we know that an FD holds on all tuples, then we say that R satisfies the FD
* if we say that R satisfies an FD 'F', we are stating a constraint on R

### Trivial FD
* those that are true for every relation
* X->Y is trivial if Y is a subset of X

### Nontrivial FD
* X->Y is called nontrivial if at least one of the attributes in Y is not among the attriutes in X

### Completely nontrivial FD
* called completely nontrivial if none of the attributes in Y is one of the attributes in X