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
    "tools": [tools: [{ type: "generate-transaction" }]]
  }
}
```

### Tools

