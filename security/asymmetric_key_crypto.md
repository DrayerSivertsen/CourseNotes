# Asymmetric Key Cryptographic Systems

* motivation
    * key management is hard
        * increases vulnerability of symmetric key systems
* also know as public key systems
* public key: shared with public
* private key: withheld by memeber

### RSA
* rivest-shamir-aldmen algorithm, devleoped in 1977
* popularity used in encryption of online sessions and digital systems

### Diffie-Hellman
* enables users to securely create shared keys
    * used in groups where the private key needs to be shared
* uses discrete logarithms
* provides 'Forward Secrecy'
    * 'a' generates a session that produces secrets 'b', 'c', and 'd'
    * forward secrecy guarentees 'a' will not be compromised if 'b', 'c', or 'd' are compromised