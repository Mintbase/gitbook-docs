---
description: Interact with Mintbase stores and mints directly with the blockchain
---

# Web3 Contract

### Interacting with Mintbase mints via blockchain

If you are a developer at Cryptovoxels and you  want your users to be able to purchase a Mintbase NFT without needing to leave that beautiful VR environment, this is what you'll need.&#x20;

All ERC-721 functions are available to you via code. Here are some read functions&#x20;

If you're using a library like ethers js

```
npm i -S ethersjs
```

### Connecting to a contract

#### EthersJS docs on connecting to a contract

{% embed url="https://docs.ethers.io/ethers.js/html/api-contract.html#connecting-to-existing-contracts" %}

```typescript
import { providers, Contract } from 'ethers'
const { web3 } = window

const provider = new providers.Web3Provider(web3.currentProvider)
const signer = await provider.getSigner()

const setContract = async () => {
    // Our current contract factory version
    const version = 'v1.0.0'
    const abiData = await fetch(`https://us-central1-thing-1d2be.cloudfunctions.net/getAbi?version=${version}`)
    
    const { abi } = await abiData.json()
    
    // The Mintbase market you want to interact with
    const address = '0x33c8a345830636556160c2ebc3abb90be2e1252b`
    const contract = new Contract(address, abi, provider)
    
    // Only need this if you need to change the state of the contract
    const signedContract = contract.connect(signer)
    
    // Now take a look at all the functions you get by looking into the log 
    console.log('Mintbase contract:', signedContract)
}

setContract()
```

### Signed Contract Achieved!

Once you have the signed contract, now it gets fun, you can now make requests from the user to make transactions like burn, transfer and buy. To see a list of all read and write functions it looks like this

{% embed url="https://etherscan.io/address/0x33c8a345830636556160c2ebc3abb90be2e1252b#readContract" %}

![](<../../../.gitbook/assets/Screen Shot 2020-02-04 at 8.06.46 PM.png>)

### Interacting with a Signed Contact

```typescript
// Make sure you understand wei vs gwei vs eth
const myETH = utils.bigNumberify(purchaseItem.price)


await signedContract.buyThing(Number(purchaseItem.thingId), {
  value: myETH,
}).catch(async (err: any) => {
  throw 'User rejected: Did not want to buy'
})

