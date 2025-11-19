# 🔐 FHEVM Hardhat Professional Setup - Thread #4

Complete professional setup guide for developing on FHEVM (Fully Homomorphic Encryption Virtual Machine) with Hardhat.

![Hardhat](https://img.shields.io/badge/Hardhat-FFF04D?style=for-the-badge&logo=hardhat&logoColor=black)
![Solidity](https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Zama](https://img.shields.io/badge/Zama-8A2BE2?style=for-the-badge)

## 📚 About

This repository contains the complete code from **Thread #4** of my educational series on FHEVM/Zama, originally created in French for the Zama Creator Program.

🐦 **Twitter Thread:** [Thread #4 - Coming Soon]

### Complete Series:
- 🔗 [Thread #2: Classic EVM on Remix](https://x.com/PandaPopArtClub/status/1986487186842153111) (French)
- 🔗 [Thread #3: First FHEVM Contract on Remix](https://x.com/PandaPopArtClub/status/1988297986158318061) (French)
- 🔥 **Thread #4: Professional Hardhat Setup** (this repo)
- ⏳ Thread #5: Sepolia Deployment (coming soon)

## 🎯 What You'll Learn

This tutorial covers everything needed to set up a professional FHEVM development environment:

✅ **Development Environment Setup**
- VS Code installation and configuration
- Node.js v18+ and Git installation
- Terminal configuration

✅ **Hardhat FHEVM Configuration**
- Clone official Zama template (113 files)
- Install 770+ npm packages
- Configure Sepolia testnet

✅ **Smart Contract Development**
- Compile FHECounter.sol
- Understand encrypted operations (euint32, FHE.add, FHE.sub)
- Work with encrypted handles

✅ **Testing & Validation**
- Automated TypeScript tests
- Mock FHEVM local testing
- Complete encryption/decryption workflow
- Homomorphic operations (add, sub)

## 🛠️ Prerequisites

Before starting, make sure you have:

- **Node.js v18+** ([nodejs.org](https://nodejs.org))
- **Git** ([git-scm.com](https://git-scm.com))
- **MetaMask** wallet with Sepolia ETH (0.05+ recommended)
- **VS Code** (recommended) or any code editor

### Get Sepolia ETH (Free Testnet Tokens)

You can get free Sepolia ETH from these faucets:
- [Alchemy Sepolia Faucet](https://sepoliafaucet.com/)
- [Infura Sepolia Faucet](https://www.infura.io/faucet/sepolia)
- [QuickNode Sepolia Faucet](https://faucet.quicknode.com/ethereum/sepolia)

## 🚀 Quick Start
```bash
# 1. Clone this repository
git clone https://github.com/xavydev/fhevm-hardhat-thread4.git
cd fhevm-hardhat-thread4

# 2. Install dependencies (770+ packages)
npm install

# 3. Configure your environment
cp .env.example .env
# Edit .env with your private key and RPC URL

# 4. Compile the smart contract
npx hardhat compile

# 5. Run local tests
npx hardhat test
```

Expected output:
```
FHECounter
  ✔ encrypted count should be uninitialized after deployment
  ✔ increment the counter by 1 (134ms)
  ✔ decrement the counter by 1 (91ms)

FHECounterSepolia
This hardhat test suite can only run on Sepolia Testnet
  - increment the counter by 1

3 passing (312ms)
1 pending
```

## 📂 Project Structure
```
fhevm-hardhat-thread4/
├── contracts/              # Solidity smart contracts
│   └── FHECounter.sol     # FHEVM counter with encrypted operations
├── deploy/                # Deployment scripts
│   └── deploy.ts          # Automated deployment script
├── test/                  # Automated tests
│   ├── FHECounter.ts           # Local tests (mock FHEVM)
│   └── FHECounterSepolia.ts    # Sepolia tests (real network)
├── tasks/                 # Custom Hardhat tasks
│   ├── accounts.ts        # List accounts
│   └── FHECounter.ts      # Counter-specific tasks
├── hardhat.config.ts      # Hardhat configuration
├── .env                   # Environment variables (NOT INCLUDED)
├── .env.example           # Environment template
├── package.json           # npm dependencies
└── README.md              # This file
```

## 🔐 Environment Configuration

Create a `.env` file in the root directory:
```properties
# Sepolia RPC URL (free public node)
SEPOLIA_RPC_URL=https://ethereum-sepolia-rpc.publicnode.com

# Your MetaMask private key (KEEP THIS SECRET!)
PRIVATE_KEY=your_private_key_here
```

### 🔒 Security Best Practices

⚠️ **CRITICAL SECURITY WARNINGS:**

❌ **NEVER** commit your `.env` file to Git
❌ **NEVER** share your private key publicly
❌ **NEVER** use your main wallet - create a dedicated test wallet
✅ **ALWAYS** use a test wallet with minimal funds
✅ **ALWAYS** verify `.env` is in `.gitignore`
✅ **ALWAYS** use environment variables for sensitive data

### How to Get Your Private Key

1. Open MetaMask
2. Click the 3 dots → Account details
3. Click "Show private key"
4. Enter your MetaMask password
5. Copy the private key (starts with 0x...)
6. Paste it in your `.env` file

## 🧪 Testing

### Local Tests (Mock FHEVM)

Run tests on a local Hardhat network with FHEVM mock:
```bash
npx hardhat test
```

**What these tests validate:**
- ✅ Initial state (uninitialized encrypted handle)
- ✅ Complete workflow: Encrypt → Add → Decrypt
- ✅ Homomorphic subtraction: Add → Subtract → Verify

### Sepolia Tests (Real Network)

After deploying to Sepolia (Thread #5):
```bash
npx hardhat test --network sepolia
```

This will run the complete integration test on the real Sepolia testnet.

## 📖 Understanding FHEVM

### What is FHEVM?

FHEVM (Fully Homomorphic Encryption Virtual Machine) is a blockchain technology that allows:
- **Encrypted computation**: Perform operations on encrypted data
- **Privacy preservation**: Keep sensitive data private on-chain
- **Smart contract confidentiality**: Build truly private dApps

### Key Concepts

**Encrypted Types:**
- `euint32`: Encrypted 32-bit unsigned integer
- `ebool`: Encrypted boolean
- `eaddress`: Encrypted address

**Homomorphic Operations:**
- `FHE.add(a, b)`: Add two encrypted values
- `FHE.sub(a, b)`: Subtract encrypted values
- `FHE.mul(a, b)`: Multiply encrypted values

**Handles:**
- Encrypted values are stored as "handles" (pointers to ciphertexts)
- Format: `bytes32` (e.g., `0x7f3a...`)
- Before any operation: `0x00...00` (uninitialized)

## 🔧 Available Commands

### Compilation
```bash
# Compile smart contracts
npx hardhat compile

# Clean artifacts and recompile
npx hardhat clean && npx hardhat compile
```

### Testing
```bash
# Run all tests
npx hardhat test

# Run specific test file
npx hardhat test test/FHECounter.ts

# Run with gas reporting
REPORT_GAS=true npx hardhat test
```

### Deployment (Thread #5)
```bash
# Deploy to Sepolia
npx hardhat deploy --network sepolia

# Verify contract on Etherscan
npx hardhat verify --network sepolia DEPLOYED_CONTRACT_ADDRESS
```

### Custom Tasks (Thread #5)
```bash
# View deployed contract address
npx hardhat task:address --network sepolia

# Increment counter with encrypted value
npx hardhat task:increment --value 10 --network sepolia

# Decrement counter
npx hardhat task:decrement --value 5 --network sepolia

# Decrypt and view counter
npx hardhat task:decrypt-count --network sepolia
```

## 🎓 Educational Thread Series

This repository is part of a complete educational series on FHEVM development:

### Thread #2: Classic EVM Basics
Learn blockchain fundamentals with a transparent counter on Remix IDE.

### Thread #3: First FHEVM Contract
Discover encrypted smart contracts with a simple FHEVM counter on Remix.

### Thread #4: Professional Setup (This Repo)
Set up a complete Hardhat development environment for FHEVM.

### Thread #5: Deployment & Workflow (Coming Soon)
Deploy to Sepolia testnet and interact with encrypted operations:
- Deploy FHECounter to Sepolia
- Increment with arbitrary values (10, 21, 100...)
- Decrypt and verify results
- Verify on Etherscan

## 📚 Resources

### Official Documentation
- 🔗 [Zama FHEVM Docs](https://docs.zama.ai/fhevm)
- 🔗 [Hardhat Official Template](https://github.com/zama-ai/fhevm-hardhat-template)
- 🔗 [Zama Creator Program](https://www.zama.ai/creator-program)

### Community
- 💬 [Zama Discord](https://discord.gg/zama)
- 🐦 [Zama Twitter](https://twitter.com/zama_fhe)
- 📝 [Zama Blog](https://www.zama.ai/blog)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

Feel free to:
- Open an issue for bugs or questions
- Submit a pull request for improvements
- Star the repository if it helped you

## 👤 Author

[@PandaPopArtClub](https://twitter.com/PandaPopArtClub)

Zama Creator Program participant creating educational FHEVM content in French 🇫🇷

## 📄 License

This project is based on the official Zama template.

See [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- [Zama](https://www.zama.ai/) for the FHEVM technology and template
- The Zama community for support and feedback
- All contributors to the FHEVM ecosystem

## 🌟 Support

If this tutorial helped you:

⭐ **Star this repository**  
🐦 **Follow** [@PandaPopArtClub](https://twitter.com/PandaPopArtClub) for more FHEVM tutorials  
🔖 **Bookmark** for future reference  

---

**Built with ❤️ for the FHEVM community**

*Part of the [Zama Creator Program]*

