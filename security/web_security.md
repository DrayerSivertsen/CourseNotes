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

* formal name: 'improper neutralization of special elements used in a SQL command'
* occurs due to improper or no sanitization of user input responses

### SQL injection protections
* input sanitization: validate user inputs and neutralize special characters
    * done by implementing RegEx for escaping special chars
        * admin') or 1=1#   admine\'\ or 1=1\#
* prepare better SQL queries
    * parameterize user inputs

### Advances SQL injection attacks
* time-based
* enumerating tables
* there exist toools to automate extraction of SQL tables

### Cross site scripting (XSS)
* inject malicious content into a webpage
* malicious content can be set to execute at desired times using parameters
* types of attacks
    * stored: malicious content is stored in the web server and executes when one assesses the web server
        * harder but reliable
    * reflected: malicious script is included in a URL that user accesses
        * requires user to access URL
        * easier but unreliable

Homework 5: 20-25 hours

### Cross site scripting Protection
* input validation
    * verify user inputs do not contain valid script tags
* encoding data
    * encode data before displaying back to browser
    * adhere to encoding standard for JS/CSS/HTML languages
* protects against reflected XSS but not stored XSS
* how do we protect against stored XSS?
    * content security policy (CSP)
    * but first: we need to know about SOP(same origin policy)

### Document object model
* defines the structure of a page's HTML document
* can be accessed and modified by scripts such as JS

### Same origin policy
* prevents scripts from modifying DOMs without permissions
* allows a script to access and modify a DOM, if it has the same URI as the DOM
    * universal resource identifier (protocol, server address, port)
* origin of resource is based on the URI of the frame
    * frame is a part of the DOM
    * frames are to web broswers as processes are to OS

url - protocol, domain, resource address
uri - protocol, server address, port

### Content Security Policy (CSP)
* prevents loading of malicious code, even if the code is stored on the server
* creates a white-list policy of content that is allowed to load on a page
    * white-list blocked by default
    * the administrator must specify all exceptions
* specific CSP options for different HTML and JS elements