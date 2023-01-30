# simple-marketplace

This guide will take you step by step through the process of creating a basic marketplace where you can purchase tokens and filter your selection by store, using the [Mintbase JS SDK](../../mintbase-sdk-ref/packages/sdk/) and [Mintbase JS Data](../../mintbase-sdk-ref/packages/data/) package.

The mintbase-js/data package provides convenient functions for retrieving data from our indexer. &#x20;

In this example, you will be able to view and purchase NFTs from a specific store.

You can find more information on Github: [https://github.com/Mintbase/examples/tree/main/simple-marketplace](https://github.com/Mintbase/examples/tree/main/simple-marketplace). \
A live demo of the marketplace can be found here: [https://examples-simple-marketplace.vercel.app/](https://examples-simple-marketplace.vercel.app/)

### Step 1: Connect wallet

Before proceeding, it is important to have a wallet connection feature implemented in your application in order to interact with the contract. To do this, you can check our guide [Add wallet connection to your react app](../getting-started/add-wallet-connection-to-your-react-app.md).

### Step 2: Get nfts from store

In this example, we utilized react-query to manage the loading state when retrieving NFTs from the contract via the `storeNfts` method. \
This method returns all NFTs from the specified contract, allowing you to display them in the user interface.

```typescript
import { ParsedDataReturn, storeNfts } from '@mintbase-js/data';
import { StoreNftsResult } from '@mintbase-js/data/lib/api/storeNfts/storeNfts.types';
import { useQuery } from 'react-query';
import { MAINNET_CONFIG } from '../config/constants';

const mapStoreNfts = (data: ParsedDataReturn<StoreNftsResult>) => ({
  nftsData: data?.data?.mb_views_nft_metadata_unburned,
});

const useStoreNfts = (store?: string) => {
  const defaultStores = process.env.NEXT_PUBLIC_STORES || MAINNET_CONFIG.stores;

  const formatedStores = defaultStores.split(/[ ,]+/);

  const {
    isLoading,
    error,
    data,
  } = useQuery(['storeNfts', store], () => storeNfts(store || formatedStores, true), {
    retry: false,
    refetchOnWindowFocus: false,
    select: mapStoreNfts,
  });

  return { ...data, error, loading: isLoading };
};

export { useStoreNfts };
```

In this example, we retrieve the information for the NFTs using the `storeNfts` method in the `Items.tsx` component.

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-24 at 11.20.42.png" alt=""><figcaption></figcaption></figure>

```typescript
import {
  EIconName,
  MbDropdownMenu,
  MbIcon,
  MbMenuWrapper,
  MbTab,
} from 'mintbase-ui';
import { useState } from 'react';
import { useStoreData } from '../hooks/useStoreData';
import { useStoreNfts } from '../hooks/useStoreNfts';
import { SelectedNft, Store } from '../types/types';
import { Item, LoadingItem } from './Item';

function Items({
  showModal,
}: {
  showModal: (item: SelectedNft) => void
}): JSX.Element {
  const [menuOpen, setMenuOpen] = useState(false);
  const [selectedStore, setSelectedStore] = useState('');

  const { nftsData, loading } = useStoreNfts(selectedStore);
  const { stores } = useStoreData();

  // show store names in the dropdown menu
  const storeTabs = stores?.map((store: Store) => ({
    content: <span>{store.name}</span>,
    onClick: () => setSelectedStore(store.id),
  }));

  // add 'all stores' to the beginning of the dropdown menu
  storeTabs?.unshift({
    content: <span>All Stores</span>,
    onClick: () => setSelectedStore(''),
  });

  return (
    <div className="w-full items-center p-12">
      <div className="flex w-full gap-4 items-center justify-end">
        <MbMenuWrapper setIsOpen={setMenuOpen}>
          <div
            onClick={() => setMenuOpen(!menuOpen)}
            onKeyDown={() => setMenuOpen(!menuOpen)}
            role="button"
            tabIndex={-1}
          >
            <MbTab
              label={(
                <div className="flex space-x-8 items-center">
                  <span>
                    {selectedStore === ''
                      ? 'All Stores'
                      : stores?.find(
                        (store: Store) => store.id === selectedStore,
                      )?.name}
                  </span>
                  <div className="pointer-events-none">
                    <MbIcon
                      name={
                        menuOpen
                          ? EIconName.ARROW_DROP_UP
                          : EIconName.ARROW_DROP_DOWN
                      }
                      size="16px"
                      color="blue-300"
                      darkColor="blue-100"
                    />
                  </div>
                </div>
              )}
              isSmall
            />
          </div>
          <MbDropdownMenu
            items={storeTabs}
            isOpen={menuOpen}
            className="mt-2"
          />
        </MbMenuWrapper>
      </div>

      {/** grid */}
      <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 2xl:grid-cols-5 gap-4 my-12">
        {loading ? (
          <LoadingItem />
        ) : (
          nftsData?.map((nft) => (
            <Item key={nft.metadata_id} item={nft} showModal={showModal} />
          ))
        )}
      </div>
    </div>
  );
}

export default Items;
```

By utilizing react-query, we can take advantage of the loading state to display a loading indicator while data is being retrieved.

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-24 at 11.26.51.png" alt=""><figcaption></figcaption></figure>

You can read more about the `storeNfts` method [here](../../mintbase-sdk-ref/packages/data/src/api/storeNfts/).\


### Step 3: Get store data

To control the tabs, we need to retrieve store data using the `storeData` method. \
This method returns the data from the specified contract, enabling you to display it in the user interface.

```typescript
import { ParsedDataReturn, storeData } from '@mintbase-js/data';
import { StoreDataResults } from '@mintbase-js/data/lib/api/storeData/storeData.types';
import { useQuery } from 'react-query';
import { MAINNET_CONFIG } from '../config/constants';

const mapStoreData = (data: ParsedDataReturn<StoreDataResults>) => ({
  stores: data?.data?.nft_contracts,
});

const useStoreData = () => {
  const defaultStores = process.env.NEXT_PUBLIC_STORES || MAINNET_CONFIG.stores;

  const formatedStores = defaultStores.split(/[ ,]+/);

  const { isLoading, error, data } = useQuery(
    'storeData',
    () => storeData(formatedStores),
    {
      retry: false,
      refetchOnWindowFocus: false,
      select: mapStoreData,
    },
  );

  return {
    ...data,
    error,
    loading: isLoading,
  };
};

export { useStoreData };
```

To handle selecting the current store, we update the `storeData` with the selected store in order to retrieve the corresponding NFTs.

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-24 at 11.43.34.png" alt=""><figcaption></figcaption></figure>

You can read more about the `storeData` method [here](../../mintbase-sdk-ref/packages/data/src/api/storeData/).\


### Step 4: Get metadata from an nft

To display NFT pricing information, available quantities, and other details in the user interface, it is necessary to access the NFT metadata using the `metadataByMetadataId` method.

You can find more metadata information in our [metadata guide](../read-data/metadata.md).

```typescript
import { metadataByMetadataId, ParsedDataReturn } from '@mintbase-js/data';
import { MetadataByMetadataIdQueryResult } from '@mintbase-js/data/lib/api/metadataByMetadataId/metadataByMetadataId.types';
import { useQuery } from 'react-query';
import { parseYactoToNear } from '../lib/numbers';
import { SelectedNft, TokenListData } from '../types/types';

const mapMetadata = (
  metadata: ParsedDataReturn<MetadataByMetadataIdQueryResult>,
): Partial<TokenListData> => {
  const firstListing = metadata?.data?.listings[0];

  if (!firstListing || firstListing === null) {
    return {
      amountAvailable: 0,
      tokensTotal: 0,
      price: 0,
      tokenId: null,
    };
  }

  const { price } = firstListing;

  const prices = metadata?.data?.listings.map((elm) => ({
    price: elm.price,
    tokenId: elm.token.token_id,
  }));

  return {
    amountAvailable: metadata?.data?.simpleSaleCount.aggregate.count,
    tokensTotal: metadata?.data?.tokenCount.aggregate.count,
    price: price ? parseYactoToNear(price) : 0,
    tokenId: firstListing.token.token_id,
    prices: prices.length > 0 ? prices : [],
    nftContractId: firstListing.token.nft_contract_id,
    marketId: firstListing.market_id,
  };
};

const useMetadataByMetadataId = ({
  metadataId,
}: SelectedNft): Partial<TokenListData> => {
  const {
    isLoading,
    data: metadata,
  } = useQuery('metadataByMetadataId', () => metadataByMetadataId(metadataId), {
    retry: false,
    refetchOnWindowFocus: false,
    select: mapMetadata,
  });

  return { ...metadata, isTokenListLoading: isLoading };
};

export { useMetadataByMetadataId };
```

This information is displayed in a pop-up window after clicking on the NFT card.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-01-24 at 11.47.29.png" alt=""><figcaption></figcaption></figure>

You can read more about the `metadataByMetadataId` method [here](../../mintbase-sdk-ref/packages/data/src/api/metadataByMetadataId/).\


### Step 5: Get current near price

To obtain the current price of the NFT in USD, it is necessary to retrieve the current Near price. We accomplish this by using the `nearPrice` method.

```typescript
import { nearPrice } from '@mintbase-js/data';
import { useEffect, useState } from 'react';

const useNearPrice = (): string => {
  const [nearPriceData, setNearPriceData] = useState<string>('0');

  useEffect(() => {
    const getNearPrice = async () => {
      const { data: priceData, error } = await nearPrice();

      setNearPriceData(error ? '0' : priceData);
    };

    getNearPrice();
  }, []);

  return nearPriceData;
};

export { useNearPrice };

```

You can read more about the `nearPrice` method [here](../../mintbase-sdk-ref/packages/data/src/api/nearPrice/).

### Step 6: Execute the contract call - buy

The `execute` method accepts one or more contract call objects and executes them using a specified wallet instance. \
In this example, we need to use the `execute` method to execute the "buy" call, allowing the user to purchase the desired NFT.

```typescript
import { useCallback, useState } from 'react';
import { MAINNET_CONFIG } from '../../config/constants';
import { useNearPrice } from '../../hooks/useNearPrice';
import { nearToYocto } from '../../lib/numbers';
import { TokenListData, TransactionEnum } from '../../types/types';
import { SignInButton } from '../SignInButton';

function AvailableNftComponent({
  data,
}: {
  data: Partial<TokenListData>
}): JSX.Element {
  const {
    amountAvailable,
    marketId,
    nftContractId,
    price,
    tokenId,
    tokensTotal,
    isTokenListLoading,
  } = data;

  const { selector, isConnected } = useWallet();

  const message = `${amountAvailable} of ${tokensTotal} Available`;
  // state to check the price x amount according to user interaction

  const [currentPrice, setCurrentPrice] = useState(price);
  const [amount, setAmount] = useState(1);

  const nearPrice = useNearPrice();
  const router = useRouter();

  const singleBuy = useCallback(async () => {
    const wallet = await selector.wallet();

    const receipt = await execute(
      { wallet },
      {
        ...buy({
          contractAddress: nftContractId,
          tokenId,
          affiliateAccount: 
            process.env.NEXT_PUBLIC_AFFILIATE_ACCOUNT 
            || MAINNET_CONFIG.affiliate,
          marketId,
          price: nearToYocto(currentPrice.toString()),
        }),
      },
    ) as FinalExecutionOutcome;

    const callback = `${
      window.location.origin
    }/wallet-callback?transactionHashes=${receipt?.transaction_outcome?.id}&signMeta=${encodeURIComponent(
      JSON.stringify({
        type: TransactionEnum.MAKE_OFFER,
        args: {
          tokenId,
          price: nearToYocto(currentPrice.toString()),
        },
      }),
    )}`;

    router.push(callback);
  }, [currentPrice]);

  // handler function to call the wallet methods to proceed the buy.
  const handleBuy = async () => {
    const isSingleAmount = amount === 1;

    if (isSingleAmount) {
      await singleBuy();
    }
  };

  const setNewPrice = (val: string) => {
    const value = Number(val);

    setAmount(value);
    setCurrentPrice(price * value);
  };

  return isConnected && !isTokenListLoading ? (
    <div className="mt-2">
      <div className="bg-gray-50 py-4 text-center">
        <MbText className="p-med-90 text-gray-700">
          <span className="p-med-130 text-black">{message}</span>
        </MbText>
      </div>
      <div className="py-2">
        <div className="mb-8">
          <MbInfoCard
            boxInfo={{
              description: `${currentPrice.toFixed(2)} N`,
              title: 'Price',
              lowerLeftText: `~ ${(
                Number(nearPrice) * Number(currentPrice)
              ).toFixed(2)} USD`,
            }}
          />
          <div className="mt-4">
            <MbText className="text-gray-700 mb-2">Quantity</MbText>
            <MbAmountInput
              maxAmount={Math.min(amountAvailable, 1)}
              onValueChange={(e) => {
                setNewPrice(e);
              }}
              disabled={amountAvailable === 1}
            />
          </div>
        </div>
        <div className="text-center">
          <MbButton
            label="Buy with NEAR"
            state={EState.ACTIVE}
            onClick={handleBuy}
          />
        </div>
      </div>
    </div>
  ) : (
    <SignInButton />
  );
}
```

You can read more about the buy call [here](../../mintbase-sdk-ref/packages/sdk/src/buy/).
