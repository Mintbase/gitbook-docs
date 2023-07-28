# 🔁 Buying as Rolling Auction

After [finding](browsing-mintbase.md) an listed NFT that you like, you can decide to buy it.

On the right side of the thing page, you can see that this NFT is listed as [**Simple Sale**](buying-as-simple-sale.md) and as **Rolling Auction**.

<figure><img src="../.gitbook/assets/Screenshot 2023-07-05 at 17.13.00.png" alt=""><figcaption></figcaption></figure>

Click on **See Auctions** to go to the Auction page.

<figure><img src="../.gitbook/assets/Screenshot 2023-04-11 at 12.39.44.png" alt=""><figcaption><p>Auction page</p></figcaption></figure>

## **Important Fields**

#### **NO OFFERS / CLOSED tabs**

On the top of the page you can a tab that says NO OFFERS (that is currently selected) and CLOSED.

The NO OFFERS is an auction that is currently open but doesn't have offers yet.

The CLOSED tabs, are past auctions that are closed. They are kept for provenance purposes.

#### **Minimum Offer**

The lowest amount you can input as a bid. In the example above it's 5 NEAR.

#### **Latest Offer**

The current offer that is winning the auction. The auction only ends, if the Owner accepts an offer.

#### **Offers Table**

In this table you can visualize the offer history on the specific token.

## How to make an offer

While logged in, type in your offer in the **Make Offer** field. It needs to be higher than the Minimum and Current offers.

After you typed the **Make Offer** button will become active.

Click it and you will be redirected to your wallet to validate the transaction. After this your offer is recorded on the blockchain.

{% hint style="info" %}
After an offer has been made, it stays locked in the contract for 24 hours.
{% endhint %}

{% embed url="https://www.loom.com/share/2fbfea062af54e138ff8017aa07c56b5" %}
Auction walkthrough
{% endembed %}

## After you make an offer

When you make an offer, your funds get into escrow and there are 3 things that can happen:

#### **1. The owner accepts your offer**

In this case your funds go to the owner and you got yourself a new NFT. Nice!

#### **2. Your offer get overtaken**

Someone made an offer higher than yours. In this case, you don't need to do anything and your funds get back to you automatically.

#### **3. Your offer unlocks**

You have the highest offer but after 24 hours the Owner has not accepted it. **In this case, you need to manually withdraw your offer from escrow.** Two ways to do it:

* On the Rolling Auction page, in the Offers table, find your offer and click **Withdraw.**
* Click on **Orders** under **Manage** in the navbar.

{% hint style="info" %}
You can check in the Auction Page or in the My Offers page in how long your offer will unlock.
{% endhint %}

### Keep in mind as an buyer:

* You can check all your offers in the [My Offers](https://www.mintbase.xyz/launchpad/my-offers/0) page (under Create)
* When you bid, you put your NEAR into escrow
* When you get outbidded your funds are automatically released from escrow
* The owner of the listing can accept anytime within 24 hours, or later if you do not withdraw your offer
* After an offer you placed unlock, you can pull back your NEAR from escrow by pressing **Withdraw** on the Rolling Auction page, or on the My Offers page (which you can find in the Launchpad)

{% hint style="info" %}
If you have the top offer (and don’t withdraw after 24 hours) the seller can accept it at anytime.
{% endhint %}

