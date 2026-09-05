<div align="center"><img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=32&pause=1000&color=A855F7&center=true&vCenter=true&width=750&lines=%40noverojava%2Flibsignal-node;Signal+Protocol+for+Node.js;Secure+Messaging+Protocol" alt="Typing SVG" /><br /><img src="https://files.catbox.moe/q319ab.png" width="150" alt="Novero Logo" />@noverojava/libsignal-node

Signal Protocol implementation for Node.js

A ratcheting forward secrecy protocol for secure messaging environments.

""npm version" (https://img.shields.io/npm/v/@noverojava/libsignal-node?style=for-the-badge&logo=npm&logoColor=white&color=A855F7&label=NPM)" (https://www.npmjs.com/package/@noverojava/libsignal-node)
""npm downloads" (https://img.shields.io/npm/dt/@noverojava/libsignal-node?style=for-the-badge&logo=npm&logoColor=white&color=blue&label=DOWNLOADS)" (https://www.npmjs.com/package/@noverojava/libsignal-node)
""License" (https://img.shields.io/badge/license-GPL--3.0-blue?style=for-the-badge)" (LICENSE)
""Node.js" (https://img.shields.io/badge/node-%3E%3D18-brightgreen?style=for-the-badge&logo=node.js&logoColor=white)" (package.json)

<br />Fast • Secure • Reliable • Extensible

</div>---

📖 Overview

"@noverojava/libsignal-node" is a Signal Protocol implementation for Node.js based on the original "libsignal-protocol-javascript" and "libsignal-node" ecosystem.

It provides cryptographic session functionality for applications that require secure communication and session state management.

Main Features

- 🔐 Signal Protocol session support
- 🔑 PreKey management
- ✍️ Signed PreKey support
- 🪪 Identity key management
- 🔄 Session state management
- 🛡️ Forward secrecy protocol
- 📦 PreKey Bundle support
- 💬 PreKey Signal Message support
- ⚡ Node.js compatible

---

📦 Installation

npm

npm install @noverojava/libsignal-node

Yarn

yarn add @noverojava/libsignal-node

pnpm

pnpm add @noverojava/libsignal-node

---

🚀 Quick Start

const libsignal = require('@noverojava/libsignal-node');

console.log('libsignal-node loaded successfully');

For ES Modules:

import libsignal from '@noverojava/libsignal-node';

console.log('Signal Protocol ready');

---

🔐 How the Signal Protocol Works

The Signal Protocol uses secure sessions between clients.

Client A
   │
   │ Retrieve PreKey Bundle
   ▼
Session Establishment
   │
   ▼
Encrypted Session
   │
   ▼
Secure Messaging

Once a session has been established, the session state can be used for future encrypted communication.

---

🔑 PreKeys

The protocol uses a concept called PreKeys.

A PreKey contains an elliptic curve public key and a unique identifier.

Clients generally generate:

- Identity Key Pair
- Signed PreKey
- Multiple PreKeys

These keys can be uploaded to a server so other clients can establish a secure session.

Client
│
├── Identity Key
│
├── Signed PreKey
│
└── PreKeys
       │
       ▼
     Server

---

✍️ Signed PreKeys

Signed PreKeys are associated with a client's identity key.

They help verify cryptographic information during session establishment.

Identity Key
      │
      ▼
Signed PreKey
      │
      ▼
Signature Verification
      │
      ▼
Secure Session

---

🔄 Sessions

Signal Protocol is session-oriented.

Clients establish a secure session and use that session for encryption and decryption.

Sessions can generally be established using:

1. PreKey Bundles

A sender retrieves a recipient's PreKey Bundle from a server.

Sender
   │
   │ Request PreKey Bundle
   ▼
Server
   │
   │ Recipient Keys
   ▼
Session Builder
   │
   ▼
Secure Session

2. PreKey Signal Messages

A client can receive a PreKey Signal Message and use it to establish a session.

Sender
   │
   │ PreKey Signal Message
   ▼
Recipient
   │
   ▼
Session Establishment
   │
   ▼
Encrypted Communication

---

🛡️ Forward Secrecy

The Signal Protocol uses a ratcheting mechanism.

Session keys evolve as messages are exchanged.

Message 1
   │
   ▼
Ratchet State A
   │
   ▼
Message 2
   │
   ▼
Ratchet State B
   │
   ▼
Message 3

This design helps protect past communication even as new messages are exchanged.

---

💾 State Management

An established session contains important cryptographic state.

State| Description
🔐 Identity State| Local and remote identity keys
🔑 PreKey State| Generated PreKeys
✍️ Signed PreKey State| Signed PreKeys
🔄 Session State| Established sessions

---

🗂️ Example Storage Structure

signal-data/
│
├── identity/
│   └── identity.json
│
├── prekeys/
│   ├── 1.json
│   ├── 2.json
│   └── 3.json
│
├── signed-prekeys/
│   └── signed-prekey.json
│
└── sessions/
    ├── user-1.json
    └── user-2.json

«⚠️ The actual storage implementation depends on your application.»

---

🔧 Requirements

Requirement| Version
Node.js| ">=18"
npm| Latest recommended
Runtime| Node.js

---

📚 Original Project

This package is based on the original Signal Protocol JavaScript ecosystem.

Original projects include:

- "libsignal-protocol-javascript"
- "libsignal-node"
- Open Whisper Systems
- Forsta Labs

---

🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Test your changes
5. Submit a Pull Request

---

📦 Development

Install dependencies:

npm install

Run tests:

npm test

---

⚠️ Security Notice

Cryptographic data should always be handled carefully.

Never:

- Expose private keys
- Upload session data to public repositories
- Commit cryptographic credentials
- Share private PreKey material

Always store sensitive cryptographic data securely.

---

📜 License

Licensed under the GPL-3.0 License.

See the "LICENSE" file for complete license information.

Original license and copyright notices remain applicable.

---

📚 Credits

Original Work

- Open Whisper Systems
- Signal Protocol contributors
- Forsta Labs

Maintained By

NoveroJava

All credit for the original Signal Protocol implementation belongs to its original developers and contributors.

---

⚠️ Disclaimer

"@noverojava/libsignal-node" is not an official Signal product.

Use this package responsibly and ensure that cryptographic implementations are properly reviewed before using them in security-critical applications.

---

<div align="center"><img src="https://files.catbox.moe/q319ab.png" width="90" alt="Novero Logo" /><br /><br />

Made with ❤️ by <b>NoveroJava</b>

<br /><b>@noverojava/libsignal-node</b>

<br /><br />

⭐ Star the repository if you find it useful.

</div>
