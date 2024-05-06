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

1. Follow the [OpenAPI spec](https://github.com/Mintbase/smart-actions-tool-example/blob/main/spec.json)
2. Deploy your service with a cloud provider like Vercel, GCP, AWS, or any other that you're comfortable with.
3. Make sure that `/spec.json` is accessible (for example `https://your-service/spec.json`)
4. Talk to our [Mintbase AI Smart Actions](https://wallet.mintbase.xyz/) and ask to validate and register your plugin followed by your URL.
