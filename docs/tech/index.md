---
title: Tech Stack
layout: default
nav_order: 3
description: "Tepe is an app that lets you use blockchain tokens to encrypt, own, and share your files."
---

# Tech Stack

Tepe is built on three core decentralized technologies: decentralized storage, decentralized key management, and decentralized ledgers.

1. **Decentralized storage**: Tepe stores your files on [Arweave](https://arweave.org), a decentralized network that uses a consensus algorithm called Proof-of-Access. This allows users to pay a one-time fee to store data permanently on the network. To use Arweave, we use [Irys](https://irys.xyz), a provenance network that serves as an abstraction layer on top of Arweave. We plan to let users choose between multiple storage endpoints in the future, including IPFS, Google Cloud, and Amazon S3.

2. **Decentralized key management**: Tepe does not store your keys. Instead, it uses a decentralized key management network called [Lit Protocol](https://litprotocol.com). Lit is a decentralized key management network that uses secure [multi-party computation](https://en.wikipedia.org/wiki/Secure_multi-party_computation) (MPC) and [threshold signature schemes](https://en.wikipedia.org/wiki/Threshold_cryptosystem) (TSS). So no one node can ever have access to your keys. But to add to that, Lit also uses AMD’s [Secure Encrypted Virtualization](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf) (SEV), which ensures that node operators never have access to any key shares directly, nor the computation processed inside of each node. Finally, decryption takes place entirely on the client side (ie, on the Tepe web app), so Tepe servers never have access to your keys or your decrypted files.

3. **Decentralized ledgers**: Records of ownership are stored on blockchains, which are decentralized ledgers. Tepe uses [Ethereum](https://ethereum.org) and [Polygon](https://polygon.technology/) to store records of ownership. The Lit Protocol directly asks the blockchains when providing the decryption key to the Tepe client. We plan to support more blockchains in the future, including [Solana](https://solana.com/).

### On-chain vs Off-chain

Tepe uses a multi-faceted approach to storing data. Files are stored off-chain on Arweave, but the records of ownership are stored on-chain on Ethereum and Polygon. This allows us to keep the cost of ownership low, while still ensuring that ownership records are immutable and decentralized.

Tepe stores the following on a traditional database:
1. encrypted file information, including their Lit-encrypted decryption keys, their Arweave URLs, and the NFTs used for encryption and
2. profile information, including usernames, Ethereum addresses, and profile pictures.

We use [Sign-in with Ethereum](https://login.xyz/) for authentication, so we do not store passwords. We plan to eventually store this data on-chain as well, but for now, we are using a traditional database.
