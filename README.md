# Challenge: Tokenization
> Mint and transfer ERC-721 NFTs with IPFS-hosted metadata deployed on Sepolia

[![Solidity](https://img.shields.io/badge/Solidity-0.8.20-363636?logo=solidity&logoColor=white)]()
[![Foundry](https://img.shields.io/badge/Built_with-Foundry-red)]()
[![Next.js](https://img.shields.io/badge/Frontend-Next.js-black?logo=next.js&logoColor=white)]()
[![Sepolia](https://img.shields.io/badge/Network-Sepolia-8A2BE2)]()

🔗 [Live Demo](https://srt-qwyn0ysc2-yuchenzhou1031-6631s-projects.vercel.app/) · 📋 [Speedrun Ethereum](https://speedrunethereum.com)

## What It Does

An NFT minting and transferring dApp built on ERC-721. Users mint tokens whose metadata (image, name, attributes) is uploaded to IPFS and stored on-chain as a URI. The frontend displays each user's holdings and lets them transfer tokens to any address.

## Real-World Relevance

- **ENS (Ethereum Name Service)** — domain names like `vitalik.eth` are ERC-721 tokens; the same standard that powers this dApp makes names programmable and composable across wallets and apps
- **Uniswap V3 LP positions** — each liquidity position is a unique NFT tracking a provider's share of a pool, showing how ERC-721 extends beyond images to represent financial state
- **Real-world asset tokenization** — stocks, bonds, and real estate can be represented as ERC-721 tokens; the on-chain transfer mechanism is the same pattern built here

## Contract Architecture

| Contract | Role |
|---|---|
| `YourCollectible.sol` | ERC-721 with Enumerable + URIStorage extensions; `mintItem(address, uri)` mints with an auto-incrementing ID and stores the IPFS URI on-chain |

## Key Concepts

- **ERC-721 Enumerable + URIStorage** — two OpenZeppelin extensions composed together; Enumerable enables `tokenOfOwnerByIndex` iteration, URIStorage stores per-token metadata URIs
- **IPFS metadata flow** — metadata is uploaded through a Next.js API route (`/api/ipfs/add`) before minting, keeping IPFS logic off the client and decoupled from the contract call
- **Cycling metadata** — `tokenIdCounter % nftsMetadata.length` selects from 6 predefined animal NFTs, demonstrating how counters drive deterministic on-chain behavior

## Local Setup

```bash
yarn chain    # start local Anvil blockchain
yarn deploy   # deploy YourCollectible to localhost
yarn start    # frontend at http://localhost:3000
```
