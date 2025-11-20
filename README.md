## 🔒 P2P-Encrypted-Chat: Zero-Trace Secure Messenger

**Serverless, peer-to-peer communication with client-side AES-256 encryption. Conversations are strictly ephemeral, existing only in RAM, and leave no trace on disk or server.**

-----

### 🚨 Ultimate Security Workflow (Recommended)

To achieve **maximum anonymity** and ensure absolutely **zero trace** on your machine, follow this strict procedure:

1.  **Download the Code:** Get the latest release here: [**Download Source Code**](https://github.com/anonymousxptdr360/P2P-Encrypted-Chat/releases)
2.  **Turn on your VPN:** This masks your IP address from the recipient and the signaling server.
3.  **Go Incognito:** Open the downloaded `index.html` file specifically in a **Private/Incognito Window**.
    * *Why?* This prevents browser caching and ensures memory is cleared upon closure.
4.  **Close Completely:** When finished, do not just close the tab. **Close the entire browser window** to trigger the immediate destruction of encryption keys and RAM data.

-----

### ✨ Core Principles and Features

This tool is designed for absolute confidentiality, relying on three golden rules:

1.  **🔒 Absolute Confidentiality (AES-256):**
    * Messages are **mathematically locked** directly on your device *before* transmission.
    * **Indecipherable:** Without the password, interception yields only random noise.

2.  **👻 Zero Trace:**
    * **Zero Database:** Nothing is stored on a server.
    * **Volatile Memory:** Data exists only in RAM.
    * **Instant Erasure:** Closing the browser wipes the session.

3.  **🚀 Serverless P2P Connection:**
    * Uses a **direct tunnel (WebRTC)** between users.

-----

### ⚠️ Critical Security & Anonymity Warnings

While the **content** is secure (AES-256), your **identity** requires extra precautions. Be aware of the following technical limitations:

* **IP Address Leak (WebRTC):** Without a VPN, the P2P protocol (WebRTC) reveals your public IP address to your recipient.
* **Metadata & CDNs:** Your ISP knows you are connecting to PeerJS servers. External scripts (CDNs) may log that your IP loaded the library. **A VPN prevents this tracking.**
* **Downloaded Files:** If you download a file sent via chat, it saves to your hard drive. **You must manually delete it** and empty your trash bin to remove the trace.

-----

### 🛠️ Quick Usage Guide

1.  **Activate:** Click "**Activer**".
2.  **Share ID:** Send your ID to your partner via a secure out-of-band channel (e.g., Signal).
3.  **Connect:** Establish the P2P connection.
4.  **SECURE IT:** Click the **Padlock Icon** 🔓 and enter a **shared password**.
    * *Warning:* If User A types "123" and User B types "456", decryption will fail. The password must be identical.
