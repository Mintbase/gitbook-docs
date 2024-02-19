# 🖥 Executing server side contract calls

In our previous guide [make-your-first-contract-call-deploycontract.md](make-your-first-contract-call-deploycontract.md "mention") , we explored the process of setting up a wallet connection on a client to facilitate smart contract executions. While wallets primarily manage user account keypairs, they can also be employed directly. This approach is often used on the server side to manage admin accounts responsible for performing specific transactions.

### Step 1: Setup



Install the necessary libraries using:

```
npm i @mintbase-js/auth

npm i @mintbase-js/sdk
```



### Step 2: Instantiate the account

A near account will correspond to one or multiple keypairs, we can choose to instantiate one through the seedphrase or private key. In this case we will use a private key. We start by setting a keystore and then calling the connect method which produces an account object which can then be used to send transactions.

```typescript

import {connect} from "@mintbase-js/auth";
import nearAPI, { KeyPair } from "near-api-js";

const ACCOUNT_ID = "YOUR-ACCOUNT-ID";
const PRIVATE_KEY = "YOUR-PRIVATE-KEY";
const NETWORK = "mainnet"

const keyStore = new nearAPI.keyStores.InMemoryKeyStore();
await keyStore.setKey(
    NETWORK,
    ACCOUNT_ID,
    KeyPair.fromString(PRIVATE_KEY),
  );
 const account = await connect(ACCOUNT_ID, keyStore, NETWORK);
```



### Step 3: Send Transactions



Now that we have the account object the next step is to create the arguments for the transactions. In this case we are gonna make a listing on the mintbase marketplace.&#x20;

In order to make a listing I need to make a contract call to deposit storage and then another to make the listings.&#x20;

For the list call the arguments are the contractAddress on which the nft was minted on and the corresponding tokenId. The token needs to belong to the account which was instantiated before.&#x20;

You can learn how to mint an nft here [upload-reference-material-to-arweave-and-mint.md](upload-reference-material-to-arweave-and-mint.md "mention")

```typescript
const depositStorageCall = depositStorage({}) 

const listCall = list({price: "1", tokenId: "the-id-for-my-token", contractAddress: "contract-from-where-my-token-was-minted"})
  
```

Now we call the execute method that can take any amount of contract call arguments in an array and attach the account object from which the call is going to be made.

```typescript
const response = await execute({ account }, [depositStorageCall, listCall]);
```

