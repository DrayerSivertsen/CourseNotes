# Cryptography Basics

Protects forward aspects of security
* confidentiality
* integrity
* authenticity (verifies provenance - came from where you say)
* authentication (verifies identity - who you claim to be)

Plain text: text that you can understand
Cypher text: text that you 'may' understand but will not have the correct meaning

Substitution cypher: changes english characters to different characters (alphabet -> alphabet)
Ex. english alphabet to latin alphabet

Multiple computations

Encryption
plain text -> cypher text 

Decryption
cypher text -> plain text

Brute force: trying every possible combination of decryption
Crypt analysis: analyize patterns to try and reverse engineer the encryption
Bribery: socially getting the person who sent the message to give up the encryption algorithm

AES: 10 rounds of computation that plain text goes for to become the cypher text result

## Symmetric algorithms
One secret key that is shared for both the encyption and decrpytion
* encryption and decrytion performed by a shared key
* sender and receiver have a copy of the key
* vulnerability increases with people involved

Definitions
- X - plain text
- Y - cipher text
- K - key
- E - encryption algorithm
- D - decryption algorithm

ciphers can be divided into two types block and stream

Advantages:
* fast and efficient
* provides confidentiality and authenticity

Disadvantage:
* key sharing, key management


Cipher in blocks
* breaks text into blocks, processes each block
* mode of operation defines how blocks fit together
* examples: AES, DES, 3DES

Cipering in streams
* encrypts text as a continuous stream
* XOR cipher key with plain text
* examples: RC4, Salsa20

## Asymmetric algorithms
AKA public-key encryption
Encryption and decryption perfomred by separate keys
* public key
* private key
Algorithms used are mathematically 'hard' i.e. computationally intense
Mathematically hard is:
* 2 large prim number factorization
* descrete log (exp)
Public key ring (PKR), sharing of public key

Added definitions
- PU - public key (provided to the public)
- PR - private key (kept private)

Broadcasting variant: messages are designed and prepared to be sent out to many people and decrypted by many. You can identify the sender by which public key works to decrypt.
Provides a digital signature of sender

Secrecy or confidentiality variant: used for private key holder to get messages from anyone with the public key. Messages can only be decrypted with the private key.

Advantages:
* easier key management
* can provide digital signatures

Disadvantages:
* slower and computationally heavier than symmetric


## Hashing
one way encryption, once encrypted it cannot be undone
* takes any number of data items
* creates a unique digest called hash
* examples: SHA, MD5
Allows digital signatures and digital certificates
Will create a fixed hash digest regardless of input

sha1 = sha128 bits in length

The hash output will always be a 128 bit hash, regardless if a novel is input, or a sentence. 

h1 != h2

Used for:
* digital signatures
* HMACS
* password storage
Provides integrity and authentication

Advantages:
* can turn 3 GB of data into a 3 KB digest

Disadvantage:
* one way process

Homework:
#4 data store is incorrect, watch video for resolution
