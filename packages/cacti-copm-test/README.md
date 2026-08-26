# @hyperledger-cacti/cacti-copm-test

## Overview

Integration-test framework for the Cacti Operations Lifecycle Management Protocol (COPM) core package and its distributed-ledger-specific implementations. It provides common test abstractions and network-specific test setup for asset transfer and exchange workflows.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

The network setup requires Docker and the ledger-specific prerequisites used by the selected Makefile target.

## API Summary

The main abstractions are:

- TestAssets: issues bonds and tokens, resolves bond ownership, and reads token balances.
- CopmTester: creates a ledger-specific COPM plugin and exposes the parties, test assets, and gRPC clients used by the suites.
- WeaverInteropConfiguration: describes the Weaver interoperability environment used by the tests.

A new ledger implementation should implement TestAssets and CopmTester, then register its tester with the COPM tester factory.

Relevant Cacti packages:

- [COPM core](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cacti-copm-core)
- [COPM Corda implementation](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cacti-plugin-copm-corda)
- [COPM Fabric implementation](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cacti-plugin-copm-fabric)
- [Corda connector](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-plugin-ledger-connector-corda)

## Usage

The Makefile builds the Weaver components and ledger networks used by the tests. Ledger-specific Makefile_<ledger_type> files provide:

- make setup: build the Weaver components.
- make pledge-network: prepare a pledge and claim asset-transfer network.
- make lock-network: prepare a lock and claim asset-exchange network.

The pledge and lock network modes are mutually exclusive.

## Testing

Integration suites are located under src/test/typescript/integration. The package declares test, test:lock, test:pledge, and test:view scripts, but those scripts currently reference a top-level Jest runner that is not defined by the demos root package. Until that runner is restored, validate compilation and repository checks from the root:

```bash
yarn run build:dev:backend
yarn run lint
```

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
