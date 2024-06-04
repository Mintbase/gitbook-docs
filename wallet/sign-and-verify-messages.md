---
description: >-
  Mintbase Wallet provides functionalities for signing and verifying messages.
  This documentation outlines the steps for using these features, including
  signing a message, verifying a message via the UI
---

# ✉️ Sign and Verify Messages

## Sign Message

The sign message functionality allows you to sign a message using your Mintbase Wallet. The signed message can then be used for various verification purposes.

#### Endpoint

* **URL**: [https://wallet.mintbase.xyz/sign-message](https://wallet.mintbase.xyz/sign-message)

#### Parameters

* `message`: The message you want to sign.
* `callbackUrl`: The URL to which the signed message will be sent.
* `nonce`: A unique identifier to prevent replay attacks.

#### Example

```
https://wallet.mintbase.xyz/sign-message?message=hey&callbackUrl=https://mintbase-wallet-git-sign-verify-v2-mintbase.vercel.app&nonce=1
```

### Verify Message

The verify message functionality allows you to verify a signed message using the UI or API. Verification ensures that the message was signed by the rightful owner of the specified account.

#### Verify via UI

**Endpoint**

* **URL**: [https://wallet.mintbase.xyz/verify-message](https://wallet.mintbase.xyz/verify-message)

**Parameters**

* `accountId`: The account ID of the signer.
* `publicKey`: The public key of the signer in base58 format.
* `signature`: The signature of the signed message in base64 format.
* `message`: The original message that was signed.
* `nonce`: A unique identifier used during signing.
* `recipient`: The intended recipient (e.g., `mainnet`).
* `callbackUrl`: The URL to which the verification result will be sent.

**Example**

```
https://wallet.mintbase.xyz/verify-message?accountId=faraday_stroud.mintbase.testnet&publicKey=ed25519%3A6533dMsJstJvNUFcCkvgdWPWFdbs4RDRtt4vaUc1gnZU&signature=sMPu%2BAnsM2OCXMTM1OeB19XaskFG%2Fg1cBXzCClW0IbDwPvowM3Uotq6iYOoX5Qxuti5rq01GnAeIAZQ6%2F0UCCA%3D%3D&message=hey&nonce=1&recipient=mainnet&callbackUrl=https://mintbase-wallet-git-signing-message-mintbase.vercel.app
```

### Verify Message via API Endpoint

**Endpoint**

* **URL**: [https://wallet.mintbase.xyz/api/verify-message](https://wallet.mintbase.xyz/api/verify-message)

**Parameters**

* `accountId`: The account ID of the signer.
* `publicKey`: The public key of the signer in base58 format.
* `signature`: The signature of the signed message in base64 format.
* `message`: The original message that was signed.
* `nonce`: A unique identifier used during signing.
* `recipient`: The intended recipient (e.g., `mainnet`).
* `callbackUrl`: The URL to which the verification result will be sent.

**Example**

```
https://wallet.mintbase.xyz/api/verify-message?accountId=faraday_stroud.mintbase.testnet&publicKey=ed25519%3A6533dMsJstJvNUFcCkvgdWPWFdbs4RDRtt4vaUc1gnZU&signature=sMPu%2BAnsM2OCXMTM1OeB19XaskFG%2Fg1cBXzCClW0IbDwPvowM3Uotq6iYOoX5Qxuti5rq01GnAeIAZQ6%2F0UCCA%3D%3D&message=hey&nonce=1&recipient=mainnet&callbackUrl=https://mintbase-wallet-git-signing-message-mintbase.vercel.app
```
