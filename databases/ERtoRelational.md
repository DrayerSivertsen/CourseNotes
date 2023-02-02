# Mapping ER to Relational model

## Entity Sets to Relations

ER model attributes must have single values
single attributes can be broken down to the smaller parts

## Relationship Sets to Relations
for many - many include the primary keys, and attributes of the relationship itself

primary keys become foreign keys to enforce integrity of data

if one-to-many or many-to-one (allows relation to have a minimal key)
simply use one primary key - of many (each many has one)
and foreign keys of proj and ssn

if one-to-one relationship
either key works but only a single primary key is necessary

if partial participation the table will include a lot of NULL values (pay attention to how many instances of the relation appear)

total participation - needs to be enforced using assertion and triggers

