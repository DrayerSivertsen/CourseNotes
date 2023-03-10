# Crypto History

## Randomness
* used frequently in crypto
    * generates keys, nonces, canaries etc
* criteria
    * uniformity: random characters must be uniformly distributed
    * independence: each value should be statistically independent from others
    * unpredicability: random text shouldn't be predictable
* applications
    * encryption (TLS, public key, symmetric key, auth protocols)
    * salts
    * unbiased sequencing

# True Randomness
* TRNG: true random number generator
* based on truly random process, often based on physical processes
    * e.g. rolling a dice

# Pseudo Randomness
* true randomness is difficult to achieve
* PRNG: Pseudo random nuumber generator
    * based on a deterministic algorithm
    * salt values
* CSPRNG: cryptographically secure pseudo number generator

## PRNG in Linux
* linux PRNG: /dev/random and /dev/urandom
* entropy sources
    * translates system events to bits
    * add bits to entropy pool
        * primary secondary, and universal

## Intel Ivy Bridge: RdRand
* entropy obtained from thermal noise from the processor
* entropy processed by AES and MAC protocols
* resultant random number is sent to a destination register
* 20x slower than python CSPRNG
* used to be considered TRNG
* destination register can be compromised

## Failures of Randomness
* CVE-2008-0166
    * debian OpenSSL 2008 vulberability
    * caused by dev accidentally removing randomization code
* mining of keys by Heninger et al.
    * 5.8 million public keys collected and analyzed 
        * 5.57% of TLS hosts have same keys
        * could predict keys for 0.575% TLS hosts
            * amounts of 333.500 compromised keys

## One-time Pad Cipher
* cipher is a key that is used once and not more
    * encrypt: cipher = (message + key) mod 26
    * decrypt: cipher = (cipher - key) mod 26
    * key is a predetermined random value that's shared with trusted parties
        * key should be as long as the message at least
    * provides perfect secrecy if a truly random value is used for the key
        * cannot be cracked
    * key management is a problem
* commonly used throughout 20th century
    * US, USSR, Germany

## Substitution Cipher
* plain text substituted with cipher text using a key shift
* relatively weak due to smaller number of possible keys
* susceptible to cryptanalysis attacks due to standard patterns of ciphers
* Ceasar cipher is an example; used form 108 BCE to 879 CE

## Transposition Cipher
* cipher text is a permutation of the plain text
    * permutation: shuffling; is the key
* relatively weak due to a smaller number of possible keys
* susceptible to styptanalysis attacks due to availavility of plain text in cipher text
* cylinder cipher is a popular example; used by ancient Greeks
    * paper contains cipher that can be decrypted by using a stick of correct diameter

# Symmetric Key Cryptosystems
* block ciphers
    * break text into blocks, encrypt each block
    * key: random string of bits
    * examples: DES, 3DES, AES
* stream ciphers
    * encrypts text as continuous stream
    * keystream: random streams of data; one-time use
        * same length as plaintext
    * XOR plain with keystream to get cipher
    * XOR cipher with keystream to get plain

## Advanced Encryption Standard (AES)
* each round is a series of substitution, shifting, multiplication, adding round key
* round key is a derivation of the primary key
    * e.g. 128 bit key has 11 round keys
* computing round keys from primary key is called 'expanding the key'

## Security of AES
* avg. key length 128bits i.e. 2^128 possible keys
* assuming following:
    * modern GPU's avg procession power: 33,862,700 bits/s
    * assume 1000 operations per decryption
        * 3x10^17 years
* AES 128 may work for a lay person
* AES 256 may work for top secret national security info

## AES Modes of Operation
* the algorithm we saw is for one block
* how do we manage all the blocks?
* depends on modes of operations
    * defines
        * size of blocks
        * sequence of blocks
* AES modes of operation
    * electronic code block (ECB)
    * cipher block chaining (CBC)