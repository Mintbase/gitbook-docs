# Build a Simple Minter

This guide will walk you through the process of creating a simple minting page. You will be able to connect your wallet, upload media and input information, and finally, mint your creation. To complete this guide, you should have a basic understanding of React and JavaScript, as well as a functioning wallet connection in your application. If you need help setting up a wallet connection, please refer to [this guide](../getting-started/add-wallet-connection-to-your-react-app.md).

## Step 1: Install and add config

The initial step involves installing and configuring MBJS. To install you can enter the following lines into the terminal&#x20;

```
npm install @mintbase-js/sdk
npm install @mintbase-js/storage
```

For the configuration, this function can be added to any of your parent components, such as `app.tsx` or `index.tsx`. In this step, you can specify the network (testnet or mainnet), the callback URL (the URL where your frontend will be redirected to after contract call wallet signatures), and the contract address (the contract you will use for minting). If you are unfamiliar with how to deploy a contract, please refer to [this guide](../getting-started/make-your-first-contract-call-deploycontract.md) for more information.

```typescript
import { mbjs } from "@mintbase-js/sdk";

mbjs.config({
    network: process.env.NEXT_PUBLIC_NEAR_NETWORK,
    callbackUrl: process.env.NEXT_PUBLIC_CALLBACK_URL,
    contractAddress: process.env.NEXT_PUBLIC_CONTRACT_ADDRESS,
  });
```

## Step 2: Get form data

To collect the necessary information, we will first create a standard form where you can gather the fields to be uploaded. You can use any React form package such as react-hook-form for this purpose. In this form, you will gather the title, description, and media. The field names can be anything, but fields containing files must have the key "media", "document", or "animation\_url". These fields will then be used to construct a JSON object that will be uploaded to Arweave.

```typescript
export default function Minter() {
  const { selector, activeAccountId } = useWallet();

  const methods = useForm({
    defaultValues: {
      [TITLE]: "",
      [DESCRIPTION]: "",
      [MAIN_IMAGE]: null,
    },
  });
  const { getValues, handleSubmit } = methods;
  //gets called on form submit
  const onSubmit = async (data: { [x: string]: any }) => {
    const wallet = await selector.wallet();
    //get file from form
    const file = getValues(MAIN_IMAGE);
    //validate that it was correctly retrieved
    if (file == null || activeAccountId == null) {
      console.error("Error uploading file")
      return
    }
    //call handleUpload method with file and formData
    const reference = await handleUpload(file, data);
  };

  return (
    <div className="md:max-w-2xl w-full space-y-4">
      <div className="flex flex-col items-center justify-center mt-2">
        <MbText className="text-3xl">Mint your NFTs</MbText>
        <div className="w-full mt-4 space-y-4">
          <FormProvider {...methods}>
            <form
              onSubmit={handleSubmit(onSubmit, (errorMsgs) =>
                console.error(errorMsgs)
              )}
            >
              <MintForm />
              <div className="flex justify-center items-center mt-4">
                <MbButton type="submit" label="Mint Me" />
              </div>
            </form>
          </FormProvider>
        </div>
      </div>
    </div>
  );
}

async function handleUpload(file: File, data: { [x: string]: any }): Promise<string> {
  //build object with form data
  const metadata = {
    title: data[TITLE],
    description: data[DESCRIPTION],
    media: file
  };
}

```



## Step 3: Upload to permanent storage

In this snippet the [storage module](../../mintbase-sdk-ref/packages/storage/) method `uploadReference()` is called with the metadata object as an argument. This will upload the JSON object to permanent storage as well as the files contained as long as their values correspond to the correct object keys. For more information on how to handle uploading references visit our [Upload Reference Material To Arweave and Mint](../getting-started/upload-reference-material-to-arweave-and-mint.md) guide.

This method returns the id of the hash. It can be appended to the base URI `arweave.net/ + referenceJson.id`. The result of visiting that link is a permanently hosted metadata object!

```typescript
async function handleUpload(file: File, data: { [x: string]: any }): Promise<string> {
  const metadata = {
    title: data[TITLE],
    description: data[DESCRIPTION],
    media: file
  };

  const referenceJson = await uploadReference(metadata)
  console.log("Successfully minted with referece:", referenceJson.id)
  return referenceJson.id
}
```

## Step 4: Minting

In the code below, we add a `handleMint` function that takes a wallet instance, reference, and accountId and makes a mint contract call to the contract corresponding to what was defined in the config.\
If you want to learn how to make a contract call you can check out [this guide](../getting-started/make-your-first-contract-call-deploycontract.md) or the [SDK documentation](../../mintbase-sdk-ref/packages/sdk/) to find all available methods.

```typescript
const onSubmit = async (data: { [x: string]: any }) => {
    const wallet = await selector.wallet();
    const file = getValues(MAIN_IMAGE);

    if (file == null || activeAccountId == null) {
      console.error("Error uploading file")
      return
    }

    const reference = await handleUpload(file, data);
    await handleMint(reference, activeAccountId, wallet);
  };
  

async function handleMint(reference: string, activeAccountId: string, wallet: any) {

  if (reference) {
    const mintCall = mint({
      reference: reference,
      ownerId: activeAccountId,
    })

    await execute({ wallet }, mintCall)
  }
}
```

