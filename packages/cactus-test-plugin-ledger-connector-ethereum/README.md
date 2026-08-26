# @hyperledger-cacti/cactus-test-plugin-ledger-connector-ethereum

## Overview

Dedicated test package for the [Ethereum connector](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-ledger-connector-ethereum). Separating the tests prevents circular dependencies between the connector and the API, keychain, and ledger fixtures used to exercise it.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required by the integration suite.

## API Summary

This package does not expose a production API. Its unit and integration suites validate Ethereum connector behavior and its interaction with the surrounding Cacti services.

## Usage

Use the sources under src/test/typescript as examples of configuring the Ethereum connector and submitting requests through its generated client.

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
