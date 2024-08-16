---
description: >-
  The Bitte Paymaster service lets you create a dedicated wallet that acts as a
  relayer, covering gas fees for your users. This means your users can interact
  with your app without needing to hold NEAR.
---

# 🌀 Paymaster

{% embed url="https://youtu.be/95VPFESsfv0" %}

## Creating a Paymaster

Now you can enable your community to interact with your smart contracts freely. They will not need crypto to mint, vote on your DAOs, or receive free airdrops.

1. Go to the Bitte Wallet
2. Head to the APPs tab
3. Click "New Paymaster"

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

4. Enter the contract you want to sponsor on NEAR
5. Functions will appear below that you can toggle to enable or disable functionalities you want your users to run for free.\


<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

6. Fund your paymaster wallet with enough funds to sponsor gas for transactions

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>



The paymaster is now successfully created and will automatically fund the transactions defined before!\


<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## Using the paymaster



There are currently 2 ways to use the paymaster, either directly through the [wallet](https://wallet.bitte.ai/) or via code.



### Using Paymaster Via Wallet

In the previous example I created a sponsorship for the contract blackdragon.tkn.near and selected the method "ft\_transfer". Now whenever someone transacts on that contract/method through the wallet their gas fee will be sponsored.

This makes it easy to use, by adding a wallet connection to any application users can be redirected to bitte to sign transactions at which point the sponsorship will take effect.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>



### Using Paymaster with Code

To use the paymaster via code you must have access to accounts from within your application.



Start by copying the relayer URL from the dashboard.&#x20;

The next step involves buildinng the transaction and sending it to that URL via a post request, you can check the [official near docs](https://docs.near.org/concepts/abstraction/relayers) for more information or use this[simple wrapper library to get started](https://github.com/SurgeCode/near-relay)&#x20;

```typescript
pnpm i @near-relay/client


import { relayTransaction } from "@near-relay/client";

/**
 * Signs a transaction and sends it to a relayer to get dispatched
 *
 * @param {Action[]} action - The list of actions to include in the transaction.
 * @param {string} receiverId - The ID of the receiver.
 * @param {string} relayerUrl - Url for the relayer to which the tx will be sent
 * @param {Account?} account - Optionally pass in local account
 * @param {string?} network - 'mainnet | testnet'
 * @returns {Promise<any>} - Most likely a receipt (depends on format being returned by relayer).
 */

const receipt = await relayTransaction(action: Action | Action[], receiverId: string, relayerUrl: string, network: string, account: Account)
```

\
\


\
\
\
