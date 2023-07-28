---
description: How to programmatically delist NFTs from our marketplace
---

# (Un) Delisting NFTs

**You can also do this using the mintbase.xyz Launchpad UI by following** [**these instructions**](../../../creator/selling-nfts/relisting-or-remove-listing.md)

Using the CLI, you can call the Mintbase simple market contract to remove listings programmatically:

1. Export variables for near env (mainnet or testnet), your \*.mintbase1.near contract address and account. Note the list of tokens must be a comma delimited list of strings wrapped in double quotes "".

```shell
$ export NEAR_ENV="mainnet"
$ export TOKEN_CONTRACT_ACCOUNT="example.mintbase1.near"
$ export OWNER_ACCCOUNT="myaccount.near"
$ export TOKENS_TO_UNLIST='"11","12"'
```

2\. Run the following command (**You will have to be authenticated as the OWNER\_ACCOUNT for this to work)**

{% code overflow="wrap" lineNumbers="true" %}
```shell
near call simple.market.mintbase1.near unlist "{\"nft_contract_id\":\"${TOKEN_CONTRACT_ACCOUNT}\", \"token_ids\":[${TOKENS_TO_UNLIST}]}" --accountId=$TOKEN_CONTRACT_OWNER --depositYocto=1
```
{% endcode %}
