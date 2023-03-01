# Web Security

SQL - Structured Query Language

* SQL commands are uaually called queries
* contain keywords, table name, attribute names, and variables

### SQL Query Scenario
SQL Injection
* Scenario #1 - user provides username=alice AND password=12345
* scenario #2 - user provides username=alice AND password=54321
* scenario #3 - user provides username=alice AND password=a OR a=a
    * inject a universal truth to make the whole statement always true