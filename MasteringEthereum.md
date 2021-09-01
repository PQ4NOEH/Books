## Info
+ [Reference Site](https://github.com/ethereumbook/ethereumbook)
+ **publication Year**. December 1st, 2018
+ Authors
  + [Andreas M. Antonopoulos](https://aantonop.com/)
  + [Gavin Wood](https://gavwood.com/)

## What is ethereum?
Distributed state machine that tracks the state transitions of a general-purpose data store. Can hold any data expressible as a key–value tuple.
It has memory that stores both code and data, and it uses the Ethereum blockchain to track how this memory changes over time.
Ethereum can load code into its state machine and run that code, storing the resulting state changes in its blockchain.

Two of the critical differences from most general-purpose computers are: 
1. State changes are governed by the rules of consensus  
2. State is distributed globally.

## Ethereum components
1. **P2P network**. Ethereum main network 30303 running a protocol called ÐΞVp2p.
2. **Concensus rules**. [The yellow paper](https://ethereum.github.io/yellowpaper/paper.pdf)
3. **Transactions**. Network messages that include (among other things) a sender, recipient, value, and data payload
4. **State machine**. EST are processed by the EVM. EVM is a stack-based virtual machine that executes byte code
5. **Data structures**. State is stored locally on each node as a database (usually Google’s LevelDB), which contains the transactions and system state in a serialized hashed data structure called a Merkle Patricia Tree.
6. **Consensus algorithm**. Nakamoto Consensus (PoW) but planning to move to casper (PoS)
7. **Economic security**. currently ETash but it might change in near future.
8. **Clients**. There are many implementations but the most prominent are: Go-ethereum and parity

## DApps
A web app built on top of open, decentralized, P2P infrastructures. It is compound out of:
1. Smart contracts on a blockchain (Mandatory)
2. Web frontend UI (Mandatory)
3. A P2P storage protocol and platform (optional)
4. A P2P messaging protocol and platform (optional)

## Ether
Ethereum's currency unit
Wei. The smallest unit possible, 1 ETH === 1,000,000,000,000,000,000 wei
Internally Ether is represented as an unsigned integer denominated in wei.

## Wallet
Software application that helps managing blockchain account

## Concepts
+ Whisper. P2P messaging service. [Ref](https://www.mycryptopedia.com/ethereum-whisper-a-detailed-guide/)
+ **Swarm** P2P storage network. [Ref](https://www.ethswarm.org/)
+ **Ether** Ethereum coin. 
+ **wei** 1 Ether is  1,000,000,000,000,000,000 wei
+ **Faucet** Where you are paid a minuscule amount of ETH with basic ad viewing and clicking.
+ **Gas** contract execution resources consumption max
+ **trapdoor functions** In cryptography mathematical functions easily inverted if you know some secret information.
+ **Hash function** Any function taht can map data of arbitrary size to data of fixed size
  + Accepts a pre-image/message/input data
  + outputs a hash
+ **Cryptographic hash function** is a hash function with the following properties
  + one-way
  + Deterministic. A given input always produce the same hash
  + Verifiable. Computing the hash of a message is efficient
  + Noncorrelation
  + Irreversibility. Computing the message from its hash is infeasible 
  + Collision protection. Two different messages produce the same hash
+ **ICAP** Inter exchange Client Address Protocol is an ethereum address encoding partly compatible with the International Bank Account Number (IBAN) encoding, offering a versatile, checksummed, and interoperable encoding for ethereum addresses

### Accounts
#### Externally owned account (EOA)
Those accounts that have a private key. Means access control over funds or contracts

#### Contract account
Has smart contract code. It is owned by the logic of its smart contract code
Contracts have addresses, just like EOAs. Contracts can also send and receive ether, just like EOAs. However, when a transaction destination is a contract address, it causes that contract to run in the EVM, using the transaction, and the transaction’s data, as its input. In addition to ether, transactions can contain data indicating which specific function in the contract to run and what parameters to pass to that function. In this way, transactions can call functions within contracts.
Because a contract account does not have a private key, it cannot initiate a transaction. Only EOAs can initiate transactions


## ropstein test withdrawall
    https://faucet.metamask.io/
    https://faucet.ropsten.be/
    https://faucet.dimensions.network/
    https://faucet.kyber.network/ (GitHub users only)
    https://ipfs.io/ipfs/QmVAwVKys271P5EQyEfVSxm7BJDKWt42A2gHvNmxLjZMps/
    http://faucet.bitfwd.xyz/

## Ethereum networks
+ Multiple networks ([Yellow paper](https://ethereum.github.io/yellowpaper/paper.pdf) implementation) that may or may no interoperate between them: Ethereum, Ethereum clasic, Ella, Expanse,...
+ Nodes types
  + Full main node: parity, Geth, ...
  + Development driven
    + Testnet node
    + Local private. ex [Ganache](https://www.trufflesuite.com/ganache)
    + Cloud based ethereum client. Example [Infura](https://infura.io/)
  + Remote client. Do not store a local copy of the blockchain or do any validation (Examples: metamask, Emerald wallet). They offer 
    + Create and broadcast transactions.
    + Offer an api such as web3.js
  + Light clients. 
    + Validate block headers 
    + Use Merkle proofs to validate the inclusion of transactions in the blockchain and determine their effects, giving them a similar level of security to a full node.
  

## wallet vs remote clients
1. Both offer transaction functionality.
2. The remote client also offer an api such as web3.js

## Cryptography
### refs
+ Discrete logarithm problem
+ Prime factorization
+ Elliptic curve cryptography

### Keys generation process
1. Find a secure source of entropy or randomness. Picking a number between 1 and $2^{256}$. This is usually achieved by feeding a large string into a 256-bit hash algorithm such as Keccak-256 or SHA-256
2. Generate public key from private. This is done applying the elliptic curve multiplication (K1 = k2 * G) to the private key:
   1. "K1" the public key
   2. "k2" the private key
   3. "*" special elliptic curve "multiplication"
   4. "G" constant point called the generator point.
3. Generate Ethereum address. 
   1. Apply Keccak-256 hash function to the public key
   2. Keep only the last 20 bytes of the hash and that is the ethereum address

### Ethereum address formats
+ Raw. Full hexadecimal Address (20 bytes)
+ ICAP. Ethereum standard format
  + Direct
  + Basic
  + Indirect
+ EIP-55






