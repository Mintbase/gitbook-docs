# 📂 Add wallet connection to your react app

This a quick guide walking you through how to manage wallet connection using Mintbase-js.

## Step 1: Install

Install the mintbase-js react package\
\
`npm install @mintbase-js/react` \
\
or\
\
yarn `install @mintbase-js/react`&#x20;

## Step 2: Add Wallet Context Provider

Add the `WalletContextProvider` to the root entry point of your app.

\
The below example shows how to do this on a Next.js app but the idea is the same. For React the equivalent should be done in the index.js file.

```typescript
import { WalletContextProvider } from '@mintbase-js/react'
import '@near-wallet-selector/modal-ui/styles.css';
import type { AppProps } from 'next/app'

export default function App({ Component, pageProps }: AppProps) {
  return (
  <WalletContextProvider>  
    <Component {...pageProps} />
  </WalletContextProvider>)
}

```

\
Step 3: Create a Wallet Connection Component
--------------------------------------------

Import use wallet and use it to get the necessary functions.

Use the connect method to provide the wallet selector UI where you can select which wallets to connect with.

Once the wallet is connected the activeAccountId will be populated

```typescript
import { useWallet } from  '@mintbase-js/react'

const  NearWalletConnector = () => {
  const {
    connect,
    disconnect,
    activeAccountId,
    selector,
    isConnected,
    errorMessage,
  } = useWallet();


  if (!isConnected) {
    return <button  onClick={connect}>Connect To NEAR</button>
  }

  return (
    <div>
      <p>You are connected as {activeAccountId}</p>
      <button  onClick={disconnect}>Disconnect</button>
    </div>
  )
}
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
  } = useWallet();

  const  signTxn = async () => {
  const  wallet = await selector.wallet();
  // ... call mintbase SDK methods with wallet as signingOption arg
  }
```

For more information on how to execute methods like transfer, mint on your very own token contracts deployed via our deployContract method or on how to list and buy from the mintbase market contracts check out the [Make Your First Contract Call](make-your-first-contract-call-deploycontract.md) guide.



## Join Us and Build the Future

Have feedback or perhaps need a hand? **Reach out on our** [**Telegram**](https://t.me/mintdev) **public developer support channel where we are happy to help!**

Building something cool? **Consider** [**applying for a grant**](https://github.com/Mintbase/Grants-Program)**.**\






\


