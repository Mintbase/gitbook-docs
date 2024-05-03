# Minting and burning

## Minting

On version 1 of the NFT contracts, metadata definition and minting happen in a single step:

* [Usage via MintbaseJS](https://github.com/Mintbase/mintbase-js/tree/beta/packages/sdk/src/mint)
* [Smart contract implementation](https://github.com/Mintbase/mb-contracts/blob/main/mb-nft-v1/src/minting.rs#L56)

On version 2 of the NFT contracts, metadata definition and minting are separated. This allows for more scalability when minting a high number of tokens by eliminating redundant storage deposits, and it comes with an array of configurability around the mint.

* [Metadata definition usage via MintbaseJS](https://github.com/Mintbase/mintbase-js/tree/beta/packages/sdk/src/createMetadata) (available to creators registered with the smart contract)
* [Metadata definition implementation](https://github.com/Mintbase/mb-contracts/blob/main/mb-nft-v2/src/minting.rs#L46)
* [Minting usage via MintbaseJS](https://github.com/Mintbase/mintbase-js/tree/beta/packages/sdk/src/mintOnMetadata) (available to anyone or predefined minters)
* [Minting implementation](https://github.com/Mintbase/mb-contracts/blob/main/mb-nft-v2/src/minting.rs#L148)

## Burning

To burn tokens, you can use the `nft_batch_burn` method:

```ts
function nft_batch_burn(token_ids: Array<string>);
```

This will remove the token from the on-chain storage! This means you can no longer use methods such as `nft_token` with this token ID, but storage requirements are being decreased by burning. To verify your identity, you are required to attach one yoctoNEAR to the method call.
