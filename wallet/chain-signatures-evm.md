---
description: >-
  Send EVM transactions directly through Bitte wallet in a couple of lines of
  code
---

# ✍️ Chain Signatures (EVM)

Chain signatures enable NEAR to sign and execute transactions across multiple blockchains via an MPC (Multi-Party Computation) network. Fortunately, to implement this functionality in your DApp, you won't need to integrate MPC directly, as it's fully operational within Bitte Wallet. Once you've established a basic connection with the wallet, building an EVM transaction is straightforward. Simply redirect to the wallet URL with the `evmTx` parameter, and the wallet will handle the complexities of generating the EVM signature and sending the transaction.

> **Note:** This functionality currently only works for the NEAR testnet.



```typescript
import { BaseTx, setupAdapter } from "near-ca";

const accountId = "your-account.testnet";
const network = {
  networkId: "testnet",
  nodeUrl: "https://rpc.testnet.near.org",
};

const adapter = await setupAdapter({ accountId, network });

// Build your favourite transaction!
const baseTx: BaseTx = {
  to: "0xDEADBEEF00000000000000000000000000000000",
  value: 1n,
  chainId: 11_155_111,
  data: "0x",
};

// This will attach gas, fees and nonce to transaction.
const { transaction } = await adapter.createTxPayload(baseTx);

// Pass the serialized transaction to this url route.
const route = `https://wallet.bitte.ai/sign-evm?evmTx=${transaction}&callback_url=https://yourdappurl.xyz`;

// Redirect to our wallet URL with the transaction to be sent, once successful user will be redirected to callback_url

```



Check out NEAR-CA if you would like to implement MPC directly without using a wallet, or to take advantage of its various utilities for interfacing between NEAR and EVM.

{% embed url="https://www.npmjs.com/package/near-ca" %}
