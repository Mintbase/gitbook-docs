# 📊 GraphQL Indexer

This is our preferred option as it is probably the most flexible option and allows an easy schema exploration.

### Endpoints

<table><thead><tr><th width="249.57142857142856">Network</th><th>Endpoint</th></tr></thead><tbody><tr><td>mainnet</td><td><mark style="color:green;">https://graph.mintbase.xyz/mainnet</mark></td></tr><tr><td>testnet</td><td><mark style="color:orange;">https://graph.mintbase.xyz/testnet</mark></td></tr></tbody></table>

### Use GraphiQL

<figure><img src="../../.gitbook/assets/Screen Shot 2022-11-08 at 4.44.15 PM.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="249.57142857142856">Network</th><th>URL</th></tr></thead><tbody><tr><td>mainnet<a href="https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-mainnet.hasura.app%2Fv1%2Fgraphql"><br></a><br></td><td><a href="https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Fgraph.mintbase.xyz%2Fmainnet&#x26;header=mb-api-key:anon">https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Fgraph.mintbase.xyz%2Fmainnet&#x26;header=mb-api-key:anon</a></td></tr><tr><td>testnet</td><td><a href="https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Fgraph.mintbase.xyz%2Ftestnet&#x26;header=mb-api-key:anon"><mark style="color:orange;">https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Fgraph.mintbase.xyz%2Ftestnet&#x26;header=mb-api-key:anon</mark></a></td></tr></tbody></table>



The queries and relationships are extensible, we suggest just clicking around the tree to make the queries and it will become easy over time.&#x20;

### API Key

In the future, users may be required to register using an api key. For now, simply passing the value`anon` for `mb-api-key` will work: e.g.

```bash

curl --location --request POST 'https://graph.mintbase.xyz' \
--header 'mb-api-key: anon' \
--header 'Content-Type: application/json' \
--data-raw '{"query":"query blocks {\n    blocks {\n        synced_height\n    }\n}","variables":{}}'

```



### Examples

1. [Get NFTs owned by an account,](https://t.ly/9gtj) notice the `burned_timestamp` if null indicates it has not been burned yet
2. [Get Metadata from token reference](https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Fgraph.mintbase.xyz%2Fmainnet\&header=mb-api-key%3Aanon\&query=query+MyQuery+%7B%0A++nft\_metadata%28%0A++++where%3A+%7Breference%3A+%7B\_eq%3A+%22nb0-oBR379DzoFYeYv-LesjVNmrVlDs5IqQ8hfDfnMU%22%7D%7D%0A++%29+%7B%0A++++id%0A++++media%0A++++reference\_blob%0A++%7D%0A%7D%0A) including title, media, documents, sound, 3d.
3. [Get unburned tokens on a contract](https://shorturl.at/dqxFS)



{% embed url="https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Fgraph.mintbase.xyz%2Fmainnet&header=mb-api-key%3Aanon&query=query+MyQuery+%7B%0A++mb_views_nft_tokens%28%0A++++where%3A+%7Bowner%3A+%7B_eq%3A+%22nate.near%22%7D%2C+_and%3A+%7Bburned_timestamp%3A+%7B_is_null%3A+true%7D%2C+last_transfer_timestamp%3A+%7B_is_null%3A+false%7D%7D%7D%0A++++limit%3A+30%0A++++order_by%3A+%7Blast_transfer_timestamp%3A+desc%7D%0A++%29+%7B%0A++++nft_contract_id%0A++++title%0A++++description%0A++++media%0A++++last_transfer_receipt_id%0A++%7D%0A%7D%0A" %}





###

### Query Formatting

Find all the different entities and parameters for interacting with the API.

#### Core Entities

* `nft_tokens`: Gets data on single tokens
* `mb_views_nft_metadata_unburned`: The token type (metadata wrapper)
* `nft_metadata`: Indexed metadata
* `nft_contracts`: Stores/contracts deployed
* `nft_listings`: Marketplace listings
* `offers`: Offers made to market listings
* `mb_store_minters`: Allowed mintings accounts&#x20;
* `nft_earnings`: Historical earnings per account



#### Aggregated Entities

...

#### Query Parameters

...

#### Pagination Parameters

`offset`: position where it should start the results ex:\
&#x20;`offset : 12` \
&#x20; it will render results from 12 > \


### Query Examples

#### GetTokenById

Query to retrieve a specific nft/Token

you need tokenId , and contractAddress\
**ex:**\
tokenId: 137\
contract Address: voiceoftheoceans.mintbase1.near\


{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-gettokenbyid" %}



####

#### GetStoreNfts

{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-getstorenfts" %}

#### `GetStoreDataById`

{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-getstoredatabyid" %}

\
**`GetRoyaltiesInfo`**

{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-getroyaltiesinfo" %}

\
**`GetTokensSplitbyMetadataId`**

{% embed url="https://gist.github.com/rubenmarcus/1ea704327c252f198eef7fc6d9eebecd#file-gettokenssplitbymetadataid" %}

### Demo

<figure><img src="../../.gitbook/assets/Screen Shot 2022-09-09 at 15.51.12.png" alt=""><figcaption></figcaption></figure>
