# Consensus Algorithms in Blockchain
Consensus, in a general sense, refers to a collective agreement or decision-making process among a group of participants. In the context of blockchain technology, consensus is the mechanism by which all nodes in a decentralized network agree on the validity of transactions and the state of the distributed ledger. It ensures that all nodes reach an agreement on the order and content of transactions, even if some nodes are malicious or unreliable. Consensus algorithms enable the decentralized and trustless nature of blockchain systems by ensuring that no single entity has control over the network and that all participants can trust the integrity of the data stored on the blockchain.

## Consensus:
Consensus is the process by which all nodes (computers) in a blockchain network agree on the validity of transactions and the order in which they are added to the blockchain. It ensures that all copies of the blockchain across the network are synchronized and consistent. Consensus mechanisms are the protocols used to achieve this agreement among nodes.

1. **Proof of Work (PoW)**:
PoW is a consensus mechanism in which nodes (miners) compete to solve complex mathematical puzzles to validate transactions and create new blocks in the blockchain. The first miner to solve the puzzle earns the right to add the next block to the blockchain and receives a reward in the form of cryptocurrency. PoW requires significant computational power and energy consumption but is known for its security and resistance to attacks.

2. **Proof of Stake (PoS)**:
PoS is a consensus mechanism in which nodes are selected to validate transactions and create new blocks based on the amount of cryptocurrency they hold and are willing to "stake" as collateral. Validators are chosen randomly or based on factors like their stake size and the length of time they have held their coins. PoS is more energy-efficient than PoW but still ensures network security through economic incentives.

3. **Delegated Proof Of Stake (DPoS)**:
Delegated Proof of Stake (DPoS) is a consensus mechanism used in blockchain networks to achieve distributed consensus. It is a variation of the Proof of Stake (PoS) algorithm that aims to address some of its limitations, such as scalability and energy efficiency. In a DPoS system, token holders vote to elect a limited number of delegates who are responsible for validating transactions and creating new blocks on the blockchain. These delegates, also known as witnesses or validators, are entrusted with the task of securing the network and maintaining consensus.

4. **Practical Byzantine Fault Tolerance (PBFT)**:
PBFT is a consensus mechanism designed to achieve consensus in distributed systems, particularly in environments where Byzantine faults (malicious behavior) may occur. It requires a predetermined set of nodes (replicas) to reach a consensus on the validity of transactions through a multi-round voting process. PBFT is fault-tolerant and can withstand up to one-third of the nodes behaving maliciously or failing.

### Examples
1. **Proof of Work (PoW)**:
   - **Example**: Bitcoin
   - **Explanation**: Miners compete to solve complex puzzles to validate transactions and add blocks to the blockchain. The first to solve the puzzle earns the right to add the block.
  
2. **Proof of Stake (PoS)**:
   - **Example**: Ethereum 2.0 (Beacon Chain)
   - **Explanation**: Validators are chosen based on the amount of cryptocurrency they hold and are willing to stake. They validate transactions and create new blocks.

3. **Delegated Proof Of Stake (DPoS)**:
   - **Example**: EOS
   - **Explanation**: EOS is a blockchain platform that utilizes DPoS as its consensus mechanism. It allows token holders to vote for block producers who are responsible for validating transactions and securing the network.

4. **Practical Byzantine Fault Tolerance (PBFT)**:
   - **Example**: Hyperledger Fabric
   - **Explanation**: Transactions are endorsed, ordered, and validated by a subset of network participants before being added to the blockchain. PBFT ensures fast transaction finality and fault tolerance.
  
## Minting
Minting in blockchain is the process of creating new coins or tokens. It usually happens in proof-of-stake or proof-of-authority systems, where participants are rewarded with newly minted tokens for validating transactions or maintaining network integrity. It incentivizes participation and helps distribute new tokens in the network.


## Proof of Work(POW)
Proof of Work consensus is the mechanism of choice for the majority of cryptocurrencies currently in circulation. The algorithm is used to verify the transaction and create a new block in the blockchain. 

### Purpose of PoW
The purpose of a consensus mechanism is to bring all the nodes in agreement, that is, trust one another, in an environment where the nodes don’t trust each other. 
- All the transactions in the new block are then validated and the new block is then added to the blockchain. 
- The block will get added to the chain which has the longest block height(see blockchain forks to understand how multiple chains can exist at a point in time). 
- Miners(special computers on the network) perform computation work in solving a complex mathematical problem to add the block to the network, hence named, Proof-of-Work. 
- With time, the mathematical problem becomes more complex. 

### Features of PoW
There are mainly two features that have contributed to the wide popularity of this consensus protocol and they are:

- It is hard to find a solution to a mathematical problem.
- It is easy to verify the correctness of that solution.

## How Does PoW Work?

### Mining

