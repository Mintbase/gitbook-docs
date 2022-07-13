# Get Thing Metadata

{% embed url="https://www.loom.com/share/cd3efad270314784aa750ca5003f21c3" %}

### Step One, What's a Thing?

First it's important to understand what a Thing is vs a Token, [read up on our data model](../data-model/).



### Get the Thing ID

When you go to the thing page (Main overview of the asset), you can get the id in the URL right after thing/.....



![](<../../../.gitbook/assets/Screen Shot 2021-11-22 at 3.23.17 PM.png>)



Get The Metadata

If you want to use on testnet, check out the two base uris [here](broken-reference).

Simply add the thingId to the end of \`[https://mintbase-mainnet.hasura.app/api/rest/things/](https://mintbase-mainnet.hasura.app/api/rest/things/-):id\`

{% embed url="https://mintbase-mainnet.hasura.app/api/rest/things/e6rzhF2xrWL3S_3YPMtZVw-yWuI1O_INDkwdSwGYo5k:zengin.mintbase1.near" %}

```
 {
   "thing": [
    {
      "id": "e6rzhF2xrWL3S_3YPMtZVw-yWuI1O_INDkwdSwGYo5k:zengin.mintbase1.near",
      "memo": "music",
      "metaId": "e6rzhF2xrWL3S_3YPMtZVw-yWuI1O_INDkwdSwGYo5k",
      "storeId": "zengin.mintbase1.near",
      "metadata": {
        "title": "Transform love ",
        "description": "LOVE",
        "media": "https://arweave.net/iQY43tOTj7jVsyKVRficOLDdOd7rxTBdD8VqKvEufQs",
        "media_hash": "iQY43tOTj7jVsyKVRficOLDdOd7rxTBdD8VqKvEufQs",
        "animation_hash": "-aaCXEZv4zmbL5l8SPQa0As7Au2LYGTf2YM0pKvPtak",
        "animation_url": "https://arweave.net/-aaCXEZv4zmbL5l8SPQa0As7Au2LYGTf2YM0pKvPtak",
        "youtube_url": null,
        "document": null,
        "document_hash": null,
        "extra": {
          
        },
        "external_url": "https://mintbase.io/store/zengin.mintbase1.near",
        "category": "music",
        "type": "NEP171",
        "visibility": "safe",
        "media_type": "image/jpeg",
        "animation_type": "audio/mpeg",
        "tags": {
          
        },
        "media_size": 40817,
        "animation_size": 1767384
      },
      "tokens": [
        {
          "id": "64:zengin.mintbase1.near",
          "ownerId": "kseniiashm.near"
        }
      ],
      "store": {
        "baseUri": "https://arweave.net",
        "owner": "kseniiashm.near"
      }
    }
  ]
}
```



Pretty close to the [OpenSea](https://docs.opensea.io/docs/metadata-standards) metadata standards, the `animation_url` is the song as we can see in the `animation_type`

``





