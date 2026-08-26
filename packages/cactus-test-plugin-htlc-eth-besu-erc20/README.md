# @hyperledger-cacti/cactus-test-plugin-htlc-eth-besu-erc20

## Overview

Dedicated integration-test package for the [Besu ERC-20 HTLC plugin](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-htlc-eth-besu-erc20). It validates ERC-20 hash time-locked contract workflows without introducing circular test dependencies into the plugin package.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required to provision the Besu test ledger.

## API Summary

This package does not expose a production API. Its integration suites exercise the ERC-20 HTLC plugin with the [Besu ledger connector](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-ledger-connector-besu), API server, keychain, and test-ledger tooling.

## Usage

Use the suites under src/test/typescript/integration as examples of deploying the ERC-20 HTLC contract and invoking its plugin endpoints.

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
