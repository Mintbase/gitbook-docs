---
description: >-
  Integrating Mintbase Wallet into your applications is straightforward. Follow
  the steps below to get started:
---

# Integrating Mintbase Wallet

{% embed url="https://youtu.be/2TxaqILs7Jg?si=7yQzCfFCFv8LsEyw" %}

This is the [Mintbase Wallet](https://wallet.mintbase.xyz/) package for NEAR Wallet Selector.

The easiest way to use this package is to install it from the NPM registry, this package requires `near-api-js` v1.0.0 or above:

```
# Using Yarn
yarn add near-api-js

# Using NPM.
npm install near-api-js
```

```
# Using Yarn
yarn add @near-wallet-selector/mintbase-wallet

# Using NPM.
npm install @near-wallet-selector/mintbase-wallet
```

Then use it in your dApp:

```
import { setupWalletSelector } from "@near-wallet-selector/core";
import { setupMintbaseWallet } from "@near-wallet-selector/mintbase-wallet";

const mintbaseWallet =  setupMintbaseWallet({
  networkId: 'mainnet',
  walletUrl: 'https://wallet.mintbase.xyz',
  callbackUrl: 'https://www.mywebsite.com',
  deprecated: false,
});

const selector = await setupWalletSelector({
  network: "testnet",
  modules: [mintbaseWallet],
});
```

### Options

* `networkId`: (`string?`): 'mainnet' or 'testnet' . Defaults to `mainnet`.
* `deprecated`: (`boolean?`): Deprecated is optional. Default is `false`.
* `callbackUrl`: (`string?`): Valid url to send your user after txn.
* `walletUrl`: (`string?`): wallet url: [https://wallet.mintbase.xyz](https://wallet.mintbase.xyz/) for mainnet and [https://testnet.wallet.mintbase.xyz](https://testnet.wallet.mintbase.xyz/) for testnet.

### License

This repository is distributed under the terms of both the MIT license and the Apache License (Version 2.0).
