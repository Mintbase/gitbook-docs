---
description: How to set a NFT for sale
---

# Listing NFTs

After having [minted](minting-nfts.md) your NFT, you can set it for sale.

In the Launchpad tab, click on **List** button under the NFT you want to set for sale.

![](<../../.gitbook/assets/Untitled design (13).png>)

Now you are on the Listing page. You can list your NFT for simple sale or set up a rolling auction.&#x20;

### Simple Sale

You set a fixed price and anyone can buy it.

![](<../../.gitbook/assets/Screenshot 2022-08-12 at 10.10.54.png>)

#### Amount to List

This first input is the number of tokens you wish to list. In the example above, the NFT has 7 tokens that you could list. If you want to You can list up to 25 tokens in one go.

If you want to list each one at a different price, leaving "1" in this field, and making 7 different listings.

#### Price

Type the price in NEAR of your token (price of each one, if you were to list multiple at once).



**Storage Deposits**

When you list a token for sale on Mintbase, you will be asked to deposit 0.01N _per token_ listed into the market contract. _**This is NOT an additional fee and will be refunded to you when a token is sold, or your the listing is removed.**_ &#x20;

For more details regarding storage deposits [read this section or our FAQ](../../market/faq.md#what-is-a-storage-deposit-and-why-is-it-required-to-list-on-the-market)



### Rolling Auction

On the listing page, toggle between **Simple Sale** and **Rolling Auction.** Just as with Simple Sale, you'll first need to decide how many tokens you want to list. Here, rather than selecting a price, you'll need to fix a minimum bid for your auction. Buyers will not be able to bid under your minimum price.&#x20;

Each bid is active for 24hrs. After this, if you don't accept the offer, it will expire. Read more about how auctions work under [auctions.md](../../market/auctions.md "mention").

![](<../../.gitbook/assets/Screenshot 2022-08-12 at 10.30.02.png>)

That's it! After filling these fields press **Make Listing**, sign the transaction in the NEAR interface and you will see a success page. Now, your listing is visible in the Marketplace.

{% hint style="info" %}
Today we don't have a feature to unlist a token. **If you do a new listing of a token that is already listed, it will override the old listing.**
{% endhint %}
