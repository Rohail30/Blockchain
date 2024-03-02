# What is blockchain technology?

Blockchain is a shared, immutable ledger for recording transactions, tracking assets, and building trust.

## Blockchain Defined

Blockchain is a shared, immutable ledger that facilitates the process of recording transactions and tracking assets in a business network. An asset can be tangible (a house, car, cash, land) or intangible (intellectual property, patents, copyrights, branding). Virtually anything of value can be tracked and traded on a blockchain network, reducing risk and cutting costs for all involved.

# 4 Features of Blockchain

- Immutable
- Transparent
- Trustable
- Secure

## Structure of Blockchain:

- **Chain of Blocks**:
  - Blockchain is made up of blocks linked together in a chain. The first block of blockchain is called genisis and it starts with 0000 hash.
- **Block Components**:
  - **Relevant Data**: Each block stores important information, like transactions.
  - **Hash**: Every block has a unique code called a hash, like a digital fingerprint.
  - **Previous Block Hash**: Each block also includes the hash of the previous block. This links the blocks together, making it hard to change past data without anyone noticing.

## Smart Contracts: Legal Contracts

**Definition:** Smart contracts are self-executing contracts with the terms of the agreement directly written into code. They automatically execute and enforce the terms of the contract when predefined conditions are met.

### Ethereum:

- **Platform:** Ethereum is a blockchain platform that enables the creation and execution of smart contracts. It provides a decentralized environment for developers to build and deploy decentralized applications (DApps).

# Frontend and Backend of Blockchain

- **Frontend**: The part of blockchain that users interact with directly, such as applications or websites for making transactions and viewing data. 
  - Example: Blockchain Wallet Application

- **Backend**: The underlying infrastructure and protocols that power the blockchain network, including consensus mechanisms, data storage, and smart contract execution.
  - Example: Smart contracts

- **Ether.js**: links Web2 with Web3

# Nodes in Blockchain

In blockchain, a node refers to any device that participates in the network by maintaining a copy of the blockchain and validating transactions. Nodes can be run by individuals, organizations, or entities, and they play a crucial role in the decentralized nature of blockchain networks.

There are different types of nodes in a blockchain network:

1. **Full Nodes**: These nodes download and validate every transaction and block on the blockchain. They store a complete copy of the blockchain and participate in the consensus process, ensuring the integrity and security of the network.

2. **Lightweight Nodes**: Also known as SPV (Simplified Payment Verification) nodes, these nodes do not store the entire blockchain. Instead, they only download block headers and verify transactions relevant to them. Lightweight nodes rely on full nodes to provide them with accurate blockchain data.

3. **Mining Nodes**: These nodes are responsible for creating new blocks in the blockchain through the process of mining. They compete to solve complex mathematical puzzles and add new blocks to the blockchain in exchange for rewards, such as cryptocurrency.

4. **Validator Nodes**: In proof-of-stake (PoS) or other consensus mechanisms, validator nodes are responsible for validating transactions and proposing new blocks to be added to the blockchain. They are typically chosen based on their stake or other criteria.

Nodes communicate with each other to propagate transactions and blocks across the network, maintaining consensus and ensuring that all nodes have an up-to-date and consistent view of the blockchain. This decentralized network of nodes is what makes blockchain resistant to censorship, tampering, and single points of failure.

# Hashing

In blockchain, the SHA (Secure Hash Algorithm) hashing algorithm, like SHA-256 or SHA-3, is used to create unique cryptographic hashes for blocks of data. These hashes act as digital fingerprints, ensuring the authenticity and integrity of the data. They are crucial for verifying transactions and maintaining the security of the blockchain network.

# Web3

Web3 in blockchain refers to a decentralized internet powered by blockchain technology. It enables peer-to-peer interactions, trustless transactions, and decentralized applications (DApps). Web3 aims to democratize access to information and services, reducing reliance on central authorities. It is often associated with Ethereum and tools like Web3.js for building DApps and interacting with blockchain networks.
