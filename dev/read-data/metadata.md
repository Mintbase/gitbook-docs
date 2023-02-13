---
description: Describe your NFT to the world using reference JSON
---

# 🗺 Metadata

### Metadata On-Chain  vs. Reference JSON Off-Chain

Metadata is responsible for describing the properties of your token. A set of standard fields allow for on-chain metadata storage, however a more efficient and robust means of expressing the properties including attributes further documentation and more lives **off-chain in a reference.**

_Looking for a quick example of reference JSON? ****_ [Skip to the example.](metadata.md#full-example-of-nft-reference-data-with-media-title-attributes-and-tags)

The **reference** field is where the URL reference to this JSON document will be stored. This field's value is passed to the [mint transaction](../../mintbase-sdk-ref/packages/sdk/src/mint/) before the NFT is created on the blockchain.

Here are the on-chain options for token metadata provided by the NEAR[ NEP-177](https://nomicon.io/Standards/Tokens/NonFungibleToken/Metadata#nep-177) standard:&#x20;

```
type TokenMetadata = {
  title: string|null, // ex. "Arch Nemesis: Mail Carrier" or "Parcel #5055"
  description: string|null, // free-form description
  media: string|null, // URL to associated media, preferably to decentralized, content-addressed storage
  media_hash: string|null, // Base64-encoded sha256 hash of content referenced by the `media` field. Required if `media` is included.
  copies: number|null, // number of copies of this set of metadata in existence when token was minted.
  issued_at: number|null, // When token was issued or minted, Unix epoch in milliseconds
  expires_at: number|null, // When token expires, Unix epoch in milliseconds
  starts_at: number|null, // When token starts being valid, Unix epoch in milliseconds
  updated_at: number|null, // When token was last updated, Unix epoch in milliseconds
  extra: string|null, // anything extra the NFT wants to store on-chain. Can be stringified JSON.
  reference: string|null, // URL to an off-chain JSON file with more info.
  reference_hash: string|null // Base64-encoded sha256 hash of JSON from reference field. Required if `reference` is included.
}
```

Mintbase prefers to store reference JSON on [Arweave](https://www.arweave.org/), a permanent, cheap, and decentralized storage platform. &#x20;

The following video walks through how to find metadata for an existing token:

{% embed url="https://www.loom.com/share/cd3efad270314784aa750ca5003f21c3" %}

![An example of tickets to NEAR conference in 2022](<../../.gitbook/assets/Screenshot 2022-07-07 at 10.56.14.png>)

### Get token metadata using NEAR cli

If you are using the [NEAR CLI](https://github.com/near/near-cli) via command line on mainnet, you can see that Mintbase tokens will only return the reference field from metadata:

```
export NEAR_ENV=mainnet
near view nearcon2.mintbase1.near nft_token '{"token_id": "204"}'
```

**Returns**

```
{
  token_id: '30',
  owner_id: 'nearcon2.near',
  approved_account_ids: { 'market.mintbase1.near': 10 },
  metadata: {
    title: null,
    description: null,
    media: null,
    media_hash: null,
    copies: 20,
    issued_at: null,
    expires_at: null,
    starts_at: null,
    updated_at: null,
    extra: 'ticket',
    reference: 'dfnswq0LaXwNgGzqdW0-YPJLtTxc-fhQlLk8k1UCcJw',
    // New Contracts have the full url to fetch the metadata so might look like
    // reference: 'https://arweave.net/dfnswq0LaXwNgGzqdW0-YPJLtTxc-fhQlLk8k1UCcJw',
    reference_hash: null
  },
  royalty: {
    split_between: {
      'nearcon2.near': { numerator: 6000 },
      'unchain-fund.sputnik-dao.near': { numerator: 4000 }
    },
    percentage: { numerator: 5000 }
  },
  split_owners: null,
  minter: 'nearcon2.near',
  loan: null,
  composeable_stats: { local_depth: 0, cross_contract_children: 0 },
  origin_key: null
}
```

The reference field, in this case `dfnswq0LaXwNgGzqdW0-YPJLtTxc-fhQlLk8k1UCcJw` is a hash on the Arweave network. So, constructing the following URL and requesting it over https:

{% embed url="https://arweave.net/dfnswq0LaXwNgGzqdW0-YPJLtTxc-fhQlLk8k1UCcJw" %}
The full Arweve URL with refernce field (hash)
{% endembed %}

Results in the following...

### Full example of NFT reference data

```

  "media": "https://arweave.net/c2g92YvhcnbB5JBePIrK48uX5mPw6gcbhvfvabQkSGM",
  "media_hash": "c2g92YvhcnbB5JBePIrK48uX5mPw6gcbhvfvabQkSGM",
  "tags": [
    "nearcon"
  ],
  "title": "General Admission",
  "description": "The holder of this NFT will gain general admission entry to all days of NEARCON 2022. If you can't make this event, transfer it on to a colleague, sell it on secondary markets, hold an open Twitter contest (best answer gets this NFT), or even auction it off to the highest bidder. Welcome to the new world of fluid, borderless digital assets. On the day of NEARCON, please make sure it's on an easily accessible mobile account for redeeming. Checking in with a ledger is possible, but much quicker if you are already connected to a wallet.",
  "extra": [
    {
      "trait_type": "website",
      "display_type": "website",
      "value": "https://nearcon.org/"
    },
    {
      "trait_type": "Start Date",
      "value": 1662850800,
      "display_type": "date"
    },
    {
      "trait_type": "End Date",
      "value": 1663110000,
      "display_type": "date"
    },
    {
      "trait_type": "location",
      "value": "Cais da Viscondessa, 1200-109 Lisboa, Portugal"
    },
    {
      "trait_type": "place_id",
      "value": "ChIJKSi2xoQ0GQ0R2xH3l2OH5W0"
    },
    {
      "trait_type": "zoom",
      "value": 14
    },
    {
      "trait_type": "latitude",
      "value": 38.7053168
    },
    {
      "trait_type": "longitude",
      "value": -9.1549384
    },
    {
      "trait_type": "type",
      "display_type": "type",
      "value": "general_admissions"
    },
    {
      "trait_type": "access",
      "display_type": "access",
      "value": "daypass"
    },
    {
      "trait_type": "NEARCON",
      "display_type": "NEARCON",
      "value": "2"
    }
  ],
  "store": "nearcon2.mintbase1.near",
  "type": "NEP171",
  "category": "ticket"
}
```



### Get token Metadata via the UI

If we inspect our thing page:

{% embed url="https://www.mintbase.io/thing/nGr-c_UfzHr515RPqVJfQNdFV1Eivo0as2RGOo-2Z24:hellovirtualworld.mintbase1.near" %}

If you scroll down to **Details**, you'll see transaction hash

![](<../../.gitbook/assets/Screen Shot 2022-06-07 at 4.01.17 PM.png>)

Combine the Storage Gateway with Transaction Hash

{% embed url="https://arweave.net/nGr-c_UfzHr515RPqVJfQNdFV1Eivo0as2RGOo-2Z24" %}
&#x20;Arweave Metadata Source
{% endembed %}

```
{
  "category": "vr",
  "description": "Credits to Mozilla for creating this model",
  "copies": 1,
  "media_hash": "zRHjE6nUSHUN4YB3FWx__57EWNpIAOUenf4_gddCArg",
  "lock": null,
  "visibility": "safe",
  "youtube_url": null,
  "animation_url": "https://arweave.net/bUj-aADWZ1RV9Od4QYx-99oAOcVbvRcep3Fdg9OpCP8",
  "animation_hash": "bUj-aADWZ1RV9Od4QYx-99oAOcVbvRcep3Fdg9OpCP8",
  "document": null,
  "document_hash": null,
  "royalty": {
    "microchipgnu.near": 10000
  },
  "royalty_perc": 0.1,
  "split_revenue": {
    "3xr.near": 5000,
    "microchipgnu.near": 5000
  },
  "tags": [
    
  ],
  "media": "https://arweave.net/zRHjE6nUSHUN4YB3FWx__57EWNpIAOUenf4_gddCArg",
  "extra": [
    {
      "trait_type": "website",
      "value": ""
    },
    {
      "trait_type": "asset_places",
      "value": "[   {     \"position\": { \"x\": -5.6, \"y\": 1.5, \"z\": 5 },     \"rotation\": { \"_x\": 0, \"_y\": 1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -5.6, \"y\": 1.5, \"z\": 3 },     \"rotation\": { \"_x\": 0, \"_y\": 1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -5.6, \"y\": 1.5, \"z\": 1 },     \"rotation\": { \"_x\": 0, \"_y\": 1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -5.6, \"y\": 1.5, \"z\": -1 },     \"rotation\": { \"_x\": 0, \"_y\": 1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -5.6, \"y\": 1.5, \"z\": -3 },     \"rotation\": { \"_x\": 0, \"_y\": 1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 5, \"y\": 1.5, \"z\": 6.65 },     \"rotation\": { \"_x\": 0, \"_y\": 3.141592653589793, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 3, \"y\": 1.5, \"z\": 6.65 },     \"rotation\": { \"_x\": 0, \"_y\": 3.141592653589793, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 1, \"y\": 1.5, \"z\": 6.65 },     \"rotation\": { \"_x\": 0, \"_y\": 3.141592653589793, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -1, \"y\": 1.5, \"z\": 6.65 },     \"rotation\": { \"_x\": 0, \"_y\": 3.141592653589793, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -3, \"y\": 1.5, \"z\": 6.65 },     \"rotation\": { \"_x\": 0, \"_y\": 3.141592653589793, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 8.3, \"y\": 1.5, \"z\": -6 },     \"rotation\": { \"_x\": 0, \"_y\": -1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 8.3, \"y\": 1.5, \"z\": -4 },     \"rotation\": { \"_x\": 0, \"_y\": -1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 8.3, \"y\": 1.5, \"z\": -2 },     \"rotation\": { \"_x\": 0, \"_y\": -1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 8.3, \"y\": 1.5, \"z\": 0 },     \"rotation\": { \"_x\": 0, \"_y\": -1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 8.3, \"y\": 1.5, \"z\": 2 },     \"rotation\": { \"_x\": 0, \"_y\": -1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 8.3, \"y\": 1.5, \"z\": 0 },     \"rotation\": { \"_x\": 0, \"_y\": -1.5707963267948966, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -3, \"y\": 1.5, \"z\": -7.2 },     \"rotation\": { \"_x\": 0, \"_y\": 0, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": -1, \"y\": 1.5, \"z\": -7.2 },     \"rotation\": { \"_x\": 0, \"_y\": 0, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 2, \"y\": 1.5, \"z\": -7.2 },     \"rotation\": { \"_x\": 0, \"_y\": 0, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 4, \"y\": 1.5, \"z\": -7.2 },     \"rotation\": { \"_x\": 0, \"_y\": 0, \"_z\": 0, \"_order\": \"XYZ\" }   },   {     \"position\": { \"x\": 6, \"y\": 1.5, \"z\": -7.2 },     \"rotation\": { \"_x\": 0, \"_y\": 0, \"_z\": 0, \"_order\": \"XYZ\" }   } ]"
    },
    {
      "trait_type": "3xr_frame_color",
      "value": "#472558"
    }
  ],
  "title": "First Gallery 3XR template #1",
  "store": "hellovirtualworld.mintbase1.near",
  "external_url": "https://mintbase.io/store/hellovirtualworld.mintbase1.near",
  "type": "NEP171"
}
```

As you can see from the above example, merging the JSON response from Arweave produces a complete picture of token metadata while saving storage costs on-chain.&#x20;

Note that our [indexer data](broken-reference) already provides pre-resolved metadata from Arweave (currently only for Mintbase contracts).













