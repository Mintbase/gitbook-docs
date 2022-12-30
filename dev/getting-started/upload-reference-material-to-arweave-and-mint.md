# ☁ Upload Reference Material To Arweave and Mint

Uploading reference material to permanent storage through the [Mintbase JS Storage](../../mintbase-sdk-ref/packages/storage/)[ module](../../mintbase-sdk-ref/packages/storage/) is easy. \
This makes including minting functionality on your app a breeze by abstracting away the permanent metadata storage! This guide will walk you through it.

### Step 1: Get your API key

...To be added\
For now, this functionality is temporarily not restricted by an API key

### Step 2: Install the Storage Module

```
npm install @mintbase-js/storage
```

or

```
yarn install @mintbase-js/storage
```

### &#x20;**Step 3: Make a component that uploads a file**

&#x20;This example accepts a file via input and then calls the storage method `uploadResult`which receives an argument of type File.

When a result is returned the payload will contain an id field. When this is appended to the https://arweave.net/ base URI we will have a link to a permanently stored file!&#x20;

```typescript
import { useState } from 'react';
import { uploadFile } from '@mintbase-js/storage'

const FileUpload = () => {
  const [file, setFile] = useState<File | null>(null);

  const handleChange = (e: any) => {
    setFile(e.target.files[0]);
  };

  const handleSubmit = async (e: any) => {
    e.preventDefault();
    if (!file) return;
    //call storage method to upload file to arweave
    const uploadResult = await uploadFile(file);
    console.log("https://arweave.net/" + uploadResult.id)
  };

  return (
    <div>
      <form onSubmit={handleSubmit}>
        <input type="file" onChange={handleChange} />
        <button
          type="submit"
        >
          Upload
        </button>
      </form>
    </div>
  );
};
```

### Step 4: Use the Arweave Link to Mint a Token! 

Now that we have a link to the permanently stored file we can proceed to make the contract call.\
If you haven't deployed a contract yet check out our guide on [How to deploy a contract](#user-content-fn-1)[^1] or reference the [documentation](../../mintbase-sdk-ref/packages/sdk/src/deployContract/).

For more information on how to mint through a call to your very own token contract check out [Make Your First Contract Call](make-your-first-contract-call-deploycontract.md) and the [Mint method documentation](../../mintbase-sdk-ref/packages/sdk/src/mint/).

In this snippet, we are getting an instance of the connected wallet and constructing a Mint method call object, and supplying them both to the execute command.

The Arweave URL that we previously generated should be passed into the reference field. More in-depth information relating to the fields can be found in the documentation.

With all this done you should now be able to mint tokens from the uploaded reference material!

<pre class="language-typescript"><code class="lang-typescript">import { useWallet } from '@mintbase-js/react';
import { execute, mint } from '@mintbase-js/sdk';

<strong>const MintUI = ({ reference, contractId, owner }:any) => {
</strong>  const { selector } = useWallet();
  const handleMint = async (): Promise&#x3C;void> => {
    const wallet = await selector.wallet();
    await execute(
      mint({
         nftContractId: contractId,
         reference: reference, 
         ownerId: owner }),
      { wallet },   
    );
  return (
    &#x3C;div>
      &#x3C;button onClick={() => handleMint()}>
        Mint
      &#x3C;/button>
    &#x3C;/div>
  );
};
</code></pre>

\


[^1]: coming soon
