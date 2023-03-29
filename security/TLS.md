# Transport Layer Security

* an improvement of SSL (Secure Socket Layer)
* runs over TCP
* datagram TLS available for UDP
* implementations exist for connecting for HTTPS and other app layer protocols
* provides
    * integrity and auth using MACs
    * confidentiality using encryption


* TLS/SSL Versions
    * SSL 3.0 : several cracks available widely
    * TLS 1.0: BEAST vulnerability
    * TLS 1.1: fixes issues exploited by BEAST
    

## Tranport Layer Security Stack
* SSL handshake, SSL change cipher spec protocol, SSl alert protocol, HTTP
* SSL record protocol
* TCP 
* IP

### SSL Record Protocol
* TLS transmits payload as 'records'
    * records are compressed and encrypted
* record types
    * TLS handshake
    * HTTPS data
    * system events e.g. alerts (bad certificate, decryption error etc)
    * cipher switch specifications

LZS Compression - look into this!!!!

## TLS Handshake
* TLS creates a statefull connection
* handshake facilitates 'statefulness' by negotiating
    * TLS version
    * ciphers
        * RSA/DH for key exchange
        * AES/RC4 for bulk encryption
        * SHA-512 HMACs for integrity & auth
        * format: [SSL/TLS]_[key_excahnge]
    * certificates
    * preshared key
    * session ID


Steps for handshake
1. establish ciphers
2. exchange ciphers 
3. establish a session
4. data transmission


## Attack on TLS/SSL
* POODLE
    * padding oracle on downgrade legacy encryption
    * SSLv3 used as legacy fallback in windows server version
* BEAST/CRIME attacks
    * compromising IV and/or index registers
        * reverse engineer
* need
    * ability to inject and run scripts from some web location


## AEAS
* previously known as AEAD: auth encryption & assoc data
* provides a sequence for security
    * forst authenticate then encrypt
    * encrypt first and authenicate 
    * both at the same time

