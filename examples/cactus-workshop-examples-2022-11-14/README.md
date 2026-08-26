# @hyperledger-cacti/cactus-workshop-examples-2022-11-14

## Overview

Source examples from the Hyperledger workshop on blockchain interoperability with Cacti. The package demonstrates a minimal API server, a consortium configuration, and programmatic test-ledger provisioning.

Workshop materials: https://wiki.hyperledger.org/display/events/Blockchain+Interoperability+with+Hyperledger+Cacti

### Target Audience

- [x] Application developers
- [x] Contributors
- [ ] Operators

> These examples are educational. They are not production-ready, and the hello-world example does not sanitize user input.

## Install

From the cacti-demos repository root:

```bash
yarn install
```

Some examples provision containers and require Docker.

## API Summary

This package is executable workshop material and does not expose a reusable public API.

The examples use Cacti packages including:

- [Cacti API server](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-cmd-api-server)
- [Cacti Core](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-core)
- [IPFS object-store plugin](https://github.com/hyperledger-cacti/cacti/tree/main/extensions/cactus-plugin-object-store-ipfs)

## Usage

### Hello World

src/main/typescript/hello-world.ts starts an API server on port 3001 with the IPFS object-store plugin:

```bash
npx ts-node src/main/typescript/hello-world.ts
```

The plugin endpoints include:

- POST /api/v1/plugins/@hyperledger-cacti/cactus-plugin-object-store-ipfs/set-object
- POST /api/v1/plugins/@hyperledger-cacti/cactus-plugin-object-store-ipfs/get-object
- POST /api/v1/plugins/@hyperledger-cacti/cactus-plugin-object-store-ipfs/has-object

The endpoint payload values are encoded as expected by the plugin API.

### Simple Consortium

src/main/typescript/simple-consortium.ts creates a simple Cacti consortium:

```bash
npx ts-node src/main/typescript/simple-consortium.ts
```

### Substrate Test Ledger

src/main/typescript/test-ledger.ts creates a Substrate test ledger programmatically:

```bash
npx ts-node src/main/typescript/test-ledger.ts
```

## Testing

The package does not define an automated test script. From the repository root, validate that the workshop sources compile and satisfy repository checks with:

```bash
yarn run build:dev:backend
yarn run lint
```

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## Authors

- Rafael Belchior
- Mónica Gomez
- Abhinav Srivastava
- André Augusto
