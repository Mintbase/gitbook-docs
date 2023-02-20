# 📄 Make Your First Contract Call (deployContract)

This guide will walk you through making your first contract call using the [Mintbase JS SDK](../../mintbase-sdk-ref/packages/sdk/).&#x20;

\
Mintbase offers a streamlined way to deploy your very own token smart contract equipped with all the necessary methods you might need. This can be achieved by making a call to our [factory contract](../smart-contracts/) with the provided [deployContract](../../mintbase-sdk-ref/packages/sdk/src/deployContract/) SDK method. For more documentation regarding how to call other methods check out the [SDK documentation](../../mintbase-sdk-ref/packages/sdk/).

\
A prerequisite is to be able to have a wallet connection mechanism in your application. For that, you can check out a small guide on how to [Add wallet connection to your react app](add-wallet-connection-to-your-react-app.md).\


### Step 1: Get wallet instance

```typescript
import { useWallet } from '@mintbase-js/react';

const DeployContractUi = ({ tokenId, contractId }) => {
  const { selector, activeAccountId } = useWallet();
  const wallet = await selector.wallet();
  
}

```

### Step 2: Construct the contract call object

The SDK offers wrappers to make executing contract calls as easy as possible. These were specifically made to facilitate Mintbase market and token contract interaction.

In this case we are building a deployContract object with the specified fields that can be referenced [here](../../mintbase-sdk-ref/packages/sdk/src/deployContract/)



**Note: this does not call the method**\


```
npm install @mintbase-js/sdk
```

```typescript
import { useWallet } from '@mintbase-js/react';
import { deployContract } from '@mintbase-js/sdk';

const DeployContractUI = ({ name, owner, contractId, symbol }:any) => {
  const { selector } = useWallet();
  const handleDeployContract = async (): Promise<void> => {
    const wallet = await selector.wallet();
    const deployArgs = deployContract({
          name: name,
          ownerId: owner,
          metadata: {
            symbol: symbol
          }
        })
  };
};

```

### Step 3: Execute the contract call

The execute method takes any number of contract call objects and executes them using a provided wallet instance.&#x20;

Congratulations! Now that you have deployed your very own token contract you can interact with it by calling any of the SDK methods!\
[Try minting a token](upload-reference-material-to-arweave-and-mint.md).

````typescript
import { useState } from 'react';
import { useWallet } from '@mintbase-js/react';
import { execute, deployContract } from '@mintbase-js/sdk';

const DeployContractUI = ({ name, owner, contractId, symbol }:any) => {
  const { selector } = useWallet();
  const handleDeployContract = async (): Promise<void> => {
    const wallet = await selector.wallet();
    await execute(
          {wallet},
          deployContract({
          name: name,
          ownerId: owner,
          metadata: {
            symbol: symbol
          }
      })
    )
  };
  return (
    <div>
      <button onClick={() => handleDeployContract()}>
        DeployContract with name= {name} and owner= {owner}
      </button>
    </div>
  );
};
```

````

## Join Us and Build the Future

Have feedback or perhaps need a hand? **Reach out on our** [**Telegram**](https://t.me/mintdev) **public developer support channel where we are happy to help!**

Building something cool? **Consider** [**applying for a grant**](https://github.com/Mintbase/Grants-Program)**.**
