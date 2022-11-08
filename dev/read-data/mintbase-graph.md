# GraphQL

This is our preferred option as it is probably the most flexible option and allows an easy schema exploration.

### Endpoints

| Network | Endpoint                                                                         |
| ------- | -------------------------------------------------------------------------------- |
| mainnet | <mark style="color:green;">https://interop-mainnet.hasura.app/v1/graphql</mark>  |
| testnet | <mark style="color:orange;">https://interop-testnet.hasura.app/v1/graphql</mark> |

### Use GraphiQL

<figure><img src="../../.gitbook/assets/Screen Shot 2022-11-08 at 4.44.15 PM.png" alt=""><figcaption></figcaption></figure>

| Network                                                                                                                                       | URL                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>mainnet<a href="https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-mainnet.hasura.app%2Fv1%2Fgraphql"><br></a><br></p> | [https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-mainnet.hasura.app%2Fv1%2Fgraphql](https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-mainnet.hasura.app%2Fv1%2Fgraphql)                                                                                                          |
| testnet                                                                                                                                       | <mark style="color:orange;"></mark>[<mark style="color:orange;">https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-testnet.hasura.app%2Fv1%2Fgraphql</mark>](https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-testnet.hasura.app%2Fv1%2Fgraphql)<mark style="color:orange;"></mark> |



The queries and relationships are extensible, we suggest just clicking around the tree to make the queries and it will become easy over time.&#x20;

Always keep in mind our [data model](broken-reference) and [schema](broken-reference).\


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

``

#### Aggregated Entities

...

#### Query Parameters

...

#### Pagination Parameters

`offset`: position where it should start the results ex:\
&#x20;`offset : 12` \
&#x20; it will render results from 12 > \


### Query Examples

#### GetStoreNfts

{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-getstorenfts" %}

#### `GetStoreDataById`

{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-getstoredatabyid" %}

\
**`GetRoyaltiesInfo`**

{% embed url="https://gist.github.com/rubenmarcus/c781422542c19cfaca4bbc3a74ffad81#file-getroyaltiesinfo" %}

``\
``**`GetTokensSplitbyMetadataId`**

{% embed url="https://gist.github.com/rubenmarcus/1ea704327c252f198eef7fc6d9eebecd#file-gettokenssplitbymetadataid" %}

### Demo

<figure><img src="../../.gitbook/assets/Screen Shot 2022-09-09 at 15.51.12.png" alt=""><figcaption></figcaption></figure>
