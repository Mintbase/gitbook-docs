# What is a Mintbase Contract

## A Contract is Your Own NFT Smart Contract

You can look at a contract as your own decentralized API and your own dapp. Mintbase is removing itself one step away from what we know now as platform-controlled single shared contracts.&#x20;

{% hint style="info" %}
**Mintbase users deployed over 1475 contracts as of April 1 2023**
{% endhint %}

We see large companies or collectives beginning to build off of this foundational idea eventually owning their own keys. It is not just for individual artists, but art collectives who want to manage their own artist onboarding like [Gambiarra DAO](https://www.mintbase.xyz/contract/gambiarra.mintbase1.near/nfts/all/0), currently managing [over 192 artists/minters](https://www.mintbase.xyz/contract/gambiarra.mintbase1.near/minters/all/0) and the goal is to support them in creating their own stand-alone site and markets.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-11 at 15.41.png" alt=""><figcaption><p>A contract on Mintbase</p></figcaption></figure>

## Reasoning

If you want to do ticketing for a large stadium, you would not use a shared contract like on Paras, SuperRare, OpenSea, or Rarible, **you would want your own contract to track transactions and manage the upgrades.** Most companies do not have the developers on staff to learn rust, write their own contracts, and deploy an indexer solution. We take the massive learning curve of blockchain out of the equation.

Let's look at the [NEARCON 2021 Mintbase ](https://www.mintbase.xyz/contract/nearcon.mintbase1.near/nfts/all/0)contract as an example. For one event we minted VIP & [General Admission tickets](https://www.mintbase.xyz/meta/nearcon.mintbase1.near%3A9d4c81a4b81cf094f91906320c7cf300), after-party auction events, the actual [auctioned paintings](https://www.mintbase.xyz/meta/nearcon.mintbase1.near%3A1485d7d18ebafc41738fbf6f156158f4) and redeemed bottles of wine, [burritos](https://www.mintbase.xyz/meta/nearcon.mintbase1.near%3A740f7754ff28f39b07eba334190b6f46), [t-shirts](https://www.mintbase.xyz/meta/nearcon.mintbase1.near%3A1665aeccb02c8a73e14d19a124e866af), spray paint around Lisbon, all [trackable](https://nearblocks.io/address/nearcon.mintbase1.near#transaction) under one shared contract. Yes, we were able to [pack a house](https://www.youtube.com/watch?v=tAvDT77W-Lc\&t=2s) without using Eventbrite.

1. You and anyone else can track its own[ transparent immutable transactions](https://nearblocks.io/address/nearcon.mintbase1.near#transaction) on any explorer
2. You can [add your own minters](https://www.mintbase.xyz/contract/nearcon.mintbase1.near/minters/all/0) to help manage the system
3. You have your own [redeeming mechanisms ](https://www.mintbase.xyz/activity?title=redeemer\&contractAddress=nearcon.mintbase1.near)
4. Eventually will have more control over your [own contract upgradability and security](https://blog.mintbase.io/mintbase-upgraded-544-nft-contracts-8e8bb2ecf40c)
5. Can build your own UI, market using [MintbaseJS](https://www.npmjs.com/package/mintbase) or get data using our [indexer](broken-reference).
6. Can directly [interact with your rust contract functions ](https://github.com/Mintbase/mintbase-core/tree/master/store/src)itself on chain&#x20;

See the latest contracts being [deployed here ](https://www.mintbase.xyz/market/listings/newest/0)
