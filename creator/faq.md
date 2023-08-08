---
description: Frequently Asked Questions
---

# 🙋 FAQs

Have feedback or perhaps need a hand? **Reach out on our on** [**Telegram**](https://t.me/Mintbase) **where we are happy to help! Also follow us on** [**Twitter**](https://twitter.com/mintbase) **to keep up with updates.**

***

## Getting Started

{% content-ref url="getting-started/" %}
[getting-started](getting-started/)
{% endcontent-ref %}

### What does it mean to connect to Mainnet or Testnet?

Mintbase can be used on Mainnet or Testnet. Mainnet is the live, production network where transactions are processed using real funds. Testnet, on the other hand, is a simulated network for testing purposes. This means that on Testnet, users are free to test the same features without using real money.

### How do I connect my wallet to Mintbase?

If your wallet is not connected, you'll see a Connect Wallet button in the top right corner of any page on Mintbase. Click on it and follow the prompts to connect your wallet. You'll need to authorize the connection to Mintbase with limited access. Mintbase never has direct access to your funds.

### **Are all future sales tied into this platform and cryptocurrency?**

You can sell the NFT on whatever platform you like as long as it follows the NFT standard. Even if you decide to build your own platform, later on, your NFTs can be sold and resold there. NFTs are interoperable.&#x20;

Read more about [interoperability.md](interoperability.md "mention")

### **What happens if we have thousands of sales and you decide to close, etc?**

As long as NEAR and Arweave survive (where your token is stored) your token will survive. Arweave stores data for over 100 years.

***

## Selling NFTs

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

### Does Mintbase take a cut from my sales?

Mintbase market fee is 2.5%.&#x20;

### **What is a Storage Deposit and why is it required to list on the market?**

When you list a token for sale on Mintbase, you will be asked to deposit 0.01N per token listed into the market contract. This deposit is required by the NEAR protocol and is not a Mintbase fee. The deposit will be refunded to you when a token is sold or the listing is removed. For more information on, you can read more about [Storage Staking on NEAR Protocol](https://docs.near.org/concepts/storage/storage-staking).&#x20;

### **What is the process for selling an NFT for a Simple Sale on Mintbase?**

When choosing [Simple Sale](../market/listing-as-simple-sale.md), you're listing an NFT for a fixed price. You need to select Simple Sale on the Listing Type, choose the currency you want (NEAR, USDC, and USDT are supported) and type the price in the Price field. Then, type the amount you want to list in the Amount to List field. If you only have 1 token, you're limited to 1. Finally, authorize the transaction on your wallet.

### **How does the Rolling Auction work on Mintbase?**

When listing for [Rolling Auction](../market/listing-as-rolling-auction.md), you're starting an auction where people can make bids on your NFT. You choose which bid to accept to finish the auction. After 24 hours that an offer is made, the offerer can withdraw it and you will no longer be able to accept it. Both buyers and sellers can get e-mail notifications of auction events, when turning it on on User Settings. You need to manually accept the offer for it to go through.

### **Can I sell NFTs that I don't own on Mintbase?**

Yes, you can sell NFTs that you don't own through [AffiliateDirect](../market/selling-as-affiliate.md) links and **earn a 1.25% market fee**. On any Thing Page, click on Copy AffiliateDirect Link and start sharing the link. If someone buys this NFT through the link you shared, you instantly receive 1.25% of the sale. You need to be connected to Mintbase to generate the AffiliateDirect link.

### **How can I relist or remove a listing on Mintbase?**

If you want to edit a listing, you can choose to Relist the NFT or [Remove Listing](../market/relisting-or-remove-listing.md). For relisting, follow the same steps of how to list and the new listing will override the old listing. To remove a listing, find the NFT you want to unlist, click on the More Options (...) button, click on Remove Listing, and then a modal will pop up with information about the listing. Click on Remove Listing again and authorize the transaction on your wallet.

***

## Buying NFTs

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

### What is the process for buying an NFT via Simple Sale?

After finding an NFT listed as a [Simple Sale](../market/buying-as-simple-sale.md), you can see the price in NEAR and the approximated conversion in USD. Click on "Buy with NEAR" and authorize the transaction on your wallet. After the transaction is complete, you can access the Activity page to see your transaction or click on Create and My NFTs to find your new purchase.

### **What is a Rolling Auction and how can I participate?**

A [Rolling Auction](../market/buying-as-rolling-auction.md) is a type of auction where you can make an offer on an NFT. After you make an offer, it stays locked in the contract for 24 hours. During this time, the owner can accept your offer, or someone else can make a higher offer (which would return your funds to you). If your offer is the highest and the owner does not accept it within 24 hours, you can manually withdraw your offer from escrow, or the owner can accept it at any time.

### **What happens to my funds when I make an offer in a Rolling Auction?**

When you make an offer, your funds go into escrow. If the owner accepts your offer, your funds go to the owner and you receive the NFT. If someone makes a higher offer, your funds are automatically released from escrow. If you have the highest offer but the owner does not accept it within 24 hours, you need to manually withdraw your offer from escrow.

### **How can I withdraw my offer from escrow in a Rolling Auction?**

After an offer you placed unlocks, you can pull back your NEAR from escrow by pressing Withdraw on the Rolling Auction page, or on the My Offers page, which you can find under Manage in the navbar.

***

## Creating NFTs

{% content-ref url="creating-nfts/" %}
[creating-nfts](creating-nfts/)
{% endcontent-ref %}

### **What is a Mintbase contract?**

A [Mintbase Contract](creating-nfts/what-is-a-mintbase-store.md) is a smart contract that allows you to mint various types of NFTs (Non-Fungible Tokens) on it. You're the owner of the contract and Mintbase can't access it.&#x20;

### **How can I customize my contract?**

There is a lot you can [customize](creating-nfts/customize-contract.md) without code: you can change the name of your contract, add social media and website links, and upload a logo and a header image. You can also add minters who are allowed to mint NFTs on your contract. Furthermore, you can set default royalties for every mint on your contract, and even transfer the ownership of the contract to another NEAR account. There's also an "About" tab where you can provide detailed information about your contract or project. **Using code the possiblities are endless.** [Check out our developer section for more info on this.](../dev/getting-started/)

### **What are Royalties?**

You can set up [royalties](creating-nfts/splits.md) to automatically share revenue with wallets. These wallets will then receive their specified share of the revenue each time the NFT is sold.

### What are Split Revenues?

Split Revenue are shares that clear after each sale.

### **NSFW content**

We allow some variants of NSFW content, but will not support it on our UI as an easy-to-find element. All content needs, however, to abide by our [Terms of Service](https://docs.mintbase.io/company/privacy-policy-and-terms-of-service).

### **I want to include a message for the buyer of my NFT with specific information about copyrights. How can I do that?**

You can easily include a PDF with the NFT. Just keep in mind that this PDF can be viewable by anyone.

### **Is there a fee when you transfer the NFTs as a gift?**&#x20;

No, there's no fee.

### I want to mint a video or a large file

You will be able soon to pay for your own NFT storage on arweave and mint files as large as you want. The current file limits are temporary while we figure out the best way to implement this.

### I made a mistake, can I edit my NFT?

After you mint the NFT it cannot be edited at all. The blockchain is immutable. The solution is to burn your tokens and mint them again with the correct information.

### Can I transfer tokens from one store to another?

No, not yet. You can currently only transfer tokens from one NEAR wallet to another wallet address.

### What happened to the Ethereum Tokens on Mintbase ETH?&#x20;

Ethereum is another blockchain and they stay where they are, on the Ethereum chain. Once we figured out interoperability between chains,  there may be a way to transport ETH NFTs (ERC-721) to NEAR and NEAR NFTs (NEP-171) to Ethereum.
