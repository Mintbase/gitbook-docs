---
description: >-
  Mintbase is introducing a new marketplace contract that enables arbitrary
  accounts to collect the market fee when a token is sold with its registered
  referral id.
---

# New Marketplace

### Join the Referral Program

Referrals collect fees for tokens sold using their referral id. [Join the Referral Program](https://forms.gle/DyFRjrta76fFQp4T7).

### List a token

Listing a token to the marketplace requires two function calls. The first to reserve storage in the contract for the listing and other to authorize the marketplace to transfer the token once sold.

#### Storage deposit

The new market requires a 0.1N storage deposit per listing.

* **Method**: deposit\_storage
* **Receiver Id**: the market contract address
* **Arguments**: none
* **Deposit**: 0.1N
* **Gas**: 200000000000000 yoctoGas | 200 TGas

Transaction example: [https://testnet.nearblocks.io/txns/CRgUHgfPEHcUGFmD6YSxM88aWk8y2gRZrHa49nToUcMu#execution](https://testnet.nearblocks.io/txns/CRgUHgfPEHcUGFmD6YSxM88aWk8y2gRZrHa49nToUcMu#execution)

#### Authorize the market

* **Method**: nft\_approve
* **Receiver Id**: the token contract address
* **Arguments**:&#x20;
  * **account\_id**: the market contract address
  * **token\_id:** the token id
  * **msg**: a stringified object that contains price expressed in yoctoNEAR
    * e.g "{"price":"500000000000000000000000"}" ****&#x20;
* **Deposit**: 0.1N
* **Gas**: 200000000000000 yoctoGas | 200 TGas

Transaction example: [https://testnet.nearblocks.io/txns/EQaeWj4wC26Exvspq58vGeL54FBcvZLAkSG1Zi5XTdxj#execution](https://testnet.nearblocks.io/txns/EQaeWj4wC26Exvspq58vGeL54FBcvZLAkSG1Zi5XTdxj#execution)

### Buy a token

Once an `account` is registered for collecting fees ([see above](new-marketplace.md#join-the-referral-program)) it can start collecting market fees for being a referral.

#### Buy

* **Method**: buy
* **Receiver Id**: the market address
* **Arguments**:&#x20;
  * **nft\_contract\_id**: the token contract address
  * **token\_id:** the token id
  * **referrer\_id**: the account address that will collect the market fee
    * ⚠️ Note that the `referrer_id` has to be registered first by Mintbase ([see above](new-marketplace.md#join-the-referral-program))
* **Deposit**: the token listing price
* **Gas**: 200000000000000 yoctoGas | 200 TGas

Transaction example:

[https://testnet.nearblocks.io/txns/CQNaVQFRAcpT6nQif9jJAYiMoycRaymKCwaVqSQCduqd#execution](https://testnet.nearblocks.io/txns/CQNaVQFRAcpT6nQif9jJAYiMoycRaymKCwaVqSQCduqd#execution)

