# addMinter

Give an account id minting permission for a smart contract of your choice.

**As with all new SDK api methods, this call should be wrapped in** [**execute**](../../../../mintbase-sdk-ref/packages/sdk/src/#execute) **and passed a signing method**

## addMinter(args: addMinterArgs): NearContractCall

`addMinter` takes a single argument of type `AddMinterArgs`

```typescript
type AddMinterArgs = {
    //the contract you own for which you wish to grant minting access
    //as an argument or through NFT_CONTRACT_ID env
    nftContractId?: string;
    //the id of the account that will be allowed to mint on the corresponding nftContractId
    minterId: string;
};
```

Example usage of addMinter method in a hypothetical React component:

{% code title="AddMinterUI.ts" overflow="wrap" lineNumbers="true" %}
```typescript
import { useState } from 'react';
import { useWallet } from '@mintbase-js/react';
import { execute, addMinter } from '@mintbase-js/sdk';


export const AddMinterUI = ({ contractId, minterId }:any) => {
  const { selector } = useWallet();
  const handleAddMinter = async (): Promise<void> => {
    const wallet = await selector.wallet();
    await execute(
      addMinter({ nftContractId: contractId, minterId: minterId })
    );
  return (
    <div>
      <button onClick={() => handleAddMinter()}>
        addMinter to contract you own
      </button>
    </div>
  );
};
```
{% endcode %}
