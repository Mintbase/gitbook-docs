---
description: How to make and accept offers on Mintbase
---

# Rolling Auction

## Video Walkthrough

{% embed url="https://www.loom.com/share/2fbfea062af54e138ff8017aa07c56b5" %}
Video Walkthrough of a Rolling Auction
{% endembed %}

## Text Walkthrough

On the Token Page, check the Rolling Auction section to see if any tokens are listed via auction (like in the example below).

![Rolling Auction section on the Token Page](<../.gitbook/assets/Screenshot 2022-06-15 at 16.45.47.png>)

Click the **See Auctions** button to go to the auctions page.

<figure><img src="../.gitbook/assets/Screenshot 2022-11-11 at 11.48.25.png" alt=""><figcaption><p>Rolling Auction page</p></figcaption></figure>

### Rolling Auction Page

There are some things going on here, so let's break them down:

#### **Minimum Offer**

The lowest amount you can input as a bid. In the example above it's 0.09 NEAR.

#### **Latest Offer**

The current offer that is winning the auction. The auction only ends, if the Owner accepts an offer.

#### **Offers Table**

In this table you can visualize the offer history on the specific token.



### Rolling Auctions with multiple tokens

If more than 1 token is listed as Rolling Auction, you can navigate between them in this upper tab:

<figure><img src="../.gitbook/assets/Screenshot 2022-11-11 at 11.48.26.png" alt=""><figcaption><p>Tab to navigate different auctions</p></figcaption></figure>

In this example there are 2 tokens currently listed as Rolling Auction and one old auction that has ended (CLOSED). Both listed tokens have offers, if they were empty the tab would say NO OFFERS.



### How to make an offer

<figure><img src="../.gitbook/assets/Screenshot 2022-11-11 at 11.48.27.png" alt=""><figcaption><p>Rolling Auction Page highlighting where to make an offer</p></figcaption></figure>

While logged in, type in your offer in the Make Offer field. It needs to be higher then the Minimum and Current offers.

After you typed the **Make Offer** button will become active. Click it an you will be redirected to the NEAR wallet to validate the transaction. After this your offer is recorded on the blockchain.

{% hint style="info" %}
After an offer has been made, it stays locked in the contract for 24 hours.
{% endhint %}



### After you make an offer

When you make an offer, your funds get into escrow and there are 3 things that can happen:

#### **1. The owner accepts your offer**

In this case your funds go to the owner and you got yourself a new NFT. Nice!

#### **2. Your offer get overtaken**

Someone made an offer higher than yours. In this case, you don't need to do anything and your funds get back to you automatically.

#### **3. Your offer unlocks**

You have the highest offer but after 24 hours the Owner has not accepted it. **In this case, you need to manually withdraw your offer from escrow.** Two ways to do it:

* On the Rolling Auction page, in the Offers table, find your offer and click **Withdraw.**
* Click your profile picture in the navbar (or on mobile on the hamburger menu) and click on **Earned & Orders.** On the tab navigate to **Open Orders.** In the My Offers table, click **Withdraw.**

{% hint style="info" %}
You can check in the Auction Page or in the My Offers page in how long your offer will unlock.
{% endhint %}



### Keep in mind as an buyer:

* You can check all your offers in the [My Offers](https://www.mintbase.xyz/launchpad/my-offers/0) page (under Launchpad)
* When you bid, you put your NEAR into escrow
* When you get outbidded your funds are automatically released from escrow
* The owner of the listing can accept anytime within 24 hours, or later if you do not withdraw your offer
* After an offer you placed unlock, you can pull back your NEAR from escrow by pressing **Withdraw** on the Rolling Auction page, or on the My Offers page (which you can find in the Launchpad)

{% hint style="info" %}
If you have the top offer, and don’t withdraw after 24 hours, the seller can accept it at anytime.
{% endhint %}



### Keep in mind as an seller

* You can check all your received offers in the [Offered To Me](https://www.mintbase.xyz/launchpad/offered-to-me/0) page
* After 24 hours that an offer is made, the offerer can withdraw it and you will no longer be able to accept it

{% hint style="info" %}
Both buyers and sellers can get e-mail notifications of auction events, when turning it on on [User Settings](../creating/sign-in/user-settings.md)
{% endhint %}
