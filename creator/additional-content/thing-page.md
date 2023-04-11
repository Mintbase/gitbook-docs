---
description: The main page containing all info of an NFT
---

# Thing Page

The Thing Page is where all the the info of an NFT is displayed. Here you can check if the NFT is for sale, what type of sale, how many edition there are, who the minter is, and much more.



A **thing** is a collection of multiple **tokens.** When [minting](../creating-nfts/minting-nfts.md) an NFT, you can choose to mint either 1/1 or multiple editions of the same thing. On the thing page, you can check all this, and access the individual token pages.



**To access a Thing Page, simply click on any NFT in the Marketplace.**

![Example of a Thing Page](<../../.gitbook/assets/Screenshot 2022-05-10 at 11.43.05.png>)

There's a lot of stuff to cover here, so we're going to break down each section.

## Default Information

These fields will be visible in all thing pages.



### Listing Details

Here you can check if this NFT is listed via [Simple Sale](../selling-nfts/listing-as-simple-sale.md) or [Rolling Auction](../selling-nfts/listing-as-rolling-auction.md).

![Example of a Listing Details section](<../../.gitbook/assets/Screenshot 2022-05-10 at 17.41.20.png>)

#### Simple Sale

If there are tokens listed as Simple Sale, it will show here, together with the price of each token.

{% content-ref url="../buying-nfts/buying-as-simple-sale.md" %}
[buying-as-simple-sale.md](../buying-nfts/buying-as-simple-sale.md)
{% endcontent-ref %}

#### Rolling Auction

If there are tokens listed as Rolling Auction, it will show how many are available and the button "See Auctions" will be activated. If you click on it you can see all the Auctions, and make your bids.

{% content-ref url="../buying-nfts/buying-as-rolling-auction.md" %}
[buying-as-rolling-auction.md](../buying-nfts/buying-as-rolling-auction.md)
{% endcontent-ref %}

## About

This section is a summary of important information of the NFT. All the infos that are blue, you can click.

![Example of a About section](<../../.gitbook/assets/Screenshot 2022-05-10 at 17.41.28.png>)

### **Store**

[Store](../creating-nfts/what-is-a-mintbase-store.md) where this NFT was minted.

### **Minter**

A store can have [multiple minters](../creating-nfts/store-settings.md#minters), here you can check who minted this specific NFT.

### **Type**

The type of the NFT, it could be an Image, Video, 3D or Audio.

### **Owners**

How many unique owners own this NFT. If it has multiple editions, it can have multiple owners. Or maybe 1 owner who owns all the editions. If it's a 1/1 NFT, if can only have 1 owner.

### **Minted NFTs**

How many editions have been minted.

### **Listed NFTs**

Of the total that has been minted, how many are currently listed.

### **Website Button**

Some NFTs can have websites with "See More" info, that will be linked in this section.

## Properties

Here you can see all the properties of the NFT. These are the properties that you can [filter by on the Store Page](../creating-nfts/store-profile.md#filters).

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-11 at 18.12.42.png" alt=""><figcaption></figcaption></figure>

## Splits

On this section, you can check the percentage set for Royalties and Revenues. Also, which accounts are set to receive Royalties and Revenues (and how much %) once this NFT gets sold.

All this info is set during the [minting](../creating-nfts/minting-nfts.md) process.

![Splits section on the Thing Page](<../../.gitbook/assets/Screenshot 2022-05-20 at 10.53.08.png>)

### **Forever Royalties**

Forever Royalties are perpetual and are set for the lifetime of the NFT. The wallets added here, will get the specified percentage every time the NFT gets sold. The max percentage possible is 50%.

If you **click the percentage** you can see how many accounts are set, which accounts, and how much percentage of the total each one will get.

### **Split Revenues**

Split Revenues clears after every transaction (sell or transfer).

The amount of Split Revenue available depends on the amount of royalties: **100% - X% of Forever Royalties - 2.5% of Market Fee = available revenue.**



**To learn more:**

{% content-ref url="../creating-nfts/splits.md" %}
[splits.md](../creating-nfts/splits.md)
{% endcontent-ref %}



If you **click the percentage** you can see how many accounts are set, which accounts, and how much percentage of the total each one will get. **Like this:**

![Example of the Split Revenue modal with multiple tokens to](<../../.gitbook/assets/Screenshot 2022-05-20 at 11.09.05.png>)

## **Details**

Here you can see more advanced details of the NFT.

![Example of a Details section](<../../.gitbook/assets/Screenshot 2022-05-10 at 17.21.23.png>)

### **Storage Gateway**

Here is specified the storage where the info of the NFT is stored. It's on [Arweave](https://www.arweave.org/), a hybrid and decentralized network.

### **Contract**

The smart contract, or [store](broken-reference), from where this NFT was minted.

### **Transaction ID**

The transaction ID on the blockchain, of the creation of this NFT. If you click the little icon, you'll open on a new tab the NEAR explorer with the specific block detailing the transaction.

### **Thing ID**

The ID of the specific thing on Mintbase.



## Optional Information

These fields are optional to be filled during the minting process. If they weren't filled, they will not show up in the Thing Page.

### Location

Some NFTs have locations, a use case for this is for example if the NFTs are tickets for a festival.

![Example of a Location section](<../../.gitbook/assets/Screenshot 2022-05-10 at 17.28.51.png>)

### Media

It's possible to add media to an NFT, that will be forever stored on the blockchain (also using [Arweave](https://www.arweave.org/)).

![Example of a Media section](<../../.gitbook/assets/Screenshot 2022-05-10 at 17.29.17.png>)

Can be used for highres images, videos, 3D files, PDF documents...

