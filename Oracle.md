# 🧙 Oracle 

The main function of the oracle is to gather information about *whitelisted* accounts. Currently, a user's eligibility is determined by *NFT* ownership, but other options are available. The only requirement is that the oracle should be able to determine which addresses are *whitelisted* and build a corresponding cryptographic aggregator. That aggragation is than published to the blockchain (*Merkle Root Hash*).

To prove that the address is part of *whitelisted* accounts, the user should gain access to the *Merkle Branch*. Currently, to obtain it, users can send a request to the oracle. But the full *Merkle Tree* can be published and stored at any resource provider or by users themselves, allowing anyone to generate proofs without relying on the oracle. 

Oracle source code: https://gitlab.com/distributed_lab/zk-reviews/oracle