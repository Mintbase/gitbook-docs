# 🖼 Get Blockchain Data (ownedTokens)

NEAR transaction events get stored by the Mintbase GraphQL Indexer making it easy for you to get the information you need.\
This page will guide you through getting the tokens that are owned by a specific user as an example.

There are 2 ways to retrieve data.

1. Calling the corresponding [data](../../mintbase-sdk-ref/packages/data/ "mention") method (alpha)
2. Making a GraphQL query

### Mintbase JS Data&#x20;

Getting data from this package is easier but is limited to the current methods available.

In this case, all you need to do is import the method and call it.\


```typescript
import { ownedTokens, OwnedTokens } from '@mintbase/data'

const ownedTokens: OwnedTokens[] = ownedTokens('mb_alice.near', { limit: 20 });

```

The documentation for the currently available methods can be referenced [here](../../mintbase-sdk-ref/packages/data/).



### GraphQL Indexer

This endpoint enables you to make GraphQL queries to our API.\
<mark style="color:green;">`https://interop-mainnet.hasura.app/v1/graphql`</mark>

You can try this and other queries on the[ Hasura Sandbox](https://cloud.hasura.io/public/graphiql?endpoint=https%3A%2F%2Finterop-mainnet.hasura.app%2Fv1%2Fgraphql)

**More examples and information on how to query all sorts of blockchain information can be found** [**here**](get-blockchain-data-ownedtokens.md#graphql-indexer)

```typescript
query ownedTokens {
  tokens: mb_views_nft_owned_tokens(
    where: {
      owner: { _eq: "INSERT_OWNER" }
    }
  
  ) {
    lastTransferredAt: last_transfer_timestamp
    tokenId: token_id
    contractId: nft_contract_id
    baseUri: base_uri
    metadataId: metadata_id
    title
    minter
    media
    document: reference_blob(path: "$.document")
    animationUrl: reference_blob(path: "$.animation_url")
  }
}
```

\
Join Us and Build the Future
----------------------------

Have feedback or perhaps need a hand? **Reach out on our** [**Telegram**](https://t.me/mintdev) **public developer support channel where we are happy to help!**

Building something cool? **Consider** [**applying for a grant**](https://github.com/Mintbase/Grants-Program)**.**\
