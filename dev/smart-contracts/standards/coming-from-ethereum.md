---
description: A comparison on NEP-171 and ERC-721
---

# Coming from Ethereum

## NEP-171 Token Standard

This is the non-fungible token standard on NEAR. It was carefully designed with input from several experienced developers and creators, and includes native support for royalty payments.

### Introduction

> In the three years since [ERC-721](https://eips.ethereum.org/EIPS/eip-721) was ratified by the Ethereum community, Non-Fungible Tokens have proven themselves as an incredible new opportunity across a wide array of disciplines: collectibles, art, gaming, finance, virtual reality, real estate, and more.
>
>
>
> This standard builds off the lessons learned in this early experimentation, and pushes the possibilities further by harnessing unique attributes of the NEAR blockchain:
>
> * an asynchronous, sharded runtime, meaning that two contracts can be executed at the same time in different shards
> * a [storage staking](https://docs.near.org/docs/concepts/storage-staking) model that separates [gas](https://docs.near.org/docs/concepts/gas) fees from the storage demands of the network, enabling greater on-chain storage (see [Metadata](https://nomicon.io/Standards/Tokens/NonFungibleToken/Metadata) extension) and ultra-low transaction fees
>
> Read more [https://nomicon.io/Standards/Tokens/NonFungibleToken/Core#motivation](https://nomicon.io/Standards/Tokens/NonFungibleToken/Core#motivation)

The NEP-171 is about the equivalent of the ERC721. It's just a guideline to enabling other platforms to interoperate with assets, giving them confidence the [nft\_transfer](https://github.com/near/NEPs/blob/master/specs/Standards/NonFungibleToken/Core.md#nft-interface) and ownerhip verification.

Anytime you see the `nft_` in front of a function, this is help indexer identify what's going on. In Ethereum land, every contract indexes on its own chaos.

{% embed url="https://nomicon.io/Standards/Tokens/NonFungibleToken/Core" %}

### Royalties

We took it a step further and added a payouts system which gives marketplaces less excuses by giving the, easy access to royalty expectations.&#x20;

{% embed url="https://nomicon.io/Standards/Tokens/NonFungibleToken/Payout" %}
