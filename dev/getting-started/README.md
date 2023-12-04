# 🛠 Getting Started

### GraphQL Indexer

[All read-only graphQL](./#graphql-indexer) data generated from blockchain transactions happen here. It's how we know who ones what tokens with what royalties quickly.

### Rust Contracts

* [Main Repo](https://github.com/Mintbase/mb-contracts)
* [Market](https://github.com/Mintbase/mb-contracts/tree/main/mb-interop-market) with USDC listings
* [NEP171 NFT contract](https://github.com/Mintbase/mb-contracts/tree/main/mb-store), we call a store
* [Factory](https://github.com/Mintbase/mb-contracts/tree/main/mb-factory) to recreate stores (Mintbase has deployed over 1,400 on NEAR)
* [Audits](https://arweave.net/WvB-T\_sg6HbpG08NLutna0bw65hq4tkZZoUJzw4iRK4)

### MintbaseJS

[MintbaseJS](https://github.com/Mintbase/mintbase-js) is a library created to lower the barrier to entry for decentralized application development on the NEAR ecosystem and facilitate integrations with Mintbase systems.

All transitions made on Mintbase.xyz are done with MintbaseJS, mint, transfer, burn, buy, list...

Or use our boilerplate templates to deploy your own market in minutes.



### Quick Start

* [Add Wallet Connection To Your React App](add-wallet-connection-to-your-react-app.md)
* [Make Your First Contract Call (deployContract)](make-your-first-contract-call-deploycontract.md)
* [Upload Reference Material To Arweave and Mint](upload-reference-material-to-arweave-and-mint.md)
* [Get Blockchain Data (ownedTokens)](get-blockchain-data-ownedtokens.md)



### Modules

With our tools, **it is possible to cover all points of token blockchain app development.** For that, we focused on these 4 themes.\


### [@mintbase-js/sdk](./#mintbase-js-sdk)

Easily deploy a ready-to-use token contract from Mintbase and interact with it in a few lines of code. Curate your own market by listing, buying and selling on Mintbase markets with affiliate bonuses.&#x20;

### [**@mintbase-js/react**](./#mintbase-js-react)

Out-of-the-box wallet integration with our react wallet selector wrapper.

### [**@mintbase-js/storage**](../../mintbase-sdk-ref/packages/storage/)

Easily upload your source material to Arweave where it will be permanently stored to be used in minting.

### [@mintbase-js/data](../../mintbase-sdk-ref/packages/data/)

Get general [data from the blockchain in a few lines of code](../../mintbase-sdk-ref/packages/data/) or use our [GraphQl indexer](../read-data/mintbase-graph.md) to make your own custom queries.&#x20;



{% hint style="info" %}
Visit the documentation for each of the modules to find usage examples as well as descriptions of the available methods.
{% endhint %}

## Get an API Key

For most operations moving forward an API key will be required.

Register a [developer key here](https://www.mintbase.io/developer)

## [Use Case Examples](../examples/)

Get building fast with our pre-built examples.

Each one of these examples covers a use case we believe is strongly supported by our SDK.

Below you can find a dapp starting point that can be configured and deployed to your own github in 10 minutes.

* [Minter](https://github.com/Mintbase/templates/tree/main/minter)
* [Marketplace](https://github.com/Mintbase/templates/tree/main/marketplace)
* [Starter ( Simple Login )](https://github.com/Mintbase/templates/tree/main/starter)
* [AI Chat](https://github.com/Mintbase/templates/tree/main/ai-chat)
* [AI Minter](https://github.com/Mintbase/templates/tree/main/ai-minter)
* [Blog](https://github.com/Mintbase/templates/tree/main/blogchain)
* [Contract Deployer](https://github.com/Mintbase/templates/tree/main/contract-deployer)
* [NFT ](https://github.com/Mintbase/templates/tree/main/nft-stripe-checkout)[Stripe Checkout](https://github.com/Mintbase/templates/tree/main/nft-stripe-checkout)
* [Token Drop](https://github.com/Mintbase/templates/tree/main/simple-token-drop)

{% embed url="https://www.loom.com/share/bb449c7b09b644b692c0292315889288" %}

## Join Us and Build the Future

Have feedback or perhaps need a hand? **Reach out on our** [**Telegram**](https://t.me/mintdev) **public developer support channel where we are happy to help!**

Building something cool? **Consider** [**applying for a grant**](https://github.com/Mintbase/Grants-Program)**.**

## Open Source

Most of our repositories are open source with either the MIT License or the GPL-3.0 License.

Mintbase is a tool in the public domain, as such anyone can view and contribute to every aspect of the protocol.
