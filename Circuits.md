# 🔗 Circuits

*zk-SNARKs* were chosen for zero knowledge proofs generation due to their low proof size, as proofs are published to the blockchain.
**DAVID** supports *Groth16* and *PLONK* schemes. Both those schemes requires trusted setup (pre-circuit in *Groth16* and universal in *PLONK*). 

Currently we are using computer randomness for this setup. As long as malicious adversary cannot obtain access to secret parameters used in setup, the system is considered secure. For production MPC (multiparty computation computation) is required for the security purposes (*Powers of Tau* ceremony). 

For *zk-SNARK* circuits engineering Go library **gnark** is used.

Problem definition for **ZKP**: given a *message* and a *Merkle root hash* (aggregation of the *whitelisted* users, the root hash is computed and published by the oracle) as ***public*** inputs; *message signature* (by the *whitelisted* user) and *Merkle branch* (can be obtained from the oracle) as private inputs. Generate proof that the message is signed by the *whitelisted* user.

**ZKP** Modules required:
- *ECDSA* signature verification over ***secp256k1***: used to verify that user indeed has access to *whitelisted* account without using private key directly;
- *Keccak256* hash function: used to obtain address from public key (public key itself is recovered from *message* and *signature*);
- *Poseidon* hash function: used to verify that the address is agregated in the Merkle Tree (which is build on Poseidon hash function);

Why *Poseidon* hash function was chosen for Merkle Tree?
- The *Poseidon* is a hash function designed for zero-knowledge proof systems like *zk-SNARKs*. The main advantage of the Poseidon hash is simplification in circuits building. By using this hash function (instead of something more popular like Keccak of SHA-256) we significantly reduce amount of constraints, proving key size and proof generation time.
