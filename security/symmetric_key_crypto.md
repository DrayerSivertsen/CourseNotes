# Symmetric Key Crypto Systems
Two types: block and stream

## Electronic Codebook (ECB)
* no interdependece between blocks
* each block encrypted/decrypted separately
* individual blocks are treated as messages on their own

### ECB Drawbacks
* if there exists a pattern in plaintext, the cipher will retain that pattern

### Cipher Block Chaining
* encryption
    * output of block 'n' is XORded with cipher of block 'n-1' resulting in cipher block 'n'
    * first block uses initialization vector for XOR
        * IV: random nonce
    
* decryption
    * inverse of encryption

## RC4
* popular stream cipher
