## 🔒 P2P-Encrypted-Chat: Zero-Trace Secure Messenger

**Serverless, peer-to-peer communication with client-side AES-256 encryption. Conversations are strictly ephemeral, existing only in RAM, and leave no trace on disk or server.**

-----

### ✨ Core Principles and Features

This tool is designed for absolute confidentiality and anonymity, relying on three golden rules:

1.  **🔒 Absolute Confidentiality (AES-256):**

      * Messages and files are **mathematically locked (AES-256)** directly on your device *before* transmission.
      * **Indecipherable:** Interception by a hacker, ISP, or relay server yields only incomprehensible characters without the shared password.

2.  **👻 Zero Trace:**

      * **Zero Database:** Nothing is ever stored on a cloud or server.
      * **Volatile Memory:** Data exists only in **RAM (Random Access Memory)**.
      * **Instant Erasure:** Closing the browser tab destroys all keys and data instantly, as if the conversation never took place.

3.  **🚀 Serverless P2P Connection:**

      * The system establishes a **direct tunnel (P2P)** between users. **No central server stores your data.**

-----

### ⚠️ Security Notice & Passwords

#### Encryption Activation

To activate the **AES-256 encryption**, both parties **MUST** agree on a common password and enter it using the padlock icon.

#### The Password Rule

If User "A" uses "123" and User "B" uses "456", the messages will **NOT** be readable, resulting in a red "**Decryption Failure**" warning.

#### Anonymity Tip

  * Your recipient can see your public IP address.
  * **Recommendation:** Always use a **VPN** to mask your IP address for complete anonymity.

-----

### 🛠️ Quick Start Guide

1.  **Activate:** Click the "**Activer**" (Activate) button.
2.  **Share ID:** Give your generated ID to your friend (or scan their QR Code).
3.  **Connect:** Establish the direct P2P connection.
4.  **Secure (Optional but Recommended):** Click the padlock and set a **strong, common password** shared via an out-of-band channel (e.g., Signal, SMS, voice).
5.  **Bonus:** Use **Private Browsing** mode to avoid browser caching.
