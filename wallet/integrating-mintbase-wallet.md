---
description: >-
  Integrating Mintbase Wallet into your applications is straightforward. Follow
  the steps below to get started:
---

# ⚙️ Integrating Mintbase Wallet

{% embed url="https://youtu.be/2TxaqILs7Jg" %}

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

## Mintbase Wallet Integration via URL Schemes

This guide explains how to interact with the Mintbase Wallet using URL schemes to perform operations like connecting or creating an account and signing transactions. Depending on your development environment, you can choose between the testnet and mainnet URLs.

### Base URLs

| Base URL                                                                   | Network |
| -------------------------------------------------------------------------- | ------- |
| [https://testnet.wallet.mintbase.xyz](https://testnet.wallet.mintbase.xyz) | testnet |
| [https://wallet.mintbase.xyz](https://wallet.mintbase.xyz)                 | mainnet |

### Connect or Create an Account

To connect or create an account, use the following endpoint. This action will redirect users to authenticate or create a new wallet account

* **Endpoint**: `/connect`
* **URL**: `https://wallet.mintbase.xyz/connect`

#### Parameters

*   `success_url`:&#x20;

    The URL to which the wallet redirects after a successful login. It should be able to handle the incoming parameters.

    * Example: your\_schema://\`

**Callback URL**

The callback URL is defined in the `success_url` parameter. After successful authentication, the user will be redirected to this URL.

**Parameters**

* `account_id`: The authenticated user's account ID.
* `public_key`: The currently connected public key of the user's account.&#x20;

### Sign Transactions

To sign a transaction, direct the user to the sign transaction endpoint.

* **Endpoint**: `/sign-transaction`
* **URL**: `https://wallet.mintbase.xyz/sign-transaction`

**Parameters**

* **transactions\_data**: The encoded data for the transaction that needs to be signed. See [this](https://github.com/near/wallet-selector/blob/main/packages/core/docs/api/transactions.md) to learn how to format the transaction object. The transaction object should be URL encoded (\`encodeURI(JSON.strinfigy(tx\_data))\`)&#x20;
* **callback\_url**: The URL to redirect after the transaction signing process.

**Callback URL**

After signing the transaction, the wallet will redirect to the provided `callback_url` with additional transaction details.

**Parameters**:

* `transactionHashes`: The hashes of the signed transactions.

### Examples

#### 1. **Connect Account on Mainnet**

```
https://wallet.mintbase.xyz/connect?success_url=https://mintbase.xyz
```

#### 2. **Sign Transaction on Mainnet**

```
https://wallet.mintbase.xyz/sign-transaction?transactions_data=%5B%7B%22receiverId%22%3A%220.drop.proxy.mintbase.near%22%2C%22actions%22%3A%5B%7B%22type%22%3A%22FunctionCall%22%2C%22params%22%3A%7B%22methodName%22%3A%22mint%22%2C%22args%22%3A%7B%22metadata%22%3A%22%7B%5C%22media%5C%22%3A%5C%22C6iWEOxKqUHJ2eAr5_3i0jyiYPLCcpUdoxRvM38xViM%5C%22%2C%5C%22creatorAddress%5C%22%3A%5C%22aurora-ahghara.near%5C%22%2C%5C%22title%5C%22%3A%5C%22%5C%22%2C%5C%22description%5C%22%3A%5C%22%5C%22%7D%22%2C%22nft_contract_id%22%3A%22drops.mintbase1.near%22%7D%2C%22gas%22%3A%22200000000000000%22%2C%22deposit%22%3A%2213500000000000000000000%22%7D%7D%5D%7D%5D&callback_url=https://mintbase.xyz
```
