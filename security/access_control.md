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

## Descretionary Access Control (DAC)

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

HW2: ubuntu 16.04 LTS
22.04 sudo john --format=crypt mypasswd

### Limits of Basic Unix Access Control
* company has sensitive plans in dir:/project/plans
    * privileges should be:
        * rwx for users
        * rw for engineers group
        * no other permissions

### Granularity of Basic Unix Assess Control
* granularity engables programs to:
    * run with temporary privileges
        * passwd command allows modification of /etc/shadow
    * protect selected finctions with higher privileges
        * ping command needs root for ICMP messages and not others
* problems
    * enables
        * high chances of misconfiguration
        * leading to higher amount of software vulnerabilities
    * countered by open source nature


## Mandatory Access Control
* security adminsitrator controls granting of privileges
* multilevel security
    * every object has several levels of privileges
* different implementations provide different security features
    * bell-lapadula: confidentiality
    * biba: integrity
    * chinese wall: solves conflict of interest
* problems
    * rigid and inconvenient to use
    * significant bureaucratic overhead

Example: SELinux

### Bell-LaPadula Model
* confidentiality focus
* developed by US military
* properties
    * for security level, subject can 'read' lower levels but not upper levels
    * cannot write any ofther levels

### Biba Model
* integrity focus
* properties
    * for security level, subjects cannot read/write any other levels

### Chinese Wall Model
* conflicts of interest focus
* properties
    * for a security elvel, subject can 'read' lower levels but not upper levels
        * if allowed by conflict rules
    * cannot write any other levels

## Roles Based Access Control (RBAC)
* created to suit large organizational needs
* roles instead of groups
    * roles: collections of permissions
    * groups: collection of users
* types:
    * flat: no inheritance
    * hierarchical: roles can inherit permissions
* sessions
    * users may have multiple roles
    * one user can access various privileges

* strengths
    * flexible config
    * efficient to use in complex / large systems
    * can allows granular config when needed
* drawbacks
    * overkill for simple / smaller systems
    * bureaucratic overhead hgiher than DAC

    