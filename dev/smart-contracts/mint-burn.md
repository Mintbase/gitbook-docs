# Minting and burning

## Minting

To mint tokens, you can use the `nft_batch_mint` method:

```ts
function nft_batch_mint(
  owner_id: string,
  metadata: TokenMetadata,
  num_to_mint: number,
  royalty_args: RoyaltyArgs | null,
  split_owners: PayoutsMap | null
);

type PayoutsMap = Record<string, number>;
type RoyaltyArgs = {
  split_between: PayoutsMap;
  percentage: number;
};
```

- To learn more about `TokenMetadata`, refer to the
  [corresponding standard](https://nomicon.io/Standards/Tokens/NonFungibleToken/Metadata#interface)
- Due to gas limitations, you cannot mint more than 125 tokens at once.
- The `PayoutsMap` maps from NEAR account IDs to percentages, where each
  percentage is expressed as an integer between 0 and 10000 (inclusive), where
  10000 is equivalent to 100%
- As with the `PaymoutsMap`, the `percentage` in `RoyaltyArgs` is expressed as a
  number between 0 and 10000
- Any allowed minter can call this, once they have verified their identity by
  attaching at least one yoctoNEAR to this method call. You may wish to attach
  more to cover required storage deposits, as minting increases storage
  requirements for the contract. The method will not check if sufficient
  deposits have been made, and it is the responsibility of the store owner and
  minters to keep their smart contracts sufficiently funded!

## Burning

To burn tokens, you can use the `nft_batch_burn` method:

```ts
function nft_batch_burn(token_ids: Array<string>);
```

This will remove the token from the on-chain storage! This means you can no
longer use methos such as `nft_token` with this token ID, but storage
requirements are being decreased by burning. To verify your identity, you are
required to attach one yoctoNEAR to the method call.
