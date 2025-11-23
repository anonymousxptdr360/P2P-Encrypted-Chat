# 🔒 P2P-Encrypted-Chat: Ephemeral & Serverless Secure Messenger

   

**A client-side, peer-to-peer communication tool designed for ephemeral, zero-trace exchanges. It establishes a direct encrypted tunnel between two devices without intermediate storage servers.**

-----

## 📥 Access & Deployment

You can use this tool immediately via the web or download the source code for local execution.

### 🌐 Option A: Live Web Instance (Recommended for Speed)

Access the hosted version here:
👉 **[https://stopbordo.odoo.com/transfert](https://stopbordo.odoo.com/transfert)**

> ⚠️ **Operational Security (OpSec) Warning:**
> If you use the web version, **you must use "Private Browsing" (Incognito Mode)**.
>
>   * **Why?** Standard browsing modes cache website assets (HTML/JS files) to your hard drive.
>   * **Private Mode:** Ensures that absolutely no cache, cookies, or history data remains on your device once the browser window is closed.

### 💻 Option B: Local Execution (Recommended for Paranoia)

For maximum isolation, download the source code and run it locally without relying on the hosted URL.

1.  **[Download the source code](https://github.com/anonymousxptdr360/P2P-Encrypted-Chat/releases/tag/2.1)** (or clone this repository).
2.  Disconnect from the internet (optional, for air-gapped transfers via local LAN).
3.  Open `index.html` directly in your browser.

-----

## 📖 Overview

This application addresses the need for **immediate, installation-free, and forensic-resistant communication**. Unlike traditional messaging platforms (Signal, WhatsApp) that rely on relay servers and local databases, this tool operates entirely within the browser's volatile memory (RAM).

**Key Characteristics:**

  * **Zero-Knowledge Architecture:** No conversation data is ever sent to a server.
  * **Ephemeral by Design:** Closing the tab permanently destroys all encryption keys and message history.
  * **Browser-Based:** No installation required, works on modern browsers (Chrome, Firefox, Safari).
  * **New in v2.2:** Support for sending **entire folders** (automatic client-side ZIP compression).

-----

## 🛡️ Security Architecture & Cryptography

The security model relies on a **Shared Secret (Password)** known only to the two peers. This password is never transmitted over the network.

### 1\. Encryption Scheme (Encrypt-then-MAC)

We utilize industry-standard algorithms to ensure Confidentiality, Integrity, and Authenticity.

  * **Key Derivation (PBKDF2):** The shared password is processed through **PBKDF2** with **10,000 iterations** and a random **Salt**. This mitigates brute-force and rainbow table attacks.
  * **Symmetric Encryption (AES-256):** Data is encrypted using **AES-256-CBC** with a unique, random **Initialization Vector (IV)** for every message.
  * **Message Integrity (HMAC-SHA256):** To prevent ciphertext tampering (bit-flipping attacks), every message is signed with an **HMAC-SHA256**. The application verifies this signature *before* attempting decryption.

### 2\. Transport Security (WebRTC)

The connection is established via **WebRTC**, which enforces encryption in transit using DTLS (Datagram Transport Layer Security) and SRTP (Secure Real-time Transport Protocol). This protects the data stream against passive eavesdropping on the local network.

### 3\. Supply Chain Protection (SRI)

Critical cryptographic libraries (`CryptoJS`, `PeerJS`) are loaded with **Subresource Integrity (SRI)** tags (in the production release). The browser verifies the SHA-512 hash of the external scripts to ensure they have not been compromised or modified by a third party (CDN hacking).

### 4\. Client-Side Hardening ("Fortress" Update)

  * **Anti-XSS (Cross-Site Scripting):** Incoming payloads are safely rendered. The application uses strict DOM sanitization (no `innerHTML`) to prevent code execution via malicious filenames or messages.
  * **Universal File Support:** No file type restrictions. You can send any file format (binary, executables, archives). *Note: Use caution when opening unknown files.*
  * **Anti-Spam Rate Limiting:** A flood control mechanism limits message frequency to prevent browser freezing (DoS attacks).
  * **Memory Management:** Large files are processed via buffers to prevent browser crashes, but are not written to disk.

-----

## ⚠️ Threat Model & Limitations

To use this tool effectively, one must understand what it protects against and what it does not.

| Threat Vector | Status | Explanation |
| :--- | :--- | :--- |
| **Server Seizure** | ✅ **Protected** | The signaling server (PeerJS) only handles the "handshake". It has no access to the AES keys or the message content. |
| **Forensic Analysis** | ✅ **Protected** | Since data is stored in RAM, powering off the device or closing the browser leaves no recoverable trace on the hard drive. |
| **Man-in-the-Middle (MitM)** | ⚠️ **Conditional** | Security relies entirely on the **strength of the shared password**. If the password is weak or shared via an insecure channel, an active attacker could intercept the session. |
| **Metadata / Anonymity** | ❌ **Exposed** | **WebRTC leaks IP addresses.** Without a VPN, the peer (or an attacker) can see your public IP. The signaling server knows that IP 'A' connected to IP 'B'. |
| **File Size Limits** | 🛑 **Limit** | Due to browser memory constraints, file transfers are limited to **\~50MB**. Larger files may cause the tab to crash (Out of Memory). |

-----

## ⚔️ Comparison: vs. Signal / WhatsApp

This tool is not a replacement for daily messaging apps; it is a specialized tool for specific high-risk or one-off scenarios.

| Feature | 🟢 P2P Encrypted Chat | 🔵 Signal |
| :--- | :--- | :--- |
| **Architecture** | **Decentralized (P2P)** | Centralized Relay Servers |
| **Identity** | **Anonymous** (No phone/email) | Phone Number Required |
| **Data Storage** | **None (RAM)** | Encrypted Local Database (Disk) |
| **Access** | **Web Link** (Instant) | App Installation Required |
| **Metadata** | High (IP visible) | Minimal (Sealed Sender) |
| **Asynchronous** | No (Both must be online) | Yes |
| **Use Case** | **"Burner" / One-time sensitive transfer** | Long-term secure communication |

-----

## 🚀 Usage Guide

### 1\. Initialization

  * Open the application.
  * Click **"Activer"** to generate your temporary Session ID.
  * **Security Tip:** Use a VPN to mask your IP address before connecting.

### 2\. Connection

  * Share your ID with your peer via a secure out-of-band channel (e.g., encrypted email, Signal).
  * Your peer inputs your ID and clicks **"Connexion"**. Or simply scan the **QR Code** for proximity pairing.

### 3\. Authentication (The "Handshake")

  * **CRITICAL:** Once connected, click the **Lock Icon (🔓)**.
  * Enter a strong, pre-agreed **Shared Password**.
  * Both parties must enter the **exact same password**.
  * *If the password differs, the HMAC verification will fail, and messages will be rejected.*

### 4\. Transfer & Termination

  * **Files:** Click the paperclip to send any type of file (no restrictions).
  * **Folders:** Click the folder icon to zip and send an entire directory automatically.
  * **Termination:** To destroy all data, simply **close the browser tab**. No "delete" action is required as nothing was ever written to the disk.

-----

### ⚖️ Disclaimer

*This software is provided "as is", without warranty of any kind. While it implements robust cryptographic standards (AES-256, PBKDF2, HMAC), security is a process, not a product. User operational security (OpSec) regarding password strength and device integrity is paramount.*
