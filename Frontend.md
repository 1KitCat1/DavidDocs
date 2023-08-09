# 💻Frontend

Frontend modules is responsible for message creation, interacting with user's cryptowallet (like MetaMask) and building proofs.

Flow:
- User enters a webpage and connect's a wallet;
- User creates a feedback message;
- Feedback message hash is signed by a cryptowallet;
- Frontend retrieves required *Merkle Branches* (by either calling an oracle, or retriving them from publicly available Merkle Tree);
- Frontend uses circuit compiled to `wasm` and previously gathered data to generate a zk-SNARK proof;
- Frontend provides an ability for user to publish message & proof from random address.