# Quick Start Guide

Get ParallelPay up and running in 5 minutes!

## 1. Installation (1 minute)

```bash
# Clone repository
git clone https://github.com/wildhash/monad-parallelstream.git
cd monad-parallelstream

# Install dependencies
npm install
```

## 2. Configuration (1 minute)

```bash
# Create environment file
cp .env.example .env

# Edit .env (use your favorite editor)
nano .env
```

Add your private key:
```bash
PRIVATE_KEY=0xyour_private_key_here
MONAD_RPC_URL=https://testnet.monad.xyz
```

⚠️ **Never commit your .env file!**

## 3. Compile Contracts (30 seconds)

```bash
npm run compile
```

You should see:
```
✓ Compiled ParallelPay
✓ Compiled X402Payment
```

## 4. Get Testnet Tokens (1 minute)

1. Get your address from private key
2. Visit: https://faucet.monad.xyz
3. Request testnet ETH
4. Wait for confirmation

## 5. Deploy (1 minute)

```bash
npm run deploy
```

Save the contract addresses shown in the output!

## 6. Test It! (30 seconds)

```bash
npm run stress-test
```

Watch 50 streams get created in parallel!

## 7. View Dashboard (30 seconds)

```bash
npm run dashboard
```

Open: http://localhost:3000

## What's Next?

### For Developers

- Check out [EXAMPLES.md](EXAMPLES.md) for code samples
- Read [ARCHITECTURE.md](ARCHITECTURE.md) to understand the design
- See [DEPLOYMENT.md](DEPLOYMENT.md) for advanced deployment

### For Users

- Explore the dashboard interface
- Try creating your own streams
- Monitor real-time payments

## Common First-Time Issues

### "Insufficient funds"
→ Get more testnet ETH from faucet

### "Cannot connect to network"
→ Check your RPC_URL in .env

### "Compilation failed"
→ Make sure you ran `npm install`

### Dashboard shows "not connected"
→ Run `npm run deploy` first to create deployment file

## Commands Cheat Sheet

```bash
# Development
npm run compile        # Compile contracts
npm run deploy         # Deploy to testnet
npm run stress-test    # Run stress test
npm run test-local     # Test locally
npm run dashboard      # Start dashboard

# Quick test
npm run compile && npm run test-local
```

## SDK Quick Example

```typescript
import { ethers } from 'ethers';
import { ParallelPaySDK } from './sdk/index.js';

// Connect
const provider = new ethers.JsonRpcProvider('https://testnet.monad.xyz');
const signer = new ethers.Wallet('0x...', provider);
const sdk = new ParallelPaySDK('CONTRACT_ADDRESS', signer);

// Create stream
const now = Math.floor(Date.now() / 1000);
await sdk.createStream(
  '0xRecipientAddress',
  now,              // start now
  now + 86400,      // end in 24 hours
  ethers.parseEther('1.0')  // 1 ETH
);
```

## Help & Support

- **README**: Main documentation
- **EXAMPLES**: Code examples
- **ARCHITECTURE**: Technical details
- **DEPLOYMENT**: Full deployment guide
- **GitHub Issues**: Report bugs

---

**Ready to build?** Check out the full documentation in [README.md](README.md)!
