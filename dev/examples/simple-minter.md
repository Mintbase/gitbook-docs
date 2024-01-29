# Build a NFT Minter

This guide will walk you through the process of creating a simple minting page. You will be able to connect your wallet, upload media and input information, and finally, mint your creation. To complete this guide, you should have a basic understanding of React and JavaScript, as well as a functioning wallet connection in your application. If you need help setting up a wallet connection, please refer to [this guide](../getting-started/add-wallet-connection-to-your-react-app.md).

## Step 0: Use a template

If you want you can use a [template ](https://templates.mintbase.xyz/templates/minter)to setup your own NFT Minter.\
Here you have a boilerplate for a simple Minter, but [here](https://templates.mintbase.xyz/templates/ai-minter) you can find a example of an AI Image Generation Minter&#x20;

## Step 1: Install and add config

The initial step involves installing and configuring MBJS. To install you can enter the following lines into the terminal&#x20;

```
pnpm install @mintbase-js/sdk @mintbase-js/storage @mintbase-js/react
pnpm install @near-wallet-selector/core
```

on this tutorial we use other dependencies like[ shadcn/ui](https://ui.shadcn.com/docs/components) for the components.

```
npx shadcn-ui@latest add form
npx shadcn-ui@latest add button
npx shadcn-ui@latest add card
```

For the configuration, you just need to add the info on the file _minter/src/config/setup.ts_. In this step, you can specify the network (testnet or mainnet), the callback URL (the URL where your frontend will be redirected to after contract call wallet signatures), and the contract address (the contract you will use for minting), also the proxyAddress that will allow any user that is not a minter on the contract to mint on your dapp. If you are unfamiliar with how to deploy a contract, please refer to [this guide](../getting-started/make-your-first-contract-call-deploycontract.md) for more information.

```typescript
export const proxyAddress = process?.env?.NEXT_PUBLIC_PROXY_CONTRACT_ADDRESS || "0.minsta.proxy.mintbase.testnet";
const contractAddress = process?.env?.NEXT_PUBLIC_MINT_CONTRACT_ADDRESS || "aiminter.mintspace2.testnet";
const network = process?.env?.NEXT_PUBLIC_NETWORK || "testnet";
const callbackUrl = network === "testnet" ? `https://testnet.mintbase.xyz/contract/${contractAddress}/nfts/all/0` : `https://mintbase.xyz/contract/${contractAddress}/nfts/all/0`;

export const MintbaseWalletSetup = {
  contractAddress,
  network,
  callbackUrl
};
```

&#x20;on the .env file:

```shellscript
NEXT_PUBLIC_MINT_CONTRACT_ADDRESS=  # your store contract address goes here
NEXT_PUBLIC_PROXY_CONTRACT_ADDRESS= # the proxy contract address goes here
NEXT_PUBLIC_NETWORK= # network goes here
```

## Step 2: Get form data

To collect the necessary information, we will first create a standard form where you can gather the fields to be uploaded. You can use any React form package such as react-hook-form for this purpose. In this form, you will gather the title, description, and media. The field names can be anything, but fields containing files must have the key "media", "document", or "animation\_url". These fields will then be used to construct a JSON object that will be uploaded to Arweave.

<pre class="language-typescript"><code class="lang-typescript">
import { Button } from "./ui/button";
import {
  Card,
  CardContent,
  CardFooter,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";

import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormMessage,
} from "@/components/ui/form";

import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import useMintImage from "@/hooks/useMint";
import { getImageData } from "@/hooks/utils";

<strong>
</strong><strong>export default function Minter() {
</strong>  const { form, onSubmit, preview, setPreview } = useMintImage();

  return (
    &#x3C;Form {...form}>
      &#x3C;form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
        &#x3C;Card>
          &#x3C;CardHeader>
            &#x3C;CardTitle>Mint your NFT&#x3C;/CardTitle>
          &#x3C;/CardHeader>
          &#x3C;CardContent>
            &#x3C;FormField
              control={form.control}
              name="title"
              render={({ field }) => (
                &#x3C;FormItem>
                  &#x3C;FormControl>
                    &#x3C;Input placeholder="Title" {...field} />
                  &#x3C;/FormControl>
                  &#x3C;FormMessage />
                &#x3C;/FormItem>
              )}
            />
            &#x3C;div className="h-2">&#x3C;/div>
            &#x3C;FormField
              control={form.control}
              name="description"
              render={({ field }) => (
                &#x3C;FormItem>
                  &#x3C;FormControl>
                    &#x3C;Textarea placeholder="Description" {...field} />
                  &#x3C;/FormControl>
                  &#x3C;FormMessage />
                &#x3C;/FormItem>
              )}
            />
            &#x3C;div className="h-2">&#x3C;/div>
            {preview &#x26;&#x26; (
              &#x3C;img
                src={preview as string}
                alt="Selected Preview"
                style={{
                  maxWidth: "330px",
                  marginTop: "10px",
                  marginBottom: "10px",
                }}
              />
            )}
            &#x3C;FormField
              control={form.control}
              name="media"
            // eslint-disable-next-line @typescript-eslint/no-unused-vars
              render={({ field: { onChange, value, ...rest } }) => (
                &#x3C;FormItem>
                  &#x3C;FormControl>
                    &#x3C;Input
                      id="picture"
                      type="file"
                      {...rest}
                      onChange={(event) => {
                        const { files, displayUrl } = getImageData(event);
                        setPreview(displayUrl);
                        onChange(files);
                      }}
                      className="file:bg-black file:text-white file:border file:border-solid file:border-grey-700 file:rounded-md"
                    />
                  &#x3C;/FormControl>
                  &#x3C;FormMessage />
                &#x3C;/FormItem>
              )}
            />
          &#x3C;/CardContent>
          &#x3C;CardFooter className="justify-center items-center">
            &#x3C;Button type="submit">Mint Me &#x3C;/Button>
          &#x3C;/CardFooter>
        &#x3C;/Card>
      &#x3C;/form>
    &#x3C;/Form>
  );
}

</code></pre>



## Step 3: Setup Mint hook

This hook will do the minting, the file upload, as also validate the form.

```typescript
import { useState } from "react";
import { useForm } from "react-hook-form";
import * as z from "zod";
import { useMbWallet } from "@mintbase-js/react";

import { zodResolver } from "@hookform/resolvers/zod";

import { ArweaveResponse, uploadFile, uploadReference } from "@mintbase-js/storage"
import { formSchema } from "./formSchema";
import { MintbaseWalletSetup, proxyAddress } from "@/config/setup";
import { Wallet } from "@near-wallet-selector/core"

interface SubmitData {
  title: string;
  description: string;
  media: ((false | File) & (false | File | undefined)) | null;
}


const useMintImage = () => {
  const { selector, activeAccountId } = useMbWallet();
  const [preview, setPreview] = useState<string | File>("");

  const getWallet = async () => {
    try {
      return await selector.wallet();
    } catch (error) {
      console.error("Failed to retrieve the wallet:", error);
      throw new Error("Failed to retrieve the wallet");
    }
  };

  const onSubmit = async (data: SubmitData) => {
    const wallet = await getWallet();

    const reference = await uploadReference({
      title: typeof data?.title === 'string' ? data.title : '',
      media: data?.media as unknown as File
    })

    const file = uploadFile(data?.media as unknown as File
    );

    await handleMint(reference.id, file, activeAccountId as string, wallet);
  };

  const form = useForm<z.infer<typeof formSchema>>({
    resolver: zodResolver(formSchema)
  });

  async function handleMint(
    reference: string,
    media: Promise<ArweaveResponse>,
    activeAccountId: string,
    wallet: Wallet
  ) {
    if (reference) {
      await wallet.signAndSendTransaction({
        signerId: activeAccountId,
        receiverId: proxyAddress,
        actions: [
          {
            type: "FunctionCall",
            params: {
              methodName: "mint",
              args: {
                metadata: JSON.stringify({ reference, media: (await media).id }),
                 nft_contract_id: MintbaseWalletSetup.contractAddress,
              },
              gas: "200000000000000",
              deposit: "10000000000000000000000",
            },
          },
        ],
      });
    }
  }

  return { form, onSubmit, preview, setPreview };
};

export default useMintImage;
```

##

## Step 3.1: Upload to permanent storage

In this snippet the [storage module](../../mintbase-sdk-ref/packages/storage/) method `uploadReference()` is called with the metadata object as an argument. This will upload the JSON object to permanent storage as well as the files contained as long as their values correspond to the correct object keys. For more information on how to handle uploading references visit our [Upload Reference Material To Arweave and Mint](../getting-started/upload-reference-material-to-arweave-and-mint.md) guide.

This method returns the id of the hash. It can be appended to the base URI `arweave.net/ + referenceJson.id`. The result of visiting that link is a permanently hosted metadata object!

```typescript
const onSubmit = async (data: SubmitData) => {
    const wallet = await getWallet();

    const reference = await uploadReference({
      title: typeof data?.title === 'string' ? data.title : '',
      media: data?.media
    })

    const file = uploadFile(data?.media);

    await handleMint(reference.id, file, activeAccountId, wallet);
  };
```

## Step 3.2: Minting

In the code below, we add a `handleMint` function that takes a wallet instance, reference, and accountId and makes a mint contract call to the contract corresponding to what was defined in the config.\
If you want to learn how to make a contract call you can check out [this guide](../getting-started/make-your-first-contract-call-deploycontract.md) or the [SDK documentation](../../mintbase-sdk-ref/packages/sdk/) to find all available methods.

```typescript
 async function handleMint(
    reference: string,
    media: Promise<ArweaveResponse>,
    activeAccountId: string,
    wallet: Wallet
  ) {
    if (reference) {
      await wallet.signAndSendTransaction({
        signerId: activeAccountId,
        receiverId: proxyAddress,
        actions: [
          {
            type: "FunctionCall",
            params: {
              methodName: "mint",
              args: {
                metadata: JSON.stringify({ reference, media: (await media).id }),
                 nft_contract_id: MintbaseWalletSetup.contractAddress,
              },
              gas: "200000000000000",
              deposit: "10000000000000000000000",
            },
          },
        ],
      });
    }
  }
```

