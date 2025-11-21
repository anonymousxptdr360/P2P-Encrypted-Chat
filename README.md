# 🔒 P2P-Encrypted-Chat: Zero-Trace Secure Messenger

![Security](https://img.shields.io/badge/Security-AES--256-brightgreen) ![Protocol](https://img.shields.io/badge/Protocol-WebRTC-blue) ![Storage](https://img.shields.io/badge/Storage-RAM%20Only-orange)

**Serverless, peer-to-peer communication tool with client-side AES-256 encryption. Conversations are strictly ephemeral, existing only in volatile memory (RAM), and leave no forensic trace on the disk or server.**

---

## 🌐 Access Methods

### Method A: Direct Web Access (Convenience)
Accessible for immediate usage at: **https://stopbordo.odoo.com/transfert**
> *Note: While convenient, web access introduces minor privacy risks regarding browser caching of the source code assets. For critical anonymity, use Method B.*

### Method B: Ultimate Security Workflow (Recommended)
To achieve **maximum anonymity** and ensure **zero forensic trace** on your local machine:

1. **Download Source:** Get the latest release: [**Download Source Code**](https://github.com/anonymousxptdr360/P2P-Encrypted-Chat/releases/tag/1.1)
2. **VPN Activation:** Enable your VPN. This masks your public IP address from the WebRTC signaling process and the recipient.
3. **Sandboxed Environment:** Open the `index.html` file in a **Private/Incognito Window**.
   * *Technical Reason:* This prevents the browser from caching local assets and ensures the JavaScript Heap memory is cleared immediately upon closure.
4. **Kill Switch:** When finished, close the **entire browser window**. This triggers the immediate destruction of the RAM context, encryption keys, and conversation history.

---

## 🛡️ Security Architecture

### 1. Application Layer Encryption (AES-256)
Before data is handed to the network layer, it is encrypted locally using `CryptoJS`.
* **Algorithm:** AES-256 (Advanced Encryption Standard).
* **Key Derivation:** The encryption key is derived from your shared password.
* **Security Guarantee:** Even if the WebRTC stream is intercepted or if a malicious actor guesses your ID, the payload remains mathematically indecipherable noise without the exact password.

### 2. Transport Layer Security (WebRTC/DTLS)
Connections are established via **WebRTC**, which mandates encryption in transit using DTLS (Datagram Transport Layer Security) and SRTP (Secure Real-time Transport Protocol). This prevents Man-in-the-Middle (MitM) attacks on the local network.

### 3. Volatile Memory Storage (RAM)
* **No Persistence:** Messages are stored in JavaScript variables within the browser's RAM (Random Access Memory).
* **No Disk Writes:** unlike standard messaging apps, no database (SQL/NoSQL) or local file storage is used.
* **Forensic Safety:** Once the power is cut or the process is terminated, the data is physically lost and irretrievable.

---

## ⚠️ Threat Model & Anonymity

While the **content** is secure, users must understand the distinction between *Confidentiality* and *Anonymity*.

| Threat Vector | Protection Status | Explanation |
| :--- | :--- | :--- |
| **Content Interception** | ✅ **SECURE** | AES-256 makes brute-forcing impossible with a strong password. |
| **Server Seizure** | ✅ **SECURE** | No server stores data. Only a signaling server is used for the handshake, then the connection is P2P. |
| **Metadata / IP Leak** | ⚠️ **WARNING** | **WebRTC reveals your IP.** Without a VPN, the recipient can see your public IP address. |
| **Identity Guessing** | ⚠️ **WARNING** | Using simple IDs (e.g., "test") allows strangers to connect. Always use UUIDs or complex IDs. |

---

## 🛑 Technical Limitations

### File Size Limits (RAM Constraints)
This tool uses an in-memory buffer for file encryption. It does **not** stream data from the disk.
* **Consequence:** You cannot send files larger than your available browser RAM.
* **Limit:** Attempting to send files >500MB - 1GB (depending on your hardware) may cause the browser tab to crash ("Out of Memory").

### File Persistence
If you **download** a file sent via the chat, it is written to your hard drive's "Downloads" folder.
* **Action Required:** You must manually delete the file and securely empty your trash bin to remove the trace from your disk.

---

## 🛠️ Quick Usage Guide

1. **Activate:** Click **"Activer"**.
2. **Exchange Credentials:** Share your **ID** via a secure out-of-band channel (e.g., Signal, Matrix).
3. **Connect:** Input the partner's ID and establish the P2P connection.
4. **LOCK THE CHANNEL:** Click the **Padlock Icon** 🔓 and enter a **Shared Secret (Password)**.
   * *Critical:* Both parties must enter the **exact same password**. If characters differ, decryption will fail and messages will appear as errors.
