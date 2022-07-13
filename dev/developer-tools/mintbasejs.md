# 🔧 MintbaseJS

Mintbase uses [MintbaseJS](https://www.npmjs.com/package/mintbase) for all of our transactions on both the market and minter including mint, transfer, burn, sell, buy, so if we can use it, so can you.

The best documentation to go off of is the[ typescript docs](https://mintbase.github.io/mintbase-js/classes/wallet.Wallet.html) as this library will change rapidly. If something is broken please make sure you have the latest and run see if the type are matching. Please create issue on Github to help us make it better.





[![Licence](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/Mintbase/mintbase-js/blob/main/LICENSE) [![npm version](https://img.shields.io/npm/v/mintbase.svg?style=flat)](https://www.npmjs.com/package/mintbase) ![example workflow](https://github.com/Mintbase/mintbase-js/actions/workflows/ci.yml/badge.svg)

## ⚠️⚠️ In active development  ⚠️⚠️

This package is under active development. Expect breaking changes often.

### Mintbase API

General purpose Mintbase API for interacting with NEAR, Arweave and other supported blockchains and decentralized file storage systems.

[See the types documentation](https://mintbase.github.io/mintbase-js/index.html)

### Table of Contents

* Mintbase API
* Table of Contents
* Install
* Getting Started
* Support
* Examples
* License

### Install

```
$ npm install mintbase
```

### Getting started

Initializing and Connecting Mintbase Wallet

* Acquire an API key in the `Developer` tab on [Mintbase](https://mintbase.io/developer)

```typescript
import { Wallet, Chain, Network } from 'mintbase'

// Connect and fetch details
async function connect() {
  const { data: walletData, error } = await new Wallet().init({
    networkName: Network.testnet,
    chain: Chain.near,
    apiKey: API_KEY,
  })

  const { wallet, isConnected } = walletData

  if (isConnected) {
    const { data: details } = await wallet.details()

    /*
      accountId: "qwerty.testnet"
      allowance: "0.25"
      balance: "365.77"
      contractName: "mintbase13.testnet"
    */
  }
}

connect()
```

Here's an example of a button to connect to the wallet.

```
<Button onClick={() => wallet.connect({ requestSignIn: true })}>Login</Button>
```

### Examples

Bootstrap your app with [Create Mintbase App (React + Typescript)](https://github.com/Mintbase/create-mintbase-app)

### Support

Open an [issue](https://t.me/mintdev)!

or ask in our [developer telegram](https://github.com/Mintbase/mintbase-js/issues/new)

### License

[MIT](https://github.com/Mintbase/mintbase-js/blob/main/LICENSE)
