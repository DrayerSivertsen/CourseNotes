# Access Control
Definition: the prevention of unauthorized use of a resource, including the prevention of use of a resource in an unauthorized manner

* Authentication: determine identity
* Authorization: determine permissions
* Access control: methods to enforce authorization

Glossary:
* subject: person / program attempting to access objects
* object: file / service / function / device being accessed

### Access Control Approaches
* Descretionary access control
    * owners can provide other subjects with object permissions
    * e.g. unix/linux file permissions
* Mandatory access control
    * a security administrator can grant object permissions
    * e.g. SELinux, windows UAC
* Role-based access control
    * subjects have roles, permissions are allocated to roles instead
    * e.g. MS AD
* several approaches can be used together
    * not mutally exclusive

### Descretionary Access Control (DAC)

* object owner determines who has access
    * every object has at least one owner
* uses an access matrix to control rights
* problems:
    * users might incorrectly grant privileges
        * chmod 777 -R ./*
    * transitive privileges
        * if x gives y read rights, y can pass read rights to anyone else
* implementations
    * access control lists
    * unix access control

### Access Control Lists (ACL)
* each object has a list of identities that can have access

Confusion Deputy Problem
* tricking a program into misusing its privileges
* occurs when one program has bloated permissions
* frequently occurs with ACLs

### Basic Unix Access Control
* unix/linux file permissions are not ACLs
* every object has permissions as part of its node (index node)
    * users are classified into owner, group, and other
    * groups defined in /etc/groups
    * each user category has separate permissions read, write, execute
* strengths
    * easy to control per subject
    * granular access per object
    * no confused deputy problems
* problem
    * not very flexible
    * ease of use lower

