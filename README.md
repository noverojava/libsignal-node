<div align="center"><img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=32&pause=1000&color=A855F7&center=true&vCenter=true&width=750&lines=%40noverojava%2Flibsignal-node;Signal+Protocol+for+Node.js;Created+and+Maintained+by+noverojava" alt="noverojava libsignal typing banner" /><br/><img src="https://files.catbox.moe/q319ab.png" width="150" alt="noverojava Logo" />@noverojava/libsignal-node

A powerful Signal Protocol implementation for Node.js.

Built for secure session management, identity keys, PreKeys, signed PreKeys, and encrypted messaging environments.

Fast • Secure • Modern • Extensible

""npm version" (https://img.shields.io/npm/v/%40noverojava%2Flibsignal-node?color=A855F7&label=npm)" (https://www.npmjs.com/package/@noverojava/libsignal-node)
""npm downloads" (https://img.shields.io/npm/dt/%40noverojava%2Flibsignal-node?color=blue&label=downloads)" (https://www.npmjs.com/package/@noverojava/libsignal-node)
""License" (https://img.shields.io/badge/license-GPL--3.0-blue.svg)" (LICENSE)
""Node.js" (https://img.shields.io/badge/node-%3E%3D18-brightgreen.svg)" (package.json)

</div>---

«📖 New here?

"@noverojava/libsignal-node" provides Signal Protocol functionality for Node.js applications requiring secure session establishment and encrypted communication.»

---

✨ Overview

"@noverojava/libsignal-node" is a Node.js implementation based on the concepts and architecture of the Signal Protocol.

The Signal Protocol provides a ratcheting forward secrecy system designed for both synchronous and asynchronous messaging environments.

The library manages important cryptographic session components including:

- 🔐 Identity Keys
- 🔑 PreKeys
- ✍️ Signed PreKeys
- 🔄 Session Records
- 📦 PreKey Bundles
- 💬 PreKey Signal Messages
- 🛡️ Forward Secrecy
- 🔒 Session Encryption

---

📦 Installation

Install using npm:

npm install @noverojava/libsignal-node

Or using Yarn:

yarn add @noverojava/libsignal-node

Or pnpm:

pnpm add @noverojava/libsignal-node

---

🚀 Quick Start

Example:

const libsignal = require('@noverojava/libsignal-node');

console.log(
    'libsignal-node loaded successfully'
);

For ES Modules:

import libsignal from '@noverojava/libsignal-node';

console.log(
    'Signal Protocol ready'
);

---

🔐 Signal Protocol

The Signal Protocol is designed around secure sessions between communicating clients.

Once a session has been established, it can be reused for future encrypted communication.

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
   │
   ▼
Forward Secrecy

---

🔑 PreKeys

This protocol uses a concept called PreKeys.

A PreKey consists of an Elliptic Curve public key and a unique identifier.

PreKeys are stored by a server and can later be retrieved by clients that want to establish a secure session.

At installation or registration time, clients generally generate:

- One Signed PreKey
- Multiple unsigned PreKeys
- Identity Keys

These keys can then be uploaded to a server.

Client
   │
   ├── Identity Key
   │
   ├── Signed PreKey
   │
   └── PreKey Collection
          │
          ▼
        Server

---

✍️ Signed PreKeys

A Signed PreKey provides additional verification for session establishment.

The key is associated with the client's identity and cryptographically signed.

Typical usage:

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

Clients establish a secure session which is then used for subsequent encryption and decryption operations.

Once established, a session can continue to maintain its cryptographic state.

Sessions can be established in two primary ways.

1️⃣ PreKey Bundles

A client wishing to send a message can retrieve a recipient's PreKey Bundle.

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

---

2️⃣ PreKey Signal Messages

A client may receive a PreKey Signal Message.

That message can be used to establish a new secure session with the sender.

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

The protocol uses a ratcheting mechanism designed to improve message confidentiality.

Each session evolves as messages are exchanged.

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
   │
   ▼
Ratchet State C

This approach helps ensure that session keys continue to evolve over time.

---

💾 State Management

An established session contains important cryptographic state.

That state should be stored securely and maintained for the lifetime of the session.

The main state categories include:

State| Description
🔐 Identity State| Stores local and remote identity keys
🔑 PreKey State| Stores generated PreKeys
✍️ Signed PreKey State| Stores signed PreKeys
🔄 Session State| Stores established session information

---

🔐 Identity State

Clients maintain their own identity key pair.

They may also store identity keys belonging to other clients.

Identity State

├── Local Identity Key Pair
│
└── Remote Identity Keys

Identity information is an important part of establishing trusted communication.

---

🔑 PreKey State

Clients maintain generated PreKeys.

These keys can be used by other clients to initiate sessions.

PreKey Storage

├── PreKey #1
├── PreKey #2
├── PreKey #3
├── PreKey #4
└── ...

PreKeys may be consumed or replaced depending on the application's protocol implementation.

---

✍️ Signed PreKey State

Clients also maintain their signed PreKeys.

Signed PreKey

├── Public Key
├── Private Key
├── Signature
└── Key Identifier

Applications should securely store this information.

---

🔄 Session State

Session state contains the cryptographic information required for encrypted communication.

Session

├── Root Key
├── Chain Keys
├── Ratchet State
├── Remote Identity
└── Message Counters

Session records should be treated as sensitive cryptographic data.

---

📁 Example Storage Structure

An application may organize protocol state like this:

signal-data/

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

«⚠️ Storage implementation depends on your application.»

---

⚡ Performance

"@noverojava/libsignal-node" is intended for Node.js environments requiring cryptographic session functionality.

Recommended practices:

- Cache only required session information
- Persist session state safely
- Remove expired or unused records when appropriate
- Avoid exposing private keys
- Protect database backups containing cryptographic state
- Use secure storage for sensitive information

---

🧩 Integration

This library can be integrated into applications requiring Signal Protocol functionality.

Possible use cases include:

- 💬 Secure messaging systems
- 🔐 Encrypted communication services
- 📱 Multi-device messaging architectures
- 🖥️ Node.js backend services
- 🔑 Secure session management
- 🧩 Applications built on compatible Signal Protocol architectures

---

🔧 Requirements

Requirement| Version
Node.js| ">=18"
npm| Latest Recommended
Runtime| Node.js

---

📚 Original Project

This package is based on the original Signal Protocol JavaScript implementation.

Original project:

- libsignal-protocol-javascript
- Open Whisper Systems
- Forsta Labs

The original protocol implementation and its contributors deserve full credit for the foundational work.

---

🤝 Contributing

Contributions are welcome.

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Test your changes
5. Submit a Pull Request

Before contributing major changes, please ensure your implementation remains compatible with the intended protocol behavior.

---

📦 Publishing

Install dependencies:

npm install

Run tests:

npm test

Publish the package:

npm publish

---

⚠️ Security Notice

Cryptographic libraries should be used carefully.

Do not:

- ❌ Expose private keys
- ❌ Commit session data to GitHub
- ❌ Store identity keys in public databases
- ❌ Share PreKey private material
- ❌ Modify cryptographic primitives without proper review

Always protect sensitive session and identity information.

---

📜 License

This project is licensed under the GPL-3.0 License.

See:

LICENSE

for the complete license information.

Original license and copyright information are preserved.

---

📚 Credits

Original Protocol Work

- Open Whisper Systems
- Signal Protocol contributors
- Forsta Labs

Original Project

- libsignal-protocol-javascript
- libsignal-node

Maintained / Published By

noverojava

All credit for the original Signal Protocol implementation belongs to the original developers and contributors.

---

⚠️ Disclaimer

"@noverojava/libsignal-node" is not an official Signal product.

This package should be used responsibly and with proper understanding of cryptographic security.

Do not rely on modified cryptographic implementations without appropriate security review.

---

<div align="center"><img src="https://files.catbox.moe/q319ab.png" width="90" alt="noverojava Logo" /><br/>Made with ❤️ by noverojava

@noverojava/libsignal-node

⭐ Star the repository if you find it useful.

</div>---

«Note: This package is based on the original "libsignal-node" ecosystem and related Signal Protocol JavaScript implementations. Original licensing and copyright notices must remain included in the package where required.»