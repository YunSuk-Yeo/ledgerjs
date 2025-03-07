**[We are hiring, join us! 👨‍💻👩‍💻](https://jobs.lever.co/ledger/?department=Engineering)**


<img src="https://user-images.githubusercontent.com/3273751/151214602-f5153588-1911-4456-ae65-604d56821b36.png" height="80" /> <img src="https://user-images.githubusercontent.com/211411/52533081-e679d380-2d2e-11e9-9c5e-571e4ad0107b.png" height="80" />

[![Ledger Devs Slack](https://img.shields.io/badge/Slack-LedgerDevs-yellow.svg?style=flat)](https://ledger-dev.slack.com/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Welcome to Ledger's JavaScript libraries.

**See also:**

- [Changelog](https://github.com/LedgerHQ/ledgerjs/releases)
- [**LedgerJS examples**](https://github.com/LedgerHQ/ledgerjs-examples)
- [Ledger Live Desktop](https://github.com/ledgerhq/ledger-live-desktop)
- [Ledger Live Mobile](https://github.com/ledgerhq/ledger-live-mobile)
- [live-common](https://github.com/ledgerhq/ledger-live-common)
- Deprecated libraries are archived in https://github.com/LedgerHQ/ledgerjs-legacy

## `@ledgerhq/hw-transport-*`

**To communicate with a Ledger device, you first need to identify which transport(s) to use.**

> The _hw-transport_ libraries implement communication protocol for our [hardware wallet devices](https://www.ledger.com/) (Ledger Nano / Ledger Nano S / Ledger Nano X / Ledger Blue) in many platforms: **Web, Node, Electron, React Native,...** and using many different communication channels: **U2F, HID, WebUSB, Bluetooth,...**

| Channels | U2F/WebAuthn | HID | WebUSB | Bluetooth |
|----------|--------------|-----|--------|-----------|
| Blue     | DEPRECATED<sup>1</sup> | YES | NO     | NO        |
| Nano S   | DEPRECATED<sup>1</sup> | YES | YES    | NO        |
| Nano X   | DEPRECATED<sup>1</sup> | YES | YES    | YES       |

1. U2F is deprecated. See https://github.com/LedgerHQ/ledgerjs/blob/master/docs/migrate_webusb.md

Summary of implementations available per platform


|    Platforms     |  U2F/WebAuthn    |                HID                |       WebUSB        |           Bluetooth           |
|------------------|------------------|-----------------------------------|---------------------|-------------------------------|
| Web              | `@ledgerhq/hw-transport-u2f` | `@ledgerhq/hw-transport-webhid` | `@ledgerhq/hw-transport-webusb` | `@ledgerhq/hw-transport-web-ble`          |
| Electron/Node.js | NO               | `@ledgerhq/hw-transport-node-hid`<sup>1</sup> | NO                  | `@ledgerhq/hw-transport-node-ble`         |
| iOS              | NO               | NO                                | NO                  | `@ledgerhq/react-native-hw-transport-ble` |
| Android          | `@ledgerhq/hw-transport-u2f`<sup>2</sup> | `@ledgerhq/react-native-hid`                  | `@ledgerhq/hw-transport-webusb`<sup>2</sup>    | `@ledgerhq/react-native-hw-transport-ble` |

1. 3 implementations available
2. via Android Chrome

**Beware the current web support:**


| Channels | U2F               | WebHID.         | WebUSB             | WebBluetooth |
|----------|-------------------|-----------------|--------------------|--------------|
| Windows  | DEPRECATED<sup>1</sup> | YES             | OK BUT<sup>2</sup> | YES          |
| Mac      | DEPRECATED<sup>1</sup> | YES             | YES                | YES          |
| Linux    | DEPRECATED<sup>1</sup> | YES             | YES                | YES          |
| Chrome   | DEPRECATED<sup>1</sup> | YES<sup>3</sup> | YES                | YES          |
| Safari   | DEPRECATED<sup>1</sup> | NO              | NO                 | NO           |
| Firefox  | DEPRECATED<sup>1</sup> | NO              | NO                 | NO           |
| IE.      | DEPRECATED<sup>1</sup> | NO              | NO                 | NO           |


1. U2F is deprecated. See https://github.com/LedgerHQ/ledgerjs/blob/master/docs/migrate_webusb.md
2. instabilities has been reported
3. WebHID supported under _Chrome experimental flags_


**Please find respective documentation for each transport:**

- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-u2f.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-u2f) [@ledgerhq/hw-transport-u2f](https://github.com/LedgerHQ/ledgerjs-legacy/tree/master/packages/hw-transport-u2f) **[Web]** **(U2F)** (legacy but reliable) – FIDO U2F api. [check browser support](https://caniuse.com/u2f).
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-webauthn.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-webauthn) [@ledgerhq/hw-transport-webauthn](https://github.com/LedgerHQ/ledgerjs-legacy/tree/master/packages/hw-transport-webauthn) **[Web]** **(WebAuthn)** (experimental) – WebAuthn api. [check browser support](https://caniuse.com/webauthn).
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-webusb.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-webusb) [@ledgerhq/hw-transport-webusb](./packages/hw-transport-webusb) **[Web]** **(WebUSB)** – WebUSB [check browser support](https://caniuse.com/webusb).
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-webhid.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-webhid) [@ledgerhq/hw-transport-webhid](./packages/hw-transport-webhid) **[Web]** **(WebHID)** – WebHID [check browser support](https://caniuse.com/webhid).
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-web-ble.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-web-ble) [@ledgerhq/hw-transport-web-ble](./packages/hw-transport-web-ble) **[Web]** **(Bluetooth)** – [check browser support](https://caniuse.com/web-bluetooth).
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-node-hid.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-node-hid) [@ledgerhq/hw-transport-node-hid](./packages/hw-transport-node-hid) **[Node]**/Electron **(HID)** – historical implementation – uses `node-hid` and `usb`.
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-node-hid-noevents.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-node-hid-noevents) [@ledgerhq/hw-transport-node-hid-noevents](./packages/hw-transport-node-hid-noevents) **[Node]**/Electron **(HID)** – uses **only** `node-hid`. Does not provide USB events.
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-node-hid-singleton.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-node-hid-singleton) [@ledgerhq/hw-transport-node-hid-singleton](./packages/hw-transport-node-hid-singleton) **[Node]**/Electron **(HID)** – uses `node-hid` and `usb-detection`. Focus on supporting one device at a time (potentially will have more robust events and less blocking cases)
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-node-ble.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-node-ble) [@ledgerhq/hw-transport-node-ble](./packages/hw-transport-node-ble) **[Node]**/Electron **(BLE)** (experimental) – uses `@abandonware/noble`.
- [![npm](https://img.shields.io/npm/v/@ledgerhq/react-native-hw-transport-ble.svg)](https://www.npmjs.com/package/@ledgerhq/react-native-hw-transport-ble) [@ledgerhq/react-native-hw-transport-ble](./packages/react-native-hw-transport-ble) **[React Native]** **(Bluetooth)** – uses `react-native-ble-plx`
- [![npm](https://img.shields.io/npm/v/@ledgerhq/react-native-hid.svg)](https://www.npmjs.com/package/@ledgerhq/react-native-hid) [@ledgerhq/react-native-hid](./packages/react-native-hid) **[React Native]** **(HID)** _Android_ – Ledger's native implementation
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-http.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-http) [@ledgerhq/hw-transport-http](./packages/hw-transport-http) **[DEV only]** universal HTTP channel. **NOT for PROD**.

### An unified _Transport_ interface

All these transports implement a generic interface exposed by
[@ledgerhq/hw-transport](./packages/hw-transport).
There are specifics for each transport which are explained in each package.

A Transport is essentially:

- `Transport.listen: (observer)=>Subscription`
- `Transport.open: (descriptor)=>Promise<Transport>`
- `transport.exchange(apdu: Buffer): Promise<Buffer>`
- `transport.close()`

and some derivates:

- `transport.create(): Promise<Transport>`: make use of `listen` and `open` for the most simple scenario.
- `transport.send(cla, ins, p1, p2, data): Promise<Buffer>`: a small abstraction of `exchange`

> NB: [APDU](https://en.wikipedia.org/wiki/Smart_card_application_protocol_data_unit) is the encoding primitive for all binary exchange with the devices. (it comes from smart card industry)

## `@ledgerhq/hw-app-*`

As soon as your _Transport_ is created, you can already communicate by implementing the apps protocol (refer to application documentations, for instance [BTC app](https://github.com/LedgerHQ/ledger-app-btc/blob/master/doc/btc.asc) and [ETH app](https://github.com/LedgerHQ/ledger-app-eth/blob/master/doc/ethapp.asc) ones).

We also provide libraries that help implementing the low level exchanges. These higher level APIs are split per app:

- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-app-eth.svg)](https://www.npmjs.com/package/@ledgerhq/hw-app-eth) [@ledgerhq/hw-app-eth](./packages/hw-app-eth): Ethereum Application API
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-app-btc.svg)](https://www.npmjs.com/package/@ledgerhq/hw-app-btc) [@ledgerhq/hw-app-btc](./packages/hw-app-btc): Bitcoin Application API
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-app-xrp.svg)](https://www.npmjs.com/package/@ledgerhq/hw-app-xrp) [@ledgerhq/hw-app-xrp](./packages/hw-app-xrp): Ripple Application API
- [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-app-str.svg)](https://www.npmjs.com/package/@ledgerhq/hw-app-str) [@ledgerhq/hw-app-str](./packages/hw-app-str): Stellar Application API

**Community packages:**

- [![npm](https://img.shields.io/npm/v/@cardano-foundation/ledgerjs-hw-app-cardano.svg)](https://www.npmjs.com/package/@cardano-foundation/ledgerjs-hw-app-cardano) [@cardano-foundation/ledgerjs-hw-app-cardano](https://github.com/cardano-foundation/ledgerjs-hw-app-cardano): Cardano ADA Application API

- [![npm](https://img.shields.io/npm/v/ledger-cosmos-js.svg)](https://www.npmjs.com/package/ledger-cosmos-js) [ledger-cosmos-js](https://github.com/cosmos/ledger-cosmos-js): Cosmos/Tendermint Application API

## Other packages

### Published Packages

| Package                                                                  | Version                                                                                                                                       | Description                                                                                                  |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| [`create-dapp`](https://github.com/LedgerHQ/ledgerjs-legacy/tree/master/packages/create-dapp)                                   | [![npm](https://img.shields.io/npm/v/create-dapp.svg)](https://www.npmjs.com/package/create-dapp)                                             | Ledger DApp Ethereum starter kit                                                                             |
| [`@ledgerhq/web3-subprovider`](https://github.com/LedgerHQ/ledgerjs-legacy/tree/master/packages/web3-subprovider)               | [![npm](https://img.shields.io/npm/v/@ledgerhq/web3-subprovider.svg)](https://www.npmjs.com/package/@ledgerhq/web3-subprovider)               | web3 subprovider implementation for web3-provider-engine                                                     |
| **Development Tools**                                                    |
| [`@ledgerhq/hw-transport-mocker`](/packages/hw-transport-mocker)         | [![npm](https://img.shields.io/npm/v/@ledgerhq/hw-transport-mocker.svg)](https://www.npmjs.com/package/@ledgerhq/hw-transport-mocker)         | Tool used for test to record and replay APDU calls.                                                          |

## Basic gist

```js
import Transport from "@ledgerhq/hw-transport-node-hid";
// import Transport from "@ledgerhq/hw-transport-webusb";
// import Transport from "@ledgerhq/react-native-hw-transport-ble";
import AppBtc from "@ledgerhq/hw-app-btc";
const getBtcAddress = async () => {
  const transport = await Transport.create();
  const btc = new AppBtc(transport);
  const result = await btc.getWalletPublicKey("44'/0'/0'/0/0");
  return result.bitcoinAddress;
};
getBtcAddress().then(a => console.log(a));
```

## Contributing

Please read our [contribution guidelines](./CONTRIBUTING.md) before getting
started.

**You need to have a recent [Node.js](https://nodejs.org/) and
[Yarn](https://yarnpkg.com/) installed.**

### Install dependencies

```bash
yarn
```

### Build

Build all packages

```bash
yarn build
```

### Watch

Watch all packages change. Very useful during development to build only file that changes.

```bash
yarn watch
```

### Lint

Lint all packages

```bash
yarn lint
```

### Run Tests

First of all, this ensure the libraries are correctly building, and passing lint and flow:

```
yarn test
```

**then to test on a real device...**

Plug a device like the Nano S and open Bitcoin app.

Then run the test and accept the commands on the devices for the tests to
continue.

```bash
yarn test-node
```

You can also test on the web:

```bash
yarn test-browser
```

> make sure to configure your device app with "Browser support" set to "YES".

### Deploy

Checklist before deploying a new release:

- you have the right in the LedgerHQ org on NPM
- you have run `npm login` once (check `npm whoami`)
- Go to **master** branch
  - your master point on LedgerHQ repository (check with `git config remote.$(git config branch.master.remote).url` and fix it with `git branch --set-upstream master origin/master`)
  - you are in sync (`git pull`) and there is no changes in `git status`
- Run `yarn` once, there is still no changes in `git status`

**deploy a new release**

```
 yarn run publish
```

then, go to [/releases](https://github.com/LedgerHQ/ledgerjs/releases) and create a release with change logs.

**alternatively:**

deploy a canary release (beta, etc)

```
 yarn run publish -c
```

> NB: if there is a new package, AFAIK you need to manually `npm publish` it once on NPM.

## VSCode settings 

Here is a example config for a workspace file to handle the monorepo setup.  
Just add `project.code-workspace` to your `.vscode` folder

```json
{
  "folders": [
    {
      "name": "root",
      "path": "../"
    },
    {
      "name": "cryptoassets",
      "path": "../packages/cryptoassets"
    },
    {
      "name": "devices",
      "path": "../packages/devices"
    },
    {
      "name": "errors",
      "path": "../packages/errors"
    },
    {
      "name": "hw-app-algorand",
      "path": "../packages/hw-app-algorand"
    },
    {
      "name": "hw-app-btc",
      "path": "../packages/hw-app-btc"
    },
    {
      "name": "hw-app-cosmos",
      "path": "../packages/hw-app-cosmos"
    },
    {
      "name": "hw-app-eth",
      "path": "../packages/hw-app-eth"
    },
    {
      "name": "hw-app-polkadot",
      "path": "../packages/hw-app-polkadot"
    },
    {
      "name": "hw-app-str",
      "path": "../packages/hw-app-str"
    },
    {
      "name": "hw-app-terra",
      "path": "../packages/hw-app-terra"
    },
    {
      "name": "hw-app-tezos",
      "path": "../packages/hw-app-tezos"
    },
    {
      "name": "hw-app-trx",
      "path": "../packages/hw-app-trx"
    },
    {
      "name": "hw-app-xrp",
      "path": "../packages/hw-app-xrp"
    },
    {
      "name": "hw-transport",
      "path": "../packages/hw-transport"
    },
    {
      "name": "hw-transport-http",
      "path": "../packages/hw-transport-http"
    },
    {
      "name": "hw-transport-mocker",
      "path": "../packages/hw-transport-mocker"
    },
    {
      "name": "hw-transport-node-ble",
      "path": "../packages/hw-transport-node-ble"
    },
    {
      "name": "hw-transport-node-hid",
      "path": "../packages/hw-transport-node-hid"
    },
    {
      "name": "hw-transport-node-hid-noevents",
      "path": "../packages/hw-transport-node-hid-noevents"
    },
    {
      "name": "hw-transport-node-hid-singleton",
      "path": "../packages/hw-transport-node-hid-singleton"
    },
    {
      "name": "hw-transport-node-speculos",
      "path": "../packages/hw-transport-node-speculos"
    },
    {
      "name": "hw-transport-web-ble",
      "path": "../packages/hw-transport-web-ble"
    },
    {
      "name": "hw-transport-webhid",
      "path": "../packages/hw-transport-webhid"
    },
    {
      "name": "hw-transport-webusb",
      "path": "../packages/hw-transport-webusb"
    },
    {
      "name": "logs",
      "path": "../packages/logs"
    },
    {
      "name": "react-native-hid",
      "path": "../packages/react-native-hid"
    },
    {
      "name": "react-native-hw-transport-ble",
      "path": "../packages/react-native-hw-transport-ble"
    }
  ],
}
```

