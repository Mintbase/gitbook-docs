# 🌐 Agent Plugins

We've implemented support for plugins in our [AI wallet](https://wallet.mintbase.xyz)[.](https://wallet.bitte.ao) Plugins enable connecting tools and AI agents specifically designed for language models.

## Ref Finance Tool Example

{% embed url="https://www.loom.com/share/0d6e1d0e47d945649e64bd2ea362baf3?sid=7696d745-9061-44a6-8020-437addf77bc8" %}

The Ref Finance Tool is a powerful example of a plugin designed to work seamlessly with our AI wallet. This tool allows users to directly interact with Decentralized Finance (DeFi) services from within the wallet interface.



### Quickstart

[Fork / deploy our Ref DeFi Swap Agent](https://templates.bitte.ai/templates/ref-finance-agent-next)

With the Ref Finance Tool, users can perform swaps all without leaving the AI wallet environment.

## How to add your plugin to Bitte Registry?

### 1. Prepare Your OpenAPI Specification

Ensure your AI plugin follows the OpenAPI Specification. See the Ref Finance Agent example [here](https://templates.bitte.ai/templates/ref-finance-agent-next).

[Here's an example of a well-structured OpenAPI Specification](https://ref-finance-agent.vercel.app/.well-known/ai-plugin.json).

⚠️ Make sure to include the [Bitte Extension](assistant-plugins.md#openapi-bitte-extension).

```json
"x-mb": {
  "account-id": "bitte.near",
  "assistant": {
    "name": "assistant-name",
    "description": "Shorter summary about the assistant and it's capabilities",
    "instructions": "Detailed, specific instructions to be passed to AI Assistant on it's funcitonality and tool usage.",
    "tools": [{ type: "generate-transaction" }, { type: "submit-query" }]
  }
}
```

### 2. Deploy Your Service

Deploy your service with a cloud provider such as Vercel, Google Cloud Platform (GCP), Amazon Web Services (AWS), or any other provider you are comfortable with. Ensure your service is publicly accessible.

### 3. Host the Plugin Manifest

Make sure the plugin manifest file is accessible at `/.well-known/ai-plugin.json` on your domain. The URL should be similar to:

```
https://your-service/.well-known/ai-plugin.json
```

### 4. Register Your Plugin

Register your plugin using the `ai-plugins` [API Reference UI](https://wallet.bitte.ai/api/ai-plugins/ref).

Make sure to save the **apiKey** returned for managing your plugin.\
\
To manage your plugin use the `ai-plugins/PLUGIN_ID` endpoint. `PLUGIN_ID` is your plugin's url without the protocol `https://` i.e. `ref-finance-agent.vercel.app`

Pass your **apiKey** using the `bitte-api-key` header in your request.\
\
**If not using the** [**API Reference UI**](https://wallet.bitte.ai/api/ai-plugins/ref)

<pre><code> # REGISTER - register by providing your pluginUrl or pluginId
<strong> curl -X POST \
</strong> "https://wallet.mintbase.xyz/api/ai-plugins/PLUGIN_ID"
 
 # UPDATE - refetches Plugin Spec, regenerates Agent &#x26; Tools
 curl -X PUT \
 -H "bitte-api-key: YOUR_API_KEY" \
 "https://wallet.bitte.ai/api/ai-plugins/PLUGIN_ID"

 # DELETE - deletes Plugin, Agent, and Tools from Bitte Registry
 curl -X DELETE \
-H "bitte-api-key: YOUR_API_KEY" \
"https://wallet.bitte.ai/api/ai-plugins/PLUGIN_ID"
</code></pre>

### 5. Debug and Test Your Plugin

Once registered, you will receive a debug URL that will take you to the Playground to test your agent.

```
https://wallet.bitte.ai/smart-actions/prompt/hey?mode=debug&agentId=<agentId>
```

### 6. Verification

When agents are registered they will not be immediately available in the production registry. The verification process is manual for now.&#x20;

[Contact our team ](https://t.me/mintdev) on Telegram to start the verification process when you're ready.

## OpenAPI Bitte Extension

We have created an extension for the OpenAPI specification that allows you to include additional metadata.

```json
"x-mb": {
  "account-id": "bitte.near",
  "assistant": {
    "name": "assistant-name",
    "description": "Shorter summary about the assistant and it's capabilities",
    "instructions": "Detailed, specific instructions to be passed to AI Assistant on it's funcitonality and tool usage.",
    "tools": [{ type: "generate-transaction" }, { type: "submit-query" }]
  }
}
```

### Account ID (account-id)

• Description: Specifies the account ID associated with the plugin. This is typically the account ID on the NEAR blockchain that identifies the owner or operator of the API.

• Example: bitte.near

### Assistant Configuration (assistant)

Provides the configuration for the assistant that will guide the user in interacting with the API. This section includes details about its behavior, and the tools it can use.

> **name**

Instructions provided to the assistant define its role or behavior. This helps tailor the assistant’s responses according to specific requirements.

Example: "Weather Agent"

> #### **description**

A general summary of the assistant's functionalities and tools / endpoints.

> #### **instructions**

Instructions provided to the assistant define its role or behavior. This helps tailor the assistant’s responses according to specific requirements.

Example: "You are a helpful assistant. When using the get-weather tool make sure to know or ask for the user's location."

> #### **tools**

A list of tools that the assistant can use. Each tool is defined by its type and possibly other configurations.

**Tool Type**\
The type of tool that the assistant can use. This can vary based on the functionality required by the API.

| Tool Type            | Description                                                                                                                  |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| generate-transaction | Creates a transaction based on the user request                                                                              |
| submit-query         | Creates a GraphQL query based on [Mintbase's Indexer](../dev/read-data/mintbase-graph.md), submits it and returns the result |
| generate-image       | Creates an image, uploads it to Arweave and returns a transaction hash                                                       |
| create-drop          | Creates an NFT drop                                                                                                          |
