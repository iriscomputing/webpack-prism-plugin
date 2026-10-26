# @iris-os/webpack-prism-plugin (webpack-prism-plugin)

> **Zero-disk, encrypted in-memory browser enclave and optical shard packager for Webpack.**

[![npm version](https://img.shields.io/badge/npm-v1.0.0-cb3837.svg)](#)
[![License: Proprietary / Commercial](https://img.shields.io/badge/license-Commercial-b829ff.svg)](#)
[![Security: AES-256-GCM](https://img.shields.io/badge/security-AES--256--GCM-00f0ff.svg)](#)

A production Webpack plugin that transmutes JavaScript and React bundles into encrypted optical shard containers. At runtime, the client decrypts and evaluates code strictly inside volatile browser RAM using the Web Crypto API (`crypto.subtle`) and ephemeral blob descriptors—ensuring proprietary code and algorithms never persist to local disk or cache.

---

## Key Features

- **Zero-Disk In-Memory Execution**: Plaintext source code is never stored in local storage, disk cache, or unencrypted assets.
- **AES-256-GCM Shard Packaging**: Protects production bundles against client-side tampering and reverse engineering.
- **Drop-In Integration**: Hooks seamlessly into standard Webpack 4/5 production build pipelines with zero changes to your React/Node source code.
- **Compliant & Standards-Based**: Uses standard W3C Web Cryptography APIs, requiring zero third-party browser extensions or external native runtimes.

---

## Installation

```bash
npm install --save-dev @iris-os/webpack-prism-plugin
```

---

## Quickstart

Add to your `webpack.config.js`:

```javascript
const path = require('path');
const IrisPrismWebpackPlugin = require('@iris-os/webpack-prism-plugin');

module.exports = {
  mode: 'production',
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name].[contenthash].js',
  },
  plugins: [
    new IrisPrismWebpackPlugin({
      enabled: process.env.NODE_ENV === 'production',
      encryptBundles: true,             // Transmutes JS code into AES-256-GCM optical shards
      generateOpticalShards: true,      // Builds optical density matrices and Merkle leaves
      targetChunks: [/main/, /app/],    // Targeted chunk regex
      authorDid: 'did:key:picard-sovereign-root-v1',
    }),
  ],
};
```

---

## Corporate & Legal Notice

Copyright &copy; 2026 **Campfire Creative LLC DBA Iris Computing**. All rights reserved.
