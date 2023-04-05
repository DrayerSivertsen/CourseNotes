# Cryptocurrency and Blockchain

## Older cryptocurrencies
* currencies derived from cryptographic ledgers but not blockchains
* numerous currencies
    * digicash, lucre, magicmoney
        * double spending problem
            * decentralized: copy definition fiesl multiple times and becomes rich
            * centralized: parialism, favortism
        * solution: P2P ledgers
            * implementation of P2P ledgers differ by currency


## Modern Cryptocurrencies
* decentralized i.e. no central authority
* hard to regulate i.e. no/minimal oversight
* popular for
    * anti-fiat hedge
    * money laundering
    * market manipulation
    * financial terrorism
    * darknet transactions
        * illegal activities

## Bitcoin Blockchain
* blockchain: distributed ledger of blocks
* each peer involved in the chain is called a 'node'
    * each node stores a copy of blockchain
* blocks
    * set of transactions over a predefined period/space
    * computed using merkle trees
    * includes every transaction ever made
        * bitcoin blockchain is 434GB as of 10/26/2022
            number of blocks: 760,414

### Merkle Trees
* tree of hashes
* all transactions in a block hashed into a single digest
* modular
    * can compute sections of tree as transctions are populated
* verifications of transactions can be done by checking the hashes

* bitcoin enables distributed consensus
    * byzantine fault tolerant
* blockchain integrity is continuously verified by 'miners'
* transactions
    * each is broadcasted to all peers
    * signed by owner's private key
    * need to be verified by all peer before becoming a part of blockchain

* a bitcoin (BTC) is a random number
    * created by 'miners' after completing Nakamoto consensus
* ownership tracking
    * ledgers map coins to an address
        * address is owner's public key
    * transacting requires owner to sign with private key
    * lost private key? lost al your coins
* signing
    * SHA-2 hashes
    * elliptic curve digital signature algorithm

## Mining
* verifying integity of a blockchain
* computation takes effort
    * incentivizes miners
        * first miner to find an acceptable hash gets some new coins
            * 6.25 BTC reward per block
                * 21 million total supply
                    * currently at 18.86 M
                        * reaches cap by 2040
        * acceptability: 'proof-of-work'
            * nakamoto consensus

* proof of work
    * makes tampering hard
    * non-deterministic
        * fastest miner doesn't always win
    * one CPU = one vote. majority always win
    * miners pick random nonce
        * if yes, win coins -> target change
        * if no, try again with a diff nonce
            * 260 million total hash rate
* mining pools
    * probability of a sole miner winning = 0
    * miner join in pool
        * pool win a prize, everybody split depending upon compute effort