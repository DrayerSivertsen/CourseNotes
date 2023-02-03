# Authentication
"The process of verifying an identity claimed by or for a system entity"

## Factors
* something you know
  * password, pin, security
* something you possess
  * smart card, token generator
* something you are
  * fingerprints, iris scan, face recognition

Multifactor (2FA, 3FA) is the new norm
* prevents single point of failure

## Levels
* level 1 - no ID proofing, 1FA
* level 2 - ID proofing, 1FA
* level 3 - ID proofing, 2FA (password, token)
* level 4 - ID proofing, 2FA+ (password, token, iris scan)
To move from one level to another you need distinct methods of authentication

## Passwords
Most popular: cheap and easy
* password quality/strength
  * length
  * diversity of characters
  * non-dictionary words
* strength can be measured using entropy
  * entropy: bits taken to represent data item

### Entropy
User selected passwords:
* first character = 4 bits
* next 7 characters = 2 bits
* 9th-20th characters = 1.5 bit/char
* after 20th character = 1 bit/char

Randomly selected passwords:
H = log2 (b^l)
H = entropy
l = password length 
b = char in alphabet

Standard entropy should be 128 bits

Critical systems should be 256 bits

Short password with diverse characters is easier to guess than common words with long words!

### How to store passwords on a computer
Do not store passwords in plain text
Store them by hashing the password

Unix shadow storage - to store the hash hidden

Username is stored in plain text

Slow hash, NP hard computation
Fast hash, easier to guess

Password + Salt(random string) -> slow hashing function = hash

### What threats exist
wireshark, or other to package catch to reverse engineer the username and password

social engineering, trojan payload to take the password directly

DoS, prevent client from talking to server

replay/eavesdrop, catch the package and try to repass the package to the server

Host attack, offline password hosting

### Cracking passwords
* assume: attacker gets access to password file
* file can be brute-forced to crack the hash
  * 1 high-end GPU: 8.3x(10.9) passwords/sec (8 chars)

* rainbow table
  * large public dictionary of common words

### Password manager
* better to use local pwd managers
* cloud pwd managers are more vulnerable

advantage: ease of use
disadvantage: leak

## MACs
Message Authentication Codes
* provide integrity and authentication
* can be used independently

### MAC security
* integrity
  * if a message is manipulated in transit, MACs dont match
  * F(F, M) != F(K, M')

* authentication
  * the preshared key, K , provides authentication

## Digital signatures
* provides authenticity and integrity
* uses asymmetric encryption

* recall:
  * a member's public key is available for everyone in the group
  * a memebers private key is avaliable to only the member

### Digital certificates
* provides root of trust
* helps protect against spoofing/tampering
* relies on a central certification authority (CA)
  * verisign, comodo
* if CA is compromised, the entire trust chain is vulnerable


Digital Certificate Creation
1. Create public/private keys
2. prepares certificate with information about identity, public key, and the CA
3. submit certificate to CA
4. CA hashes certificate, signs it with CA private key, attaches signature to certificate
5. CA returns signed to the user

Digital Certificate Usage
1. request communication
2. user sends signed certificate to reciever
3. revicever (already has CA public key) creates hash of certificate, checks to see if the hash matches the CA signed part of the certificate
4. if equal, cert has not been tampered with and public key in certificate can be trusted
5. if not equal potentially spoofed or tampered

-----

## Secret questions
* information that's not easily available
  * ideally info that's never available
* problem: secret is relative
  * some secrets are easy to guess
  * some are easy to crack
  * other are forgotten in time
* history of exploits
  * sara palin's email account was hacked

### Matt Honan's hack chain
Using a persons general information - email, name to reset the password of an account

Then use that account to get access to others (email to get another)

## Biometrics

* examples
  * iris, fingerprint, hand geo
* advantages
  * no issue of remembrance
  * no issue of additional security equipment
* problems
  * expensive to implement
  * complex to accurately compute
    * most implementations have low accuracy
  * privacy issues
  * can't change

* reading and verification of biometrics
  * done by algorithms
  * riddled with errors / low accuracy
  * hard to replicate patterns everyday
    * dirty hands, teary eyes, finger not in the same angle

### Biometric: Accuracy tradeoffs
* higher match threshold (match rate > 65%)
  * higher security
  * higher false non-matches
    * users are frusterated
* lower match threshold (match rate < 60%)
  * lower security
  * higher false match
    * prevelance of unauthorized access

## Tokens
* RSA secureID
  * OTP in sync with servers
* smart cards
   * embedded crypto processor
* phones
  * SMS messages
* advantages: accurate than biometrics
* problems: can be lost, stolen, cracked

### Standalone Tokens
* how do standalone tokens produce numbers in sync with a service?
* same PRNG function and salt
  * OAUTH-HOTP
    * HMAC-based one time password
      * pseudorandom number generator
        * needs a unique salt
          * every user is assigned a unique salt
          * when a device is configured, it is set to the user's salt
* same timestamp
  * OAUTH-TOTP
    * timestamp when a user clicks on 'generate token' is used

### SMS Authentication
* debated about SMS being a factor in MFA
* SMS messages can be re-directed easily
  * VoIP, account redirect with mobile carrier

### Fast Identity ONline (FIDO) Alliance
* emerging MFA online standard
  * governs websites, web apps
  * supports multiple devices


### Challenge Response Protocol

### Needham-Schroeder Protocol
* same schroeder from 'Security Design Prinicples'
  * Michael Schroeder - WSU grad

### Kerberos Protocol
* motivation
  * credential storage on systems
    * cant store all credentials on all systems for a cloud app
* example: university accounts
* solution: single authentication server
* popular for network auth (e.g. Microsoft Active Directory)

Terminology
* authenication server (AS)
  * authenticates each user's database of all users/passwords
* ticket
  * credentials used to authenticate systems
* ticket-granting server (TGS)
  * validates TGTs and provides service tickets
* ticket granting ticket (TGT)
  * used to obtain a service ticket from TGS
* authenticator
  * verifies sender of ticket is same as entitiy included in ticket