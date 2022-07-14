# Store management

## Managing minters

```ts
// change methods
function batch_change_minters(grant: Array<string>, revoke: Array<string>);

// view methods
function check_is_minter(account_id: string): boolean;
function list_minters(): Array<string>;
```

While `batch_change_minters` allows you to grant and/or revoke minting rights of
multiple accounts at the same time (requiring the usual yoctoNEAR
authentication), `check_is_minter` allows you to check if a specific NEAR
account is a minter on the NFT contract, while `list_minters` returns a list of
currently allowed minters. The owner of a store cannot be revoked from minting.

## Transferring ownership of your store

```ts
function transfer_store_ownership(new_owner: string, keep_old_minters: boolean);
```

If you decide you want to get rid of your NFT contract, e.g. to benefit a friend
or to transfer it to a DAO, use `transfer_store_ownership`. The new owner will
be added to the minters, and minter retention may be toggled with
`keep_old_minters`.

To prevent fraud and people loosing NFTs they purchased, the deletion of a store
is not possible!
