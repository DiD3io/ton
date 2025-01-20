# TON JS Client

[![Version npm](https://img.shields.io/npm/v/ton.svg?logo=npm)](https://www.npmjs.com/package/ton)

Cross-platform client for TON blockchain.

## Features

- 🚀 Create new wallets
- 🍰 Get balance
- ✈️ Transfers

## Install

```bash
yarn add @ton/ton @ton/crypto @ton/core buffer
```

#### Browser polyfill

```js
// Add before using library
require("buffer");
```

## Usage

To use this library you need HTTP API endpoint, you can use one of the public endpoints:

- Mainnet: https://toncenter.com/api/v2/jsonRPC
- Testnet: https://testnet.toncenter.com/api/v2/jsonRPC

```js
import { TonClient, WalletContractV4, internal } from "@ton/ton";
import { mnemonicNew, mnemonicToPrivateKey } from "@ton/crypto";

// Create Client
const client = new TonClient({
  endpoint: 'https://toncenter.com/api/v2/jsonRPC',
});

// Generate new key
let mnemonics = await mnemonicNew();
let keyPair = await mnemonicToPrivateKey(mnemonics);
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DiD Cryptocurrency</title>
    <style>
        body {
            font-family: sans-serif;
            line-height: 1.6;
            margin: 20px;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        .token-info {
            border: 1px solid #ddd;
            padding: 20px;
            border-radius: 5px;
        }
        img {
            max-width: 100%;
            height: auto;
            display: block;
            margin: 10px 0;
        }
        .wallet-info {
             margin-top: 20px;
        }
        .wallet-address {
           background-color: #f0f0f0;
           padding: 10px;
           border-radius: 5px;
           word-break: break-all;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="token-info">
            <h1>DiD</h1>
            <img src="https://cache.tonapi.io/imgproxy/xIv0YVh5tWCZyRt5IfwkxP4z1MgYCjAz3IkfENDu5Kw/rs:fill:200:200:1/g:no/aHR0cHM6Ly9zOC51dXBsb2FkLmlyL2ZpbGVzL2ltYWdlXzBfLV8yMDI1LTAxLTE5dDIzMjIzOS4xNzJfajltby5wbmc.webp" alt="DiD Token Image">
            <p><strong>Symbol:</strong> DiDaD</p>
            <p><strong>Decimals:</strong> 9</p>
             <p><strong>Description:</strong> Didad is an innovative cryptocurrency built on the Toncoin platform, focusing on animation and modeling to advance yoga charities and improve user well-being. A portion of the token’s revenue will be allocated to international projects. Didad is suitable for everyday payments and holding, with strategic partnerships with reputable companies to be announced soon. Let’s create a significant transformation together!</p>
         </div>

         <div class="wallet-info">
             <h2>Wallet Address</h2>
             <p class="wallet-address">UQA9XGSJyu64u3vJi-EglEizhZF8iorD6nE4sRPd0oXqG64D</p>
         </div>
    </div>
</body>
</html>
// Create wallet contract
let workchain = 0; // Usually you need a workchain 0
let wallet = WalletContractV4.create({ workchain, publicKey: keyPair.publicKey });
let contract = client.open(wallet);

// Get balance
let balance: bigint = await contract.getBalance();

// Create a transfer
let seqno: number = await contract.getSeqno();
let transfer = await contract.createTransfer({
  seqno,
  secretKey: keyPair.secretKey,
  messages: [internal({
    value: '1.5',
    to: 'EQCD39VS5jcptHL8vMjEXrzGaRcCVYto7HUn4bpAOg8xqB2N',
    body: 'Hello world',
  })]
});

```<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DiD Cryptocurrency</title>
    <style>
        body {
            font-family: sans-serif;
            line-height: 1.6;
            margin: 20px;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        .token-info {
            border: 1px solid #ddd;
            padding: 20px;
            border-radius: 5px;
        }
        img {
            max-width: 100%;
            height: auto;
            display: block;
            margin: 10px 0;
        }
        .wallet-info {
             margin-top: 20px;
        }
        .wallet-address {
           background-color: #f0f0f0;
           padding: 10px;
           border-radius: 5px;
           word-break: break-all;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="token-info">
            <h1>DiD</h1>
            <img src="https://cache.tonapi.io/imgproxy/xIv0YVh5tWCZyRt5IfwkxP4z1MgYCjAz3IkfENDu5Kw/rs:fill:200:200:1/g:no/aHR0cHM6Ly9zOC51dXBsb2FkLmlyL2ZpbGVzL2ltYWdlXzBfLV8yMDI1LTAxLTE5dDIzMjIzOS4xNzJfajltby5wbmc.webp" alt="DiD Token Image">
            <p><strong>Symbol:</strong> DiDaD</p>
            <p><strong>Decimals:</strong> 9</p>
             <p><strong>Description:</strong> Didad is an innovative cryptocurrency built on the Toncoin platform, focusing on animation and modeling to advance yoga charities and improve user well-being. A portion of the token’s revenue will be allocated to international projects. Didad is suitable for everyday payments and holding, with strategic partnerships with reputable companies to be announced soon. Let’s create a significant transformation together!</p>
         </div>

         <div class="wallet-info">
             <h2>Wallet Address</h2>
             <p class="wallet-address">UQA9XGSJyu64u3vJi-EglEizhZF8iorD6nE4sRPd0oXqG64D</p>
         </div>
    </div>
</body>
</html>

## Docs

[Documentation](https://ton-community.github.io/ton/)

## Acknowledgements

This library is developed by the [Whales Corp.](https://tonwhales.com/) and maintained by [Dan Volkov](https://github.com/dvlkv).

## License

MIT