// Success! Purchased the item
```

### Or here is a store ABI directly

{% code title="" %}
```typescript
[{"constant":true,"inputs":[{"name":"interfaceId","type":"bytes4"}],"name":"supportsInterface","outputs":[{"name":"","type":"bool"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"name","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"name":"tokenId","type":"uint256"}],"name":"getApproved","outputs":[{"name":"","type":"address"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"to","type":"address"},{"name":"tokenId","type":"uint256"}],"name":"approve","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"giver","type":"address"},{"name":"recipients","type":"address[]"},{"name":"values","type":"uint256[]"}],"name":"batchTransfer","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"totalSupply","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"from","type":"address"},{"name":"to","type":"address"},{"name":"tokenId","type":"uint256"}],"name":"transferFrom","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"owner","type":"address"},{"name":"index","type":"uint256"}],"name":"tokenOfOwnerByIndex","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"from","type":"address"},{"name":"to","type":"address"},{"name":"tokenId","type":"uint256"}],"name":"safeTransferFrom","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"tokenId","type":"uint256"}],"name":"burn","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[],"name":"destroyAndSend","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"index","type":"uint256"}],"name":"tokenByIndex","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"maker","outputs":[{"name":"","type":"address"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"to","type":"address"},{"name":"tokenId","type":"uint256"},{"name":"tokenURI","type":"string"}],"name":"mintWithTokenURI","outputs":[{"name":"","type":"bool"}],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"tokenId","type":"uint256"}],"name":"ownerOf","outputs":[{"name":"","type":"address"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"name":"owner","type":"address"}],"name":"balanceOf","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[],"name":"renounceOwnership","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"_tokenId","type":"uint256"}],"name":"buyThing","outputs":[{"name":"","type":"bool"}],"payable":true,"stateMutability":"payable","type":"function"},{"constant":true,"inputs":[{"name":"owner","type":"address"}],"name":"tokensOfOwner","outputs":[{"name":"","type":"uint256[]"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"owner","outputs":[{"name":"","type":"address"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"isOwner","outputs":[{"name":"","type":"bool"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"symbol","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"account","type":"address"}],"name":"addMinter","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"to","type":"address"},{"name":"amountToMint","type":"uint256"},{"name":"metaId","type":"string"},{"name":"setPrice","type":"uint256"},{"name":"isForSale","type":"bool"}],"name":"batchMint","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[],"name":"renounceMinter","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[],"name":"baseUri","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"to","type":"address"},{"name":"approved","type":"bool"}],"name":"setApprovalForAll","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"account","type":"address"}],"name":"isMinter","outputs":[{"name":"","type":"bool"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[],"name":"id","outputs":[{"name":"","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"from","type":"address"},{"name":"to","type":"address"},{"name":"tokenId","type":"uint256"},{"name":"_data","type":"bytes"}],"name":"safeTransferFrom","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"","type":"uint256"}],"name":"items","outputs":[{"name":"tokenId","type":"uint256"},{"name":"price","type":"uint256"},{"name":"metaId","type":"string"},{"name":"state","type":"uint8"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":true,"inputs":[{"name":"_tokenId","type":"uint256"}],"name":"tokenURI","outputs":[{"name":"","type":"string"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"ids","type":"uint256[]"},{"name":"isEnabled","type":"bool"}],"name":"setTokenState","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"tokenIds","type":"uint256[]"}],"name":"batchBurn","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":false,"inputs":[{"name":"ids","type":"uint256[]"},{"name":"setPrice","type":"uint256"}],"name":"setTokenPrice","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"owner","type":"address"},{"name":"operator","type":"address"}],"name":"isApprovedForAll","outputs":[{"name":"","type":"bool"}],"payable":false,"stateMutability":"view","type":"function"},{"constant":false,"inputs":[{"name":"newOwner","type":"address"}],"name":"transferOwnership","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"inputs":[{"name":"name","type":"string"},{"name":"symbol","type":"string"},{"name":"uri","type":"string"},{"name":"fee","type":"address"},{"name":"creator","type":"address"}],"payable":false,"stateMutability":"nonpayable","type":"constructor"},{"anonymous":false,"inputs":[{"indexed":false,"name":"error","type":"string"},{"indexed":false,"name":"tokenId","type":"uint256"}],"name":"ErrorOut","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"metaId","type":"string"},{"indexed":false,"name":"recipients","type":"address[]"},{"indexed":false,"name":"ids","type":"uint256[]"}],"name":"BatchTransfered","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"id","type":"uint256"},{"indexed":false,"name":"metaId","type":"string"}],"name":"Minted","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"metaId","type":"string"},{"indexed":false,"name":"ids","type":"uint256[]"}],"name":"BatchBurned","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"ids","type":"uint256[]"},{"indexed":false,"name":"metaId","type":"string"}],"name":"BatchForSale","type":"event"},{"anonymous":false,"inputs":[{"indexed":false,"name":"tokenId","type":"uint256"},{"indexed":false,"name":"metaId","type":"string"},{"indexed":false,"name":"value","type":"uint256"}],"name":"Bought","type":"event"},{"anonymous":false,"inputs":[],"name":"Destroy","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"name":"previousOwner","type":"address"},{"indexed":true,"name":"newOwner","type":"address"}],"name":"OwnershipTransferred","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"name":"account","type":"address"}],"name":"MinterAdded","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"name":"account","type":"address"}],"name":"MinterRemoved","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"name":"from","type":"address"},{"indexed":true,"name":"to","type":"address"},{"indexed":true,"name":"tokenId","type":"uint256"}],"name":"Transfer","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"name":"owner","type":"address"},{"indexed":true,"name":"approved","type":"address"},{"indexed":true,"name":"tokenId","type":"uint256"}],"name":"Approval","type":"event"},{"anonymous":false,"inputs":[{"indexed":true,"name":"owner","type":"address"},{"indexed":true,"name":"operator","type":"address"},{"indexed":false,"name":"approved","type":"bool"}],"name":"ApprovalForAll","type":"event"}]
```
{% endcode %}
