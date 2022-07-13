---
description: Some queries to get user data from our SubGraph on IPFS
---

# Queries

Here are all the queries we use on [Mintbase](https://mintbase.io).  This is not an exhaustive list and you can do a whole lot more, but will get you started.

Remember a **Thing: metaId** (Like a cup of coffee NFT) is a batch parent of **tokens,** so a one thing can have several tokens to it. This just means all the tokens share the same metadata (a thing). You can always find the metaId at the end of the pez-dispenser url like this one batch of [dappcon](https://dappcon.io/) tickets `Q1c8y3PwYomxjW25sW3l`

{% embed url="https://mintbase.io/pez-dispenser/0x202d2f33449bf46d6d32ae7644ada130876461a4/Q1c8y3PwYomxjW25sW3l" %}

![](<../../../.gitbook/assets/Screen Shot 2020-04-08 at 10.26.49 AM.png>)

{% embed url="https://thegraph.com/explorer/subgraph/nategeier/mintbase" %}

{% code title="" %}
```typescript
import { gql } from "apollo-boost";


export const GET_MODS = gql`
  query tokens($id: String!, $token: String!) {
    tokens(where: { metaId: $token, resolveOwner: $id }) {
      id
    }
  }
`;

export const GET_ALL_STORES = gql`
  query stores($more: Int!) {
    stores(first: $more, where: { burned: false }) {
      id
      name
      burned
      owner
      things(first: 1) {
        metaId
      }
    }
  }
`;

export const GET_STORES = gql`
  query user($id: String!, $approver: String!) {
    stores(where: { burned: false, owner: $id }) {
      id
      name
      burned
      boughtCount
      valueCount
      transferCount
      tokenCount
      approvers(id: $approver) {
        id
      }
    }
  }
`;

export const GET_STORE = gql`
  query store($id: String!) {
    store(id: $id, where: { burned: false }) {
      id
      name
      symbol
      totalSupply
      things(where: { burned: false }) {
        id
        burned
        forSale
        metaId
        tokens {
          id
          price
          state
          tokenId
        }
      }
    }
  }
`;

// Simply remove metaId if you just want to know if a user owns a  single token 
// from a contract
export const HAS_THING_FROM_STORE = gql`
  query tokens($ownerId: String!, $metaId: String!, $storeId: String!) {
    tokens(
      where: { metaId: $metaId, store: $storeId, resolveOwner: $ownerId }
    ) {
      id
    }
  }
`;

export const GET_STORE_BASIC = gql`
  query store($id: String!, $approver: String!) {
    store(id: $id, where: { burned: false }) {
      id
      name
      symbol
      approvers(id: $approver) {
        id
      }
    }
  }
`;

export const GET_ONE_STORE = gql`
  query store($id: String!) {
    store(id: $id, where: { burned: false }) {
      id
      name
      symbol
      totalSupply
      things(where: { burned: false }) {
        id
        burned
        forSale
        metaId
        tokens {
          id
          price
          state
          tokenId
        }
      }
    }
  }
`;

export const GET_USER_TOKENS = gql`
  query tokens($userId: String!, $store: String!) {
    tokens(where: { resolveOwner: $userId, store: $store, burned: false }) {
      id
      tokenId
      metaId
      state
    }
  }
`;

export const GET_THINGS = gql`
  query store($id: String!) {
    store(id: $id) {
      id
      name
      symbol
      totalSupply
      things(where: { burned: false }) {
        id
        burned
        forSale
        metaId
        tokens {
          id
          price
          state
          tokenId
        }
      }
    }
  }
`;

export const HAS_THING = gql`
  query store($ownerId: String!, $metaId: String!) {
    tokens(where: { resolveOwner: $ownerId, metaId: $metaId }) {
      id
    }
  }
`;

export const GET_THING = gql`
  query thing($metaId: String!) {
    thing(id: $metaId) {
      id
      burned
      forSale
      metaId
      minter
      tokens {
        id
        price
        state
        tokenId
      }
    }
  }
`;

export const GET_USER_THINGS = gql`
  query user($account: String!) {
    user(id: $account) {
      id
      tokens(first: 700) {
        id
        metaId
        state
        price
        tokenId
        burned
        store {
          id
          burned
        }
      }
    }
  }
`;

export const GET_USER_STORE = gql`
  query getStore($id: String!) {
    user(id: $id) {
      stores(where: { burned: false }) {
        id
        burned
      }
    }
  }
`;


```
{% endcode %}
