# ⛓ NEAR CLI



### Install NEAR CLI ([https://github.com/near/near-cli](https://github.com/near/near-cli))

```
npm install -g near-cli
```

### Fetch token data from CLI <a href="#3.-fetch-token-data-from-cli" id="3.-fetch-token-data-from-cli"></a>

```
near view dip3.mintspace2.testnet  nft_tokens '{"from_index": "0", "limit": 10}'
```

### Get the NFTs owned by account <a href="#get-the-nfts-owned-by..." id="get-the-nfts-owned-by..."></a>

```
near view dip3.mintspace2.testnet  nft_tokens_for_owner '{"account_id":"testbase.testnet", "from_index": "0", "limit": 10}'
```
