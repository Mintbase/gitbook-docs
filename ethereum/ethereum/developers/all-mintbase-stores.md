# Simple Queries

All queries on our graph can be used, using a simple fetch api.

{% embed url="https://thegraph.com/explorer/subgraph/nategeier/mintbase?query=All%20Stores" %}

```typescript
 const uri = 'https://api.thegraph.com/subgraphs/name/nategeier/mintbase'

  const query = `
    query {
      stores(first:1000) {
        id
      }
    }
  `;

  const opts = {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ query })
  };
  fetch(uri, opts)
    .then(res => res.json())
    .then(console.log)
    .catch(console.error);


  

```

