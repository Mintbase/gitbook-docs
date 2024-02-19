# 📂 Add wallet connection to your react app

This a quick guide walking you through how to manage wallet connection using Mintbase-js.\
\
We currently support a stable version only on Next.js, soon we plan to give support to more libraries and frameworks.\
\
We strong recommend that you use the first method and build on top of our [examples repo](https://github.com/Mintbase/starter).\
\
Also recommend the read of [@mintbase-js/react ](https://docs.mintbase.xyz/dev/mintbase-sdk-ref/react)documentation

## First Method: Clone the examples repo

You can easily test Mintbase Wallet, using our Simple Login example with Next.js 14 on this repository:\
\
[https://github.com/Mintbase/starter](https://github.com/Mintbase/starter) , just do a `pnpm install` on the next-js folder and `pnpm run dev` any issues or troubleshooting help you can send us a message on our Telegram Channel

##

## Second Method: Install yourself

## Step 1: Install

Install the mintbase-js react package\
\
`npm install @mintbase-js/react`\
\
or\
\
yarn `install @mintbase-js/react`

## Step 2: Add Mintbase Wallet Context Provider

Add the `WalletContextProvider` to the root entry point of your app.

\
The below example shows how to do this on a Next.js app but the idea is the same. For React the equivalent should be done in the index.js file.

```typescript
import { MintbaseWalletContextProvider } from '@mintbase-js/react'
import '@near-wallet-selector/modal-ui/styles.css';
import type { AppProps } from 'next/app'

export default function App({ Component, pageProps }: AppProps) {
  return (
<MintbaseWalletContextProvider
contractAddress="mycontract.mintbase1.near"
network="mainnet"
callbackUrl="https://www.mywebsite.com/callback">
   <Component {...pageProps} />
</MintbaseWalletContextProvider>)
}

```

\
Step 3: Create a Wallet Connection Component
--------------------------------------------

Import use wallet and use it to get the necessary functions.

Use the connect method to provide the wallet selector UI where you can select which wallets to connect with.

Once the wallet is connected the activeAccountId will be populated

```typescript

"use client"
import { useMbWallet } from "@mintbase-js/react";

export const NearWalletConnector = () => {
  const { isConnected, selector, connect , activeAccountId } = useMbWallet();

  const handleSignout = async () => {
    const wallet = await selector.wallet();
    return wallet.signOut();
  };

  const handleSignIn = async () => {
    return connect();
  };

 if (!isConnected) {
    return <button className="bg-white text-black rounded p-3 hover:bg-[#e1e1e1]" onClick={handleSignIn}>Connect To NEAR</button>;
  }

  return (
    <div>
      <p>You are connected as {activeAccountId}</p>
      <div className="flex justify-center items-center mt-4">
        <button className="bg-white text-black rounded p-3 hover:bg-[#e1e1e1]" onClick={handleSignout}> Disconnect </button>
      </div>
    </div>
  );
};


```

\
Step 4: Use the Wallet Connection to Execute Contract Calls
-----------------------------------------------------------

Now that the wallet has been connected it is possible to access these props anywhere in the app through the `useWallet()`method.

With selector.wallet() it's possible to get the current wallet instance and use it to execute [Mintbase JS SDK methods ](../../mintbase-sdk-ref/packages/sdk/)to interact with smart contracts.

```typescript
const {
    connect,
    disconnect,
    activeAccountId,
    selector,
    isConnected,
    errorMessage,
  } = useMbWallet();

  const signTxn = async () => {
  const wallet = await selector.wallet();
  // ... call mintbase SDK methods with wallet as signingOption arg
  }
```

For more information on how to execute methods like transfer, mint on your very own token contracts deployed via our deployContract method or on how to list and buy from the mintbase market contracts check out the [Make Your First Contract Call](make-your-first-contract-call-deploycontract.md) guide.



## Join Us and Build the Future

Have feedback or perhaps need a hand? **Reach out on our** [**Telegram**](https://t.me/mintdev) **public developer support channel where we are happy to help!**

Building something cool? **Consider** [**applying for a grant**](https://github.com/Mintbase/Grants-Program)**.**\\

\\
