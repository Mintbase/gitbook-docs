---
description: >-
  Mintbase is introducing a new marketplace contract that enables arbitrary
  accounts to collect the market fee when a token is sold with a registered
  referral id.
---

# Marketplace 2.0

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
* **Gas**: 200 TGas

```
near call <market-contract> deposit_storage '{}' --deposit 0.1 --accountId <your-account>h
```

#### Authorize the market

* **Method**: nft\_approve
* **Receiver Id**: the token contract address
* **Arguments**:&#x20;
  * **account\_id**: the market contract address
  * **token\_id:** the token id
  * **msg**: a stringified object that contains price expressed in yoctoNEAR
    * e.g "{"price":"500000000000000000000000"}" ****&#x20;
* **Deposit**: 1 yoctoNEAR
* **Gas**: 200 TGas

```
near call <nft-contract> nft_approve '{"account_id": <market-contract>, "token_id": <token-id>, "msg": "{\"price\":\"<amount-yocto>\"}"}' --depositYocto 1 --accountId <your-account>
```

### Buy a token

Once an `account` is registered for collecting fees ([see above](marketplace-2.0.md#join-the-referral-program)) it can start collecting market fees for being a referral.

#### Buy

* **Method**: buy
* **Receiver Id**: the market address
* **Arguments**:&#x20;
  * **nft\_contract\_id**: the token contract address
  * **token\_id:** the token id
  * **referrer\_id**: the account address that will collect the market fee
    * ⚠️ Note that the `referrer_id` has to be registered first by Mintbase ([see above](marketplace-2.0.md#join-the-referral-program))
* **Deposit**: the token listing price
* **Gas**: 200 TGas

```
near call <market-contract> buy '{"nft_contract_id": <nft-contract>, "token_id": <token-id>, "referrer_id": <referrer-id>}' --depositYocto <price-yocto> --accountId <your-account>
```

