# 💵 Affiliate Buys

When using the buy function on your own market, make sure to add your NEAR account to `affiliateAccount` This will give earn you 50% of our market fee. See [more in our SDK.](https://docs.mintbase.xyz/dev/mintbase-sdk-ref/sdk/buy#buy-args-buyargs-nearcontractcall)



```
export type BuyArgs = {
    // the price you want to buy a token for, this must be greater than the amount its currently listed for
    price: string;
    // contract to which the token belongs,
    //as an argument or through CONTRACT_ADDRESS env
    contractAddress?: string;
    // id of the token to be bought
    tokenId: string;
    // account that will receive the affiliate kick back (check affiliate documentation)
    affiliateAccount?: string;
    //address of the mintbase market contract, this defaults to the correct values depending on the NEAR_NETWORK environment variable
    marketId?: string;
  };
```

