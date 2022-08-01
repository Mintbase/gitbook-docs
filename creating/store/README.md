---
description: Your own smart contract
---

# Store

Mintbase users deployed over 1,239 of stores as of August 1 2022.

![](<../../.gitbook/assets/Screen Shot 2022-05-30 at 9.21.30 AM.png>)

### A Store is Your Own NFT Smart Contract

You can look at a store as your own decentralized API and your own dapp. Mintbase is removing itself one step away from what we know now as platform-controlled single shared contracts.&#x20;

We see large companies or collectives beginning to build off of this foundational idea eventually owning their own keys. It is not just for individual artists, but art collectives who want to manage their own artist onboarding like [Gambiarra DAO](https://www.mintbase.io/store/gambiarra.mintbase1.near?tab=nfts\&page=0), currently managing [over 192 artists / minters](https://www.mintbase.io/store/gambiarra.mintbase1.near?tab=minters\&page=0) and the goal is to support them in creating their own stand-alone site and markets.

### Reasoning

If you want to do ticketing for a large stadium, you would not use a shared contract like on Paras, SuperRare, OpenSea, or Rarible, you would want your own contract to track transactions and manage the upgrades. Most companies do not have the developers on staff to learn rust, write their own contracts, and deploy an indexer solution. We take the massive learning curve of blockchain out of the equation.

Let's look at the [NEARCON 2021 Mintbase store](https://www.mintbase.io/store/nearcon.mintbase1.near?tab=things\&page=0) as an example. For one event we minted VIP & [General Admission tickets](https://www.mintbase.io/thing/5LkXEkvDGeMzDSj3zMdgWBOi\_8hc1DQperGVmm5V2ds:nearcon.mintbase1.near), after-party auction events, the actual [auctioned paintings](https://www.mintbase.io/thing/\_aVrcDJrC9DJyFMKRiIdme2K-NczX3oYkBy8AVTm\_eA:nearcon.mintbase1.near) and redeemed bottles of wine, [burritos](https://www.mintbase.io/thing/waJxfli-d\_ZFTYQdCcdbZsL9Nmi8xkc4YRSTEmHMYC0:nearcon.mintbase1.near), [t-shirts](https://www.mintbase.io/thing/oaex7KvQqBAy3XeRxnoGWdaeBJjeOMEl7kxS\_ZNBbiU:nearcon.mintbase1.near), spray paint around Lisbon, all [trackable](https://nearblocks.io/address/nearcon.mintbase1.near#transaction) under one shared contract. Yes, we were able to [pack a house](https://www.youtube.com/watch?v=tAvDT77W-Lc\&t=2s) without using Eventbrite.

1. You and anyone else can track its own[ transparent immutable transactions](https://nearblocks.io/address/nearcon.mintbase1.near#transaction) on any explorer
2. You can [add your own minters](https://www.mintbase.io/store/nearcon.mintbase1.near?tab=minters\&page=0) to help manage the system
3. You have your own [redeeming mechanisms ](https://www.mintbase.io/activity?title=redeemer\&contractAddress=nearcon.mintbase1.near)
4. Eventually will have more control over your [own contract upgradability and security](https://blog.mintbase.io/mintbase-upgraded-544-nft-contracts-8e8bb2ecf40c)
5. Can build your own UI, market using [MintbaseJS](https://www.npmjs.com/package/mintbase) or get data using our [indexer](broken-reference).
6. Can directly [interact with your rust contract functions ](https://github.com/Mintbase/mintbase-core/tree/master/store/src)itself on chain&#x20;

See the latest stores being [deployed here ](https://www.mintbase.io/market?tab=listings\&orderby=newest\&page=0)

###
