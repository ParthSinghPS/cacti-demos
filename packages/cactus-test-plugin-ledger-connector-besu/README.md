# @hyperledger-cacti/cactus-test-plugin-ledger-connector-besu

## Overview

Dedicated test package for the [Hyperledger Besu connector](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-ledger-connector-besu). It verifies connector behavior across ledger, API server, keychain, REST, and gRPC integration boundaries.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

> This package contains test infrastructure only. It is not intended for production deployments.

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required to provision the Besu test ledger.

## API Summary

This package does not expose a production API. Its suites validate the connector's REST and gRPC interfaces, transaction execution, contract operations, and integration with supporting Cacti plugins.

## Usage

Use the suites under src/test/typescript/integration as examples of configuring the Besu connector and invoking it through generated clients.

## Testing

The package contains integration test sources but does not define a standalone Jest script in the current demos workspace. Validate compilation and repository checks from the root:

```bash
yarn run build:dev:backend
yarn run lint
```

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