The Proof of Work (PoW) consensus algorithm involves solving a computationally challenging puzzle to create new blocks in the blockchain, known as mining. Miners compete to solve these puzzles, and the winner is rewarded with new bitcoins and transaction fees.

### Energy and Time Consumption in Mining

Mining requires significant energy consumption, mainly in solving the mathematical puzzle to link new blocks to the existing blockchain. The time-consuming part is finding the right solution, which involves testing different nonce values until a suitable one is found.

### Mining Reward

Currently, miners receive 6.25 bitcoins for mining a block, with the reward halving approximately every four years. The network adjusts the difficulty level to maintain a steady block creation rate of one block every 10 minutes.

### Bitcoin’s PoW System
Bitcoin utilizes the Hashcash Proof of Work system as the basis for its mining process. The fundamental problem can be abstractly defined as follows:

```
Given data A, find a number x such that the hash of x appended to A results in a number less than B.
```

Miners collect a group of transactions and attempt to mine a new block. Mining involves solving a challenging mathematical problem known as the proof of work problem. This problem must be solved to demonstrate that the miner has performed work to find a valid solution. 

The solution to the problem must yield a hash of the block that is lower than the target hash for it to be accepted. This target hash is a predetermined value set by the network.


### Common Cryptographic Protocols Used in PoW

PoW algorithms are based on cryptographic protocols like SHA-256, Scrypt, SHA-3, etc., with SHA-256 being the most widely used in Bitcoin.

### Challenges With PoW

- **51% Risk:** If a single entity controls 51% or more of the network, it can manipulate the blockchain.
- **Time-consuming:** Finding the right solution requires testing numerous nonce values.
- **Resource Consumption:** Mining consumes significant computing power, leading to high energy consumption and resource waste.
- **Non-Instantaneous Transactions:** Transaction confirmation can take 10-60 minutes, making it less suitable for instant transactions.

# Proof of Stake (PoS) in Blockchain

Proof of Stake (PoS) is a consensus algorithm used in blockchains to achieve distributed consensus.

## Overview
In PoS, nodes on a network stake a certain amount of cryptocurrency to become candidates to validate new blocks and earn transaction fees. An algorithm selects a validator node from this pool of candidates based on factors such as stake quantity, coin-age based selection, and random block selection.
- **Coin-age based selection:** The algorithm tracks the time every validator candidate node stays a validator. The older the node becomes, the higher the chances of it becoming the new validator.
- **Random Block selection:** The validator is chosen with a combination of ‘lowest hash value’ and ‘highest stake’. The node having the best weighted-combination of these becomes the new validator.

### Typical PoS-Based Mechanism Workflow

1. **Transaction Submission:** Nodes on the network initiate transactions. These transactions are collected in a transaction pool.

2. **Stake Raising:** Nodes interested in becoming validators for the next block raise a stake. This stake, along with other factors like coin-age or randomized block selection, determines the validator selection process.

3. **Block Validation:** The selected validator verifies all transactions in the pool and constructs a new block. However, the validator's stake remains locked, and the forging reward is not granted yet.

4. **Block Approval:** The newly created block is broadcasted to other nodes on the network for validation. If the block is approved by the network (i.e., 'OK'-ed), the validator receives back their stake along with the forging reward. If a coin-age based mechanism is used, the validator's coin-age is reset to 0, lowering their priority for the next validator election.

5. **Block Rejection:** If the block fails to be verified by other nodes on the network, the validator loses their stake and is marked as 'bad' by the algorithm. The process returns to step 1 to initiate the forging of a new block.


### Features
- **Fixed Coins in Existence:** There is a finite number of coins in circulation, and new coins cannot be created through mining as in Proof of Work (PoW) systems.
- **Transaction Fee as Reward:** Validators receive transaction fees as a reward for minting new blocks, but if a block is found fraudulent, the validator loses both the transaction fees and their stake.
- **Impracticality of 51% Attack:** Conducting a 51% attack requires owning 51% of the total cryptocurrency in the network, making it expensive and unprofitable.

### Advantages
- **Energy Efficiency:** PoS consumes less energy compared to PoW, as nodes do not compete against each other to solve complex puzzles.
- **Decentralization:** Rewards in PoS are proportional to stake, discouraging centralization through mining pools.
- **Security:** Attacking the network requires owning a significant share of the cryptocurrency, making it expensive and less likely.

### Weaknesses
- **Large Stake Validators:** Groups of validators with significant stakes may dominate the network, leading to centralization.
- **New Technology:** PoS is still a relatively new concept, and ongoing research aims to address potential flaws.
- **'Nothing at Stake' Problem:** Nodes may support multiple blockchains in the event of a fork without facing significant disadvantages, hindering consensus.

### Blockchains Using PoS
- Ethereum (Casper update)
- Peercoin
- Nxt

#### Variants of PoS
- Regular Proof-of-Stake
- Delegated Proof-of-Stake
- Leased Proof-of-Stake
- Masternode Proof-of-Stake

