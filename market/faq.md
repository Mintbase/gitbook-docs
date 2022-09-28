---
description: Frequently Asked Questions on Mintbase
---

# FAQ

### Lister burned the NFT while my offer is pending

Just wait until your offer expires (24 hours) and you can withdraw it from the[ orders page](https://www.mintbase.io/orders).

### Lister transferred the NFT to someone else while my offer is pending

Just wait until your offer expires (24 hours) and you can withdraw it from the[ orders page](https://www.mintbase.io/orders).

### Bid expired on my NFT, can I still take?

No sorry. We are working on adding a notification system to warn when an offer has been set and is about to expire.&#x20;

### Why bids expire so quick?

The expiration time is fully adjustable on the smart contracts side, but since it's just the start, we want to keep the features limited to battle test. In the future we can offer adjustable expiration time.

### **What is a Storage Deposit and why is it required to list on the market?**

A storage (or "state") deposit is a staking mechanism that incentivizes NEAR network participants to store the record of your listing on the blockchain for as long as it is needed.&#x20;

Once your token is no longer listed on the market, the storage deposit is no longer required and returned to you. For more information on, you can read more about [Storage Staking on NEAR Protocol](https://docs.near.org/concepts/storage/storage-staking).&#x20;

### Can I list Multiple NFTs with the same metadata (Thing) for auction?

Yes. This is the default option, when you list you are including all NFTs of your thing.

### **Are all future sales tied into this platform and crypto currency?**

You can sell the NFT on whatever platform you like as long as it follows the NFT standard. Even if you decide to build your own platform later on, your NFTs can be sold and resold there. NFTs are interoperable. If that other platform decides to integrate fiat (credit card) payments, or other crypto currencies, they can do so. How other platforms handle payments, is up to them.

### **What happens if we have thousands of sales and you decide to close it etc?**

As long as NEAR and Arweave survive (where your token is stored) your token will survive. Arweave stores data for over 100 years.

### **NSFW**

We will be following the same sort of view as reddit, we will allow some variant of NSFW content, but will not support it on our UI as an easy to find element. You could use the mintbasejs library when it's ready to build your own platform however as the license will be MIT..

### **Locked content**

Locked content = dependence on Mintbase and our goal is to separate any dependence from the main app. So if Mintbase dies tomorrow, your token lives on.

We are working with Mintgate on a solution.

### C**an I use the NFT I mint on the testnet for the mainnet auction?**

No, you can only use the testnet NFTs on the testnet auction and not on the mainnet.&#x20;

### **I want to include a message for the buyer of my NFT with specific information about copyrights. How can I do that?**

You can easily include a PDF with the NFT. Just keep in mind that this PDF can be viewable by anyone.

### **What is the Mintbase fee?**&#x20;

2.5% on every sale

### **Is there a fee when you transfer the NFTs as a gift?**&#x20;

No, there's no fee.

### If I try to mint more than one thing the transaction fails

If your initial storage fee of 7 NEAR is almost used up you will need to top it up by sending more NEAR to your contract wallet.&#x20;

### I want to mint a video or a large file

You will be able soon to pay for your own NFT storage on arweave and mint files as large as you want. The current file limits are temporary while we figure out the best way to implement this.

### I made a mistake, can I edit my NFT?

After you mint the NFT it cannot be edited at all. The blockchain is immutable. The solution is to burn your tokens and mint them again with the correct information.

### What is my account name?

Your account name is the NEAR wallet name you have. You can have different account names and connect them to Mintbase.\


![](<../.gitbook/assets/Screen Shot 2021-06-28 at 11.25.32.png>)

### What is my store name?

The store name is the name of your smart contract that you deployed. As such, if you name your store "wildeverse" your store name is wildeverse.mintbase1.near\
You can see all the transactions of your store in the block explorer by entering [https://explorer.near.org/accounts/wildeverse.mintbase1.near](https://explorer.near.org/accounts/wildeverse.mintbase1.near)\
\
or going to [https://explorer.near.org/](https://explorer.near.org/) and search for your store name.

![](<../.gitbook/assets/Screen Shot 2021-06-28 at 11.31.25.png>)



### How do I have access to the NEAR wallet (other than logging into your Mintbase page)?

Go to [https://wallet.near.org/](https://wallet.near.org/)

### What happened to all my wallets I had on my account?

We had social login & email login as the main credentials for your account. We changed that. Now your wallet is your login on mintbase. No more twitter / google accounts needed.

This means that your account information was ported over to each wallet you had connected.

### How do I disable notifications?

Notifications are opt-out. You can disable each one of them on your Notifications page (https://mintbase.io/notifications)

![](<../.gitbook/assets/image (1).png>)

### What happen to the Ethereum Tokens on Mintbase ETH?&#x20;

Ethereum is another blockchain and they stay where they are, on the Ethereum chain. Once we figured out interoperability between chains,  there may be a way to transport ETH NFTs (ERC-721) to NEAR and NEAR NFTs (NEP-171) to Ethereum.



### Can I transfer tokens from one store to another?

No, not yet. You can currently only transfer tokens from one NEAR wallet to another wallet address.
