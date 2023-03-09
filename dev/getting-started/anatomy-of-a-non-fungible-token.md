---
description: Understanding the components that make NFTs work
---

# 🔬 Anatomy of a Non-Fungible Token

When using Mintbase it's helpful to understand the parts that make up an NFT. If you're already familiar with how NFTs work and are structured, you can [skip ahead and start coding](add-wallet-connection-to-your-react-app.md).

When you see an NFT on a marketplace or in your wallet, it's easy to draw the conclusion the creative representation, the "media" (image, music, video etc.) _is the token._&#x20;

Although a token is presented digitally using its media, an on-chain **token's concerns** **are its** **identifier**, **contract**, **reference** and most importantly - **its** **owner**. &#x20;

An NFT's primary use case is providing a cryptographically verifiable way to ascertain that _something_, the reference pointer, is owned by _someone,_ the owner.&#x20;

Worth noting, that the **price** of a token is **not** the concern of the token or token contract itself, but instead a function of the market.&#x20;

### NFT Components

An NFT is made up of several parts, each of those can be grouped into three types: **multimedia**, **reference** **data**, and then **token** itself which lives on chain.

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>NFTs on Mintbase are composed of three basic parts in three steps: Media, reference JSON and the on-chain token data. </p></figcaption></figure>

Wether you are minting programmatically, using our interface, or one of our minting services you will perform the following operations in order:&#x20;

### **1. Upload Multimedia**

One or more files can be associated with an NFT by following its reference data. The only requirement, is that **each file must be reliably accessed via permanent URL.** &#x20;

Due to the permanence and distributed nature of blockchain, newer multimedia hosting services like **Arweave** and **IPFS\*** are now commonly used to store media.&#x20;

A quick search will turn up many ways which you can use these new services. However if you just want to get started quickly, or perhaps you have really large file size requirements, you can use traditionally hosted URLs in the next step.&#x20;

{% hint style="success" %}
**Need permanent storage?** \
****We are developing a service on top of **Arweave** which makes uploading simple and pairs perfectly with our minting APIs. _This service is in alpha, but will be available to the general public sometime in 2023._ &#x20;
{% endhint %}

### 2. Create a Reference (Metadata)

Commonly referred to as "metadata", reference data specifies additional properties of a token while minimizing on-chain storage costs by delegating this data to another host. As with media, this data can be hosted anywhere.&#x20;

For purposes of indexing, metadata has a mostly predictable JSON structure, which is [described in more detail here.](../read-data/metadata.md)&#x20;

The important parts of the schema are:&#x20;

1. The attached media from step one
2. An **array of attributes** that can be used to define properties for your NFT such as "seat", "row", "section" in the case of a ticket being referenced by an NFT.
3. &#x20;A title, description and any other auxiliary information you might deem relevant or useful to the token.&#x20;

Standardization of this schema is still being worked out, though having a global standard would be very helpful for wallets and indexers of the future.

Like media, reference data _must be accessible at a single permanent URL._ Once this URL is available and serving your JSON reliably, you are ready to mint.&#x20;

### 3. Mint On-Chain Tokens

The final step in the NFT creation process is to create a "mint" or "batch\_mint" transaction on a [deployed token contract](../../mintbase-sdk-ref/packages/sdk/src/deployContract/).  Using the metadata JSON URL from the previous step, the tokens' immutable reference to that data is placed onto the blockchain in addition to other optional on-chain fields specified by the [NEAR NEP-177 NFT Metadata Specification](https://nomicon.io/Standards/Tokens/NonFungibleToken/Metadata).&#x20;

More than one token can share the same reference material URL. This can be useful if you need to create multiple copies of the same reference, perhaps for a redeemable promotion code or copies of digital artwork.

**Ready to get going? Start by** [**deploying your contract**](make-your-first-contract-call-deploycontract.md)**, then, move on to** [**upload/mint**](upload-reference-material-to-arweave-and-mint.md)**!**

_\*IPFS currently carries a risk of loosing your content forever if no one hosts it. While solutions to this problem are being worked on, we suggest using Arweave instead. Hosts there are incentivized to keep as many of the networks' contents as possible with Proof of Access block production rewards._&#x20;

