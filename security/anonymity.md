# Anonymity
* state of being anonmous i.e. unidentified
* pros
    * privacy
    * tends to enhance freedom in the form of free speech
* cons
    * undermines authority
    * tends to promote acitivities considered illegal

* proponent
    * 'my affairs are no one's business, not even the govt
* opponent
    * 'monitoring protects the nation. Lawful citizen have no cause to be worried'
* case studies
    * PRISM: global surveillance program by the NSA
        * claimed co-op: Google, Microsoft, Facebook, Apple, Dropbox, Tahoo

* total anonymity
    * no use of IDs (usernames etc)
    * total anonymity impossible in modern computing systems
        * even with cutting edge ecnryption, you're vulnerable at end points
* reasonable anonymity
    * privacy focused services
        * email: protomail
        * browsing: tor
        * VPN: tor
        * messaging/video calling: signal, session
        * OS: tails
        
## Virtual Private Networks
* creates a tunnel within a network
    * devices connected to a VPN are treated as if on the VPN's network
    * encryption of traffic in VPNs is common but not a requirement

* VPNs work best for providing
    * stability to wireless connections
        * e.g. ping values are stabilized when using a VPN over wireless
    * functionality and licensure of VPN provider
    * theoretically, one can tunnel as many times as they want
    * practically, your tunnel limit depends on your ISP's bandwidth

* VPNs are not reliable for anonymity
    * using a VPN will safeguard from ISP's traffic monitoring
    * but the VPN is still monitoring your traffic
        * most VPN providers are subject to local laws
        * they will provide your traffic info to authorities with a warrant

## Tor
* 'The Onion Router' anonymity project
* free and open source (FOSS)
* provides anonymous communication over the internet
    * uses a routing protocol know as 'Onion Routing;
* makes it hard, not impossible to perform
    * network surveillance
    * traffic analysis
* uses a global overlay network of volunteer router relay nodes

* project's fiscal sponsors include Google, Cambridge, DARPA
* the good
    * protects human rights in tyrannical regimes
        * whistleblowers, activism, internet browsing freedom etc
* the bad
    * provides a platform to market illegal operations
        * drugs, black hat hackers, fraud, counterfeit, guns

### Onion Routing
* vulnerabilities
    * traffic timing analysis
        * monitoring the onion overlay network, leverage
            * traffic patterns
            * timing patterns
        * data itself is secure but source and destination IDs are not
    * exit nodes vulnerability
        * final node always decrypts info before delivering to recipient
        * compromised exit node is a serious issue

## Signal
* redphone and textsecure projects merged in 2014
* FOSS
* provides end to end encryption
    * text messaging
    * voice calling
* signal protocol
    * uses double ratchet algorithm for initial key sharing
        * triple diffie hellman for handshake
        * AES-256

### Signal Protocol
* vulnerabilities
    * theoretical
        * compromising one end in E2E encryption
    * practical
        * MAC bypass due to andriod/ios bug
        * DoS
        * third party code injection (XSS)

