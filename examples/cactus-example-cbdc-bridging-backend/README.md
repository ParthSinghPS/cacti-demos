# @hyperledger-cacti/cactus-example-cbdc-bridging-backend

## Overview

Backend for the CBDC bridging example. It demonstrates an asset transfer workflow between Hyperledger Fabric and Hyperledger Besu using Cacti ledger connectors, SATP Hermes gateways, keychain storage, and IPFS-backed object storage.

### Target Audience

- [x] Application developers
- [x] Contributors
- [ ] Operators

> This application is an integration example and is not production-ready.

## Install

Use Node.js 20.20.0 and install dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required because the example provisions test ledger infrastructure.

## Configuration

The process.env file in this directory defines the local service addresses and ports:

| Variable                  | Purpose                               |
| :------------------------ | :------------------------------------ |
| API_HOST                  | Hostname used by the backend services |
| API_SERVER_1_PORT         | Fabric connector API port             |
| API_SERVER_2_PORT         | Besu connector API port               |
| API_GATEWAY_1_BLO_PORT    | Gateway 1 OpenAPI service port        |
| API_GATEWAY_2_BLO_PORT    | Gateway 2 OpenAPI service port        |
| API_GATEWAY_1_CLIENT_PORT | Gateway 1 SATP client port            |
| API_GATEWAY_2_CLIENT_PORT | Gateway 2 SATP client port            |
| API_GATEWAY_1_SERVER_PORT | Gateway 1 SATP server port            |
| API_GATEWAY_2_SERVER_PORT | Gateway 2 SATP server port            |

Review the file before changing ports because the frontend and integration tests expect compatible endpoint values.

## API Summary

The package exports CbdcBridgingApp and its options. Its HTTP contract is defined in src/main/yml/openapi.yml and generated into the TypeScript sources during the repository build.

The example integrates these Cacti packages:

- [Cacti API client](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-api-client)
- [Cacti API server](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-cmd-api-server)
- [Besu connector](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-ledger-connector-besu)
- [Fabric connector](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-ledger-connector-fabric)
- [SATP Hermes](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-satp-hermes)
- [IPFS object store](https://github.com/hyperledger-cacti/cacti/tree/main/extensions/cactus-plugin-object-store-ipfs)

## Usage

Start the backend from the repository root:

```bash
yarn workspace @hyperledger-cacti/cactus-example-cbdc-bridging-backend run start
```

Wait for CbdcBridgingApp running... before starting the frontend or integration tests.

### Debugging in Visual Studio Code

1. Open .vscode/template.launch.json.
2. Copy the Example: CBDC Bridging Fabric-EVM App configuration into .vscode/launch.json.
3. Select that configuration in Run and Debug.
4. Start the debugger and wait for the backend startup message.

## Testing

Run the Cucumber suite:

```bash
yarn workspace @hyperledger-cacti/cactus-example-cbdc-bridging-backend run test
```

Run the Jest integration suite:

```bash
yarn workspace @hyperledger-cacti/cactus-example-cbdc-bridging-backend run test:integration
```

These tests provision external services and require Docker.

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
