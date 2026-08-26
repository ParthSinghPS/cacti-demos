# @hyperledger-cacti/cactus-test-cmd-api-server

## Overview

Dedicated integration-test package for [@hyperledger-cacti/cactus-cmd-api-server](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-cmd-api-server). The separate package avoids circular test dependencies between the API server and the plugins and clients used to exercise it.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required by integration tests that provision ledger or service containers.

## API Summary

This package does not expose a production API. Its test suites exercise API server configuration, plugin loading, generated clients, and endpoint behavior using packages from the [main Cacti repository](https://github.com/hyperledger-cacti/cacti/tree/main/packages).

## Usage

Use the test sources under src/test/typescript as examples of starting and configuring the Cacti API server in an integration environment.

## Testing

The package contains unit and integration test sources but does not define a standalone Jest script in the current demos workspace. Validate compilation and repository checks from the root:

```bash
yarn run build:dev:backend
yarn run lint
```

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
