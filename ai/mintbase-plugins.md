---
description: This is still work-in-progress.
---

# 🌐 Mintbase Plugins

We've implemented support for plugins in our [AI wallet](https://wallet.mintbase.xyz). Plugins enable connecting tools and AI agents specifically designed for language models.

## Ref Finance Tool Example

{% embed url="https://youtu.be/80A4467Psrw" %}

The Ref Finance Tool is a powerful example of a plugin designed to work seamlessly with our AI wallet. This tool allows users to directly interact with Decentralized Finance (DeFi) services from within the wallet interface.

With the Ref Finance Tool, users can perform a swaps all without leaving the AI wallet environment. Find the source code [here](https://github.com/Mintbase/smart-actions-tool-example/tree/main).

## How to add your plugin to Mintbase Registry?

1. Follow the [OpenAPI Specification](https://swagger.io/specification/). See [this](https://github.com/Mintbase/smart-actions-tool-example/blob/main/spec.json) example.
2. Deploy your service with a cloud provider like Vercel, GCP, AWS, or any other that you're comfortable with.
3. Make sure that `/.well-known/ai-plugin.json` is accessible (for example `https://your-service/.well-known/ai-plugin.json`)
4. [Ask our team](https://t.me/mintdev) on Telegram to add your plugin (it's a manual process for now).

## OpenAPI Mintbase Extension

We have created an extension for the OpenAPI specification that allows you to include additional metadata.

```
"x-mb": {
  "account-id": "mintbase.near",
  "assistant": {
    "model": "gpt-4o",
    "instructions": "You are a helpful assistant.",
    "temperature": 0.5,
    "tools": [{ type: "generate-transaction" }, { type: "submit-query" }]
  }
}
```

### Account ID (account-id)

• Description: Specifies the account ID associated with the plugin. This is typically the account ID on the NEAR blockchain that identifies the owner or operator of the API.

• Example: mintbase.near

### Assistant Configuration (assistant)

Provides configuration for the assistant (e.g., a model like GPT-4) that can help in interacting with the API. This section includes details about the model, its behavior, and the tools it can use.

#### **model**

Specifies the model used by the assistant. This can be any valid model identifier recognized by the system.

Example: gpt-4o

#### **instructions**

Instructions provided to the assistant, defining its role or behavior. This helps in tailoring the assistant’s responses according to specific requirements.

Example: "You are a helpful assistant."

#### **temperature**

Controls the randomness of the assistant’s responses. A lower value (e.g., 0.5) makes the output more deterministic, while a higher value (e.g., 1.0) makes it more random.

Example: 0.5

#### **tools**

A list of tools that the assistant can use. Each tool is defined by its type and possibly other configurations.

**Tool Type**\
The type of tool that the assistant can use. This can vary based on the functionality required by the API.

| Tool Type            | Description                                                                                                                  |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| generate-transaction | Creates a transaction based on the user request                                                                              |
| submit-query         | Creates a GraphQL query based on [Mintbase's Indexer](../dev/read-data/mintbase-graph.md), submits it and returns the result |
| generate-image       | Creates an image, uploads it to Arweave and returns a transaction hash                                                       |
| create-drop          | Creates an NFT drop                                                                                                          |
