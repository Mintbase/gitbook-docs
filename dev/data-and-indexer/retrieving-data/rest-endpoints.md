# REST Endpoints

Mintbase only uses our [GraphQL](broken-reference) system for our Minter, Market, Redeemer, and Auction, as it has a much more robust with very deep relational architecture, but if you prefer REST here are some basic bits.&#x20;

| NEAR Network Origin | URI                                 |
| ------------------- | ----------------------------------- |
| mainnet             | https://mintbase-mainnet.hasura.app |
| testnet             | https://mintbase-testnet.hasura.app |

#### Example

```
await fetch(`[API_ORIGIN]/api/rest/stores`, {
  method: `GET`,
});
```

### Stores

{% swagger src="../../../.gitbook/assets/openapi.json" path="undefined" method="undefined" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/stores/{id}" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

#### Example

{% embed url="https://mintbase-mainnet.hasura.app/api/rest/stores/wilde.mintbase1.near" %}

### Things

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/things" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/things/{id}" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

### Tokens (NFTs)

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/tokens" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% hint style="info" %}
id = {unique token id} + ":"  + {full contract name}

\
387:bonepolice.mintbase1.near
{% endhint %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/tokens/{id}" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% embed url="https://mintbase-mainnet.hasura.app/api/rest/tokens/387:bonepolice.mintbase1.near" %}

### Market

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/lists" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/lists/{id}" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/approvals" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/dappradar/top-stores" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/marketplace" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/token-approvals" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/categories" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

### Accounts

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/accounts/{account}" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/accounts/{account}" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}

### Overall

{% swagger src="../../../.gitbook/assets/openapi.json" path="/api/rest/stats" method="get" %}
[openapi.json](../../../.gitbook/assets/openapi.json)
{% endswagger %}
