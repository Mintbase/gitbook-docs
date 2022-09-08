# GraphQL

This is our preferred option as it is probably the most flexible option and allows an easy schema exploration.

### How to query data?

| Network | Endpoint                                                                         |
| ------- | -------------------------------------------------------------------------------- |
| mainnet | <mark style="color:green;">https://interop-mainnet.hasura.app/v1/graphql</mark>  |
| testnet | <mark style="color:orange;">https://interop-testnet.hasura.app/v1/graphql</mark> |

1. Go to [https://graphiql-online.com/](https://graphiql-online.com/)
2. Enter one of the above endpoints into the input.&#x20;
3. Click around the tree on the left side, building queries can be done just by clicking around.

The queries and relationships are extensible, we suggest just clicking around the tree to make the queries and it will become easy over time.&#x20;

Always keep in mind our [data model](data-model/) and [schema](data-model/schema-v1.md#dbml).

### Query Formatting

Find all the different entities and parameters for interacting with the API.

#### Core Entities

* `tokens`: Gets data on single tokens
* `things`: The token type (metadata wrapper)
* `metadata`: Indexed metadata
* `stores`: Stores/contracts deployed
* `lists`: Marketplace listings
* `offers`: Offers made to market listings
* `minters`: Allowed mintings accounts&#x20;
* `earnings`: Historical earnings per account
* `royaltys`: Forever splits for a token
* `splits`: One-time splits for a token market listing
* `approvals`: Token approvals
* `allowlists`
* `banlists`

#### Aggregated Entities

...

#### Query Parameters

...

#### Pagination Parameters

...

### Demo

![](https://lh5.googleusercontent.com/AXfMvEvv5zB9N82hkeNA3VWZnUa94v\_SWbgP3sv-UHXD\_hiwoxRnAa9sYUqOtZhpQlHoTIx\_SRzG4YFjosA11VRT-OFZeyfTu\_NWs283Bi0GGAy4AnsJ\_ZmJ2hvyFrJFpc4D6-eS1ozr8Q84l-k)
