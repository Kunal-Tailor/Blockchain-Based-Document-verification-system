# Blockchain-Based Document Verification System with IPFS

A decentralized web application built to securely store, verify, and manage documents using the Ethereum blockchain and IPFS (InterPlanetary File System).

## 🚀 Overview

This project provides a robust solution to combat document forgery by leveraging blockchain technology. Verified institutions (Exporters) can upload documents to IPFS, generating a unique cryptographic hash that is then stored on the Ethereum blockchain. Anyone can independently verify the authenticity of a document by checking its hash against the blockchain records.

## ✨ Features

- **Document Hashing & Storage**: Upload documents to IPFS (via Pinata) and store their metadata/hashes on the blockchain.
- **Verification System**: Instantly verify documents by dragging and dropping them or searching by their unique hash.
- **Exporter Management**: The contract owner (Admin) can add, alter, or remove authorized Exporters (e.g., Universities, Organizations).
- **Role-Based Access**:
  - **Admin**: Manages the list of authorized exporters.
  - **Exporter**: Authorized addresses that can upload and delete their issued document hashes.
  - **Public/Viewer**: Anyone can use the platform to verify the authenticity of a certificate.
- **Web3 Integration**: Connects with MetaMask for authentication and signing transactions on the network (configured for Sepolia Testnet/Polygon).

## 🛠 Tech Stack

- **Frontend**: HTML5, CSS3, JavaScript
- **Blockchain**: Solidity (Smart Contracts), Ethereum/Polygon Networks
- **Storage**: IPFS (InterPlanetary File System) via Pinata API
- **Libraries/Tools**: 
  - [Web3.js](https://web3js.readthedocs.io/) - Ethereum JavaScript API
  - [Bootstrap](https://getbootstrap.com/) - Frontend Styling

## 📂 Project Structure

- `Contract/Verfication.sol`: The core Solidity smart contract handling logic for Exporters and Document Hashes.
- `index.html` / `verify.html`: Public pages to verify a document's authenticity.
- `admin.html`: Dashboard for the contract owner to manage Exporter addresses.
- `upload.html`: Dashboard for authorized Exporters to hash and upload documents.
- `delete.html`: Page for Exporters to revoke/delete documents they previously uploaded.
- `js/App.js`: Core blockchain interaction logic, connecting MetaMask and Web3.
- `assets/`, `css/`, `files/`: Static design and image assets.

## ⚙️ Prerequisites

1. **MetaMask Extension**: Install [MetaMask](https://metamask.io/) in your browser to interact with the DApp.
2. **Setup Network**: Switch your MetaMask wallet to the appropriate network (e.g., Sepolia Testnet) where the contract is deployed.
3. **Test ETH**: You will need test ETH to pay for transaction gas fees if you are an Admin or Exporter.

## 🚀 How to Run Locally

1. Clone this repository or download the source code.
2. Serve the directory using a local web server to avoid CORS issues. For example, using Python:
   ```bash
   python3 -m http.server 8000
   ```
   Or using Node.js `http-server`:
   ```bash
   npx http-server
   ```
3. Open `http://localhost:8000` in your web browser.

## 📝 Smart Contract Details

The contract (`Verification.sol`) maintains mapping records of authorized Exporter addresses and document hashes.
- **Contract Owner**: Deploys the contract, retains exclusive rights to execute `add_Exporter`, `alter_Exporter`, and `delete_Exporter`.
- **Exporters**: Authorized entities who can call `addDocHash` and `deleteHash`.
- **Public Properties**: Variables like `count_Exporters` and `count_hashes` are publicly readable.

## 🛡 Security & Privacy

The actual files are stored on IPFS, while only the unique cryptographic hashes (`keccak256`) and IPFS CIDs are stored on the highly secure, immutable Ethereum blockchain. This prevents data tampering while keeping storage costs low.
