# @hyperledger-cacti/cactus-test-geth-ledger

## Overview

Utilities for starting and controlling a go-ethereum test ledger in automated tests. GethTestLedger manages the container lifecycle and exposes the ledger RPC endpoint.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required to run the ledger container.

## Configuration

GethTestLedger accepts IGethTestLedgerOptions. The exported GETH_TEST_LEDGER_DEFAULT_OPTIONS provides suitable local defaults. Common options include the container image name and version, log level, container-log forwarding, environment variables, and whether to reuse an already running ledger.

The package also exports the development whale account address and private key. Use these credentials only in isolated test environments.

## API Summary

- GethTestLedger: starts, inspects, stops, and destroys the test ledger.
- IGethTestLedgerOptions: constructor options.
- GETH_TEST_LEDGER_DEFAULT_OPTIONS: default container configuration.
- WHALE_ACCOUNT_ADDRESS and WHALE_ACCOUNT_PRIVATE_KEY: funded test credentials.

The implementation uses [Cacti Common](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-common) and the local [test-tooling package](../cactus-test-tooling/README.md).

## Usage

```typescript
import {
  GethTestLedger,
  type IGethTestLedgerOptions,
} from "@hyperledger-cacti/cactus-test-geth-ledger";

const options: Partial<IGethTestLedgerOptions> = {
  emitContainerLogs: false,
  useRunningLedger: false,
};

const ledger = new GethTestLedger(options);
await ledger.start();

try {
  const rpcApiHttpHost = await ledger.getRpcApiHttpHost();
  console.log(rpcApiHttpHost);
} finally {
  await ledger.stop();
  await ledger.destroy();
}
```

## Testing

Integration tests are located under src/test/typescript/integration. The package does not define a standalone Jest script in the current demos workspace. Validate compilation and repository checks from the root:

```bash
yarn run build:dev:backend
yarn run lint
```

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
