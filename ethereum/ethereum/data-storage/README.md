---
description: Information about data storage on Mintbase
---

# Data Storage

We now store all NFT files and metadata on the [Arweave](https://www.arweave.org/) hybrid blockchain they call the blockweave.

{% embed url="https://medium.com/mintbase/mintbase-arweave-9459f3889c79" %}

### TLDR;

Your NFTs' entire life now lives on two blockchains,  Ethereum and Arweave, nothing on Mintbase, which is neat, but adds some complexity.&#x20;

### On Ethereum (\~12 second transactions)

1. Your own deployed smart contract we call a store
2. Your token&#x20;

### On Arweave  (2-10min second transactions)

1. Immutable metadata [that looks like this](https://arweave.net/by6foO9X3Lg97cf0WuWrdrQJquHjuH4n4LLrnkkEreY)
2. Any files uploaded[ like this one](https://arweave.net/0b\_LVmlQvpxNUp3BlQSnFSagUUC\_kzpAVjwrFSo-FSw)

![](https://arweave.net/0b\_LVmlQvpxNUp3BlQSnFSagUUC\_kzpAVjwrFSo-FSw)



### Where things might go wrong.

You might have noticed the two difference transaction times, basically we start by pushing the files and metadata when you mint and upload, and this will take longer than the token itself on Ethereum to confirm.

### My token minted,  but not the image

According to the Arweave team, there is a 1/200 chance of the data not being mined so there is a possibility that you might upload a file, mint the token and the storage never takes. Apologies for this, this is why we have a free tier now of 100MB as we pay the Arweave fees behind the scenes.&#x20;

If over 30 minutes have passed and you still see the loading to Arweave message you might need to burn that token and try again.

### We are all pioneers

Always remember, we are pioneering new technology and leveraging about 6 other blockchain companies that are also pioneering, so things might break. Imagine the early pioneers complaining to have to fight through jungle not having a nice fancy highway to romp down.&#x20;

Mintbase is doing it the right way, which is not the easiest. Ping us on [discord](https://discord.gg/VCH5dMm) if you have more issues.

### Get Metadata

If you want to find your Arweave stuff, just go to the single item view can grab the last long string after the last "/" and put that into `https://arweave.net/{{ string }}`

![](<../../../.gitbook/assets/Screen Shot 2020-06-03 at 1.56.54 PM.png>)

###

You'll see something like this:

```javascript
{
  "minter": "0x87085d8d22d688e7ac9da3384127169f83e059e6",
  "mintedOn": "2020-06-02T01:08:18.731Z",
  "contractAddress": "0x0163f249af5a4781cd09edeb2326066b9552d8ec",
  "minted": "Minted on Mintbase.io",
  "fiatPrice": "$24.85",
  "name": "300 • Dandy Newman",
  "description": "We are not perfect. We were not made by computational probabilities and mathematical calculations. We are the product of pure fun. That is why WE ARE UNIQUE.",
  "youtube_url": "",
  "price": "$0.00",
  "ethPrice": "0.1",
  "amountToMint": 1,
  "forSale": true,
  "image": "https://arweave.net/0b_LVmlQvpxNUp3BlQSnFSagUUC_kzpAVjwrFSo-FSw",
  "attributes": [
    {
      "trait_type": "rarity",
      "value": "vjEP45pAZoPyAxV0KZIc"
    },
    {
      "trait_type": "website",
      "value": "https://twitter.com/MrMonkArt"
    },
    {
      "trait_type": "location",
      "value": "Mexico"
    },
    {
      "trait_type": "place_id",
      "value": "ChIJU1NoiDs6BIQREZgJa760ZO0"
    },
    {
      "trait_type": "Side",
      "value": "Tecnico"
    },
    {
      "trait_type": "Technique",
      "value": "Scissor Jack"
    },
    {
      "trait_type": "Shape",
      "value": "Triangle"
    }
  ],
  "category": "alJuInV4dezvHTNU8Dp1",
  "external_url": "https://mintbase.io/my-market/0x0163f249af5a4781cd09edeb2326066b9552d8ec",
  "type": "ERC721"
}
```

### `Transaction Data`

If you want to see the transaction data when mines just add a `tx` in between:

{% embed url="https://arweave.net/tx/by6foO9X3Lg97cf0WuWrdrQJquHjuH4n4LLrnkkEreY" %}

```javascript
{
  "format": 2,
  "id": "by6foO9X3Lg97cf0WuWrdrQJquHjuH4n4LLrnkkEreY",
  "last_tx": "wxxFpk3l85BvBrp_m54uE9myYmgTHxWn3jAve9JOQ3D9fSMvzfJ6R0gAWasuDHEH",
  "owner": "yGQOpZIfJTpsHOEAVVaFzdL2vkAVWDEa8vPcOGgmlN1OQRh6wzjqTvWZ-i5sF93OHhGXc53pU86viaTX7MSQKD8VwoStge2U_gP6HgjZD6CjqnFwqkX-bN2RRaWMm9wcpzk8Ki-XdX63gdn9s-gx_cj6wbK_iTlev4LiV8s6iZuDq6Bfvdn0RPy4z3gstfEZxx_y443p9vf4zHq0QB42j3r4-wALURZuMsFGa6akcDxkFYF1HrU96IDVk4vSp9wSG7eGSapFgwiQDBjpEkvR8_hN5iaBVKQjwSpqvS9LyeIH-23bmR52iBeZnBQ8FYuXOXUTFhqFX44bmcE0dA7GFbV9WDXATwrd0uKnN2Sz7-HZFawiiQJaojAkNB1I6dACWNrcKpKBtGQYO8Gwsuvyb90ganlMFfz6mDhXwl9Z6UKnpFdUPitYu6fXM3i6XWWNnYPC-oIg4eRm5gT7QTzkA3gAVQMRgAZHgXOrsOOLyTK3tiAz-OoYBUKanQamMzKxVeZFQpTX59OD3FpduD8NmDEijoh_NX2zIDaTYCqt1ljl1G3bdXM-VV5mqek0ZGRdZ1T3H_Ix1HyIAsHf8u3gtAWgIDhrhxndhtSVjRFsI3DD8S1OcL6DguyLT97DZTx056wvpD3QRY8BWU9_Q8eXr5sYhQMmE9-bh_Ly4l83EPk",
  "tags": [
    {
      "name": "Q29udGVudC1UeXBl",
      "value": "YXBwbGljYXRpb24vanNvbg"
    }
  ],
  "target": "",
  "quantity": "0",
  "data": "",
  "data_size": "1084",
  "data_tree": [
    
  ],
  "data_root": "6uLp_tUpzWAVUKq3oVZ47VFMUTPOANXN9KbN_lf_yDo",
  "reward": "5727346",
  "signature": "uGqXDkA3jMyW8oNv7JoJievpWBhQ2wPJ_dzrGt0i64fMhlKK1Dr9HwFqQAqZER8YRrEYrumbeiFWt3z5fLzT9kBKjmizZ16dGLQ_cSEZZV0leJEdiDCPBqE5XFdP4MjBunaYl17WA7Ew9XbWnVMjJAi2XCDIkcs8qq0b6xWNpNNqpF9uYvyMXfNglk616qWELhJHr_qtzqAyJgNB2Sb9bj6PU-SiwFrmQg692F8zJG2R7jlaQNGAEB28svfVpONMEwy86KL4ZIkUPxi7iiK1Lb-eYpgLw8ScIddDNx2kY35vmUWiom0E5w4xvRQZEMURALE2MRrsX0_kSHsYwuMrvJGq1vwWZ2dJhLCDFfxUsHpCn1Yhl4HKGF3cCcXV1_NRWhlcB5GxDz44ZnLhiCbNh505_sR4AT3pRkWcm1OLFiWjnIrVrpjP-v-BDr2JmPpCrTA6C32nsCFpLPN6avjX14--W8bhc49fwnIf7k6LDZmycCxdAX-O1P5s_YLfp5VBMedeMPstL40PGbpDsa4HTCQ3O4c5NGJEb8OK8ZypXoycVjCL5SCQojx4UoDdIZlqmuVAfPWa7vvA3jtGGkOThwxfHGwZYKZxtgoKMkykV4vJXeDT8dL2LAMDMeJ8PE4SQOdP6pFucrHj36i26q9S3wk_uhjxy-tzzK_Pd5iI5CM"
}
```

\
\
\
\
\
