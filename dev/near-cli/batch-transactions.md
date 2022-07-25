# Batch Transactions

### Install Loop

Install something like loop so you can run on transaction and that can keep running behind the scenes while you make a sandwich.

{% embed url="https://github.com/Miserlou/Loop" %}

### Using the NEAR CLI

{% embed url="https://docs.near.org/tools/near-cli" %}

#### Log into the account that has the premission needed to execute what you need

```
near login
```

### Find the Transaction Data Needed

1. Go on the mintbase UI and find a transaction you want to loop through, let's do Multiply

&#x20;

![](<../../.gitbook/assets/Screen Shot 2022-07-25 at 5.14.35 PM.png>)

2\. Initiate the transaction, but click "More Information" on the Approve Page.



![](<../../.gitbook/assets/Screen Shot 2022-07-25 at 5.15.53 PM.png>)

3\. Then click the function name \`nft\__batch_\_mint\` to reveal the code

![](<../../.gitbook/assets/Screen Shot 2022-07-25 at 5.17.14 PM.png>)

### Run a Loop on the Command line

1. Create a local file called mass\_mint
2. Replace the obvious fields formatted like so below

```
#!/bin/bash

near call nearcon2.mintbase1.near nft_batch_mint "{
\"owner_id\": \"nearcon2.near\",
\"metadata\": {
  \"extra\": \"ticket\",
  \"reference\": \"O0j5Is1vKIhyoaY74EDJs9c1te3SamALSElvw6udJDk\"
},
\"num_to_mint\": 25,
\"royalty_args\": {
  \"split_between\":{
    \"nearcon2.near\":6667,
    \"unchain-fund.sputnik-dao.near\":3333
  },
  \"percentage\":300
},
\"split_owners\": {
    \"nearcon2.near\":8000,
    \"unchain-fund.sputnik-dao.near\":2000
  }
}" --accountId nearcon2.near --gas 280000000000000 --amount 0.00000000000000000000001
```

3\. Then run the loop

```
loop 'bash mass_mint.sh' --for-duration 1h --every 5s
```





