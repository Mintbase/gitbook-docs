## Batch transfers

To simplify sending lots of tokens to different people, e.g. to do airdrops, we
define `nft_batch_transfer`:

```ts
function nft_batch_transfer(token_ids: Array<[string, string]>);
```

The first string is the token ID (must always parse to a `u64`), and then second
string must be a valid NEAR account. This is not currently hardcapped, but will
fail if you run out of gas while doing so. As with `nft_transfer`, you will need
to deposit one yoctoNEAR to prove your identity to the contract.

## Batch approvals

To simply listing lots of tokens on a market (or any other usecase you may come
up with), we define `nft_batch_approve`:

```ts
function nft_batch_approve(
  token_ids: Array<string>,
  account_id: string,
  msg: string | null
);
```

As with `nft_approve`, you will need to deposit one yoctoNEAR to prove your
identity to the contract.
