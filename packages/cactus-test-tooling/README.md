# @hyperledger-cacti/cactus-test-tooling

## Overview

Shared infrastructure for Cacti integration tests and demonstrations. The package manages disposable ledger networks, service containers, cryptographic fixtures, Docker resources, and SATP gateway processes.

### Target Audience

- [ ] Application developers
- [x] Contributors
- [ ] Operators

> The exported defaults and credentials are designed for isolated tests. Do not use them in production.

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Most ledger helpers require Docker. Individual ledgers may also require platform-specific prerequisites documented by their upstream images.

## Configuration

Each test-ledger or container class accepts its own typed constructor options and exports defaults where applicable. Options commonly control the image name and version, exposed ports, environment variables, resource limits, log forwarding, and reuse of existing containers.

## API Summary

The public API includes:

- Test ledgers for Besu, Besu multi-party, Corda 4, Corda 5, DAML, Fabric, Indy, OpenEthereum, Stellar, and Substrate
- Service containers for PostgreSQL, Vault, LocalStack, Keycloak, IPFS, HTTP echo, Corda connector, and WS identity
- SATPGatewayRunner for SATP integration environments
- Container lifecycle, Docker image build, environment conversion, stream, and GitHub Actions utilities
- Self-signed PKI generation and Socket.IO test setup helpers

Refer to src/main/typescript/public-api.ts for the complete export surface. The shared implementation uses [Cacti Common](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-common).

## Usage

A typical ledger lifecycle is:

```typescript
import { BesuTestLedger } from "@hyperledger-cacti/cactus-test-tooling";

const ledger = new BesuTestLedger();

await ledger.start();

try {
  const rpcApiHttpHost = await ledger.getRpcApiHttpHost();
  console.log(rpcApiHttpHost);
} finally {
  await ledger.stop();
  await ledger.destroy();
}
```

Always stop and destroy resources in a finally block so failed tests do not leave containers running.

### Stellar Test Ledger

StellarTestLedger manages the [Stellar Quickstart image](https://github.com/stellar/quickstart). Its network option selects a pristine local ledger or an existing public test network. The limits option configures Soroban resource limits and defaults to testnet-compatible values.

```typescript
await stellarTestLedger.start();

try {
  const networkConfiguration =
    await stellarTestLedger.getNetworkConfiguration();
} finally {
  await stellarTestLedger.stop();
  await stellarTestLedger.destroy();
}
```

The returned network configuration is compatible with the stellar-plus library.

### WS Identity Test Server

WsTestServer supports integration testing of WS-X.509 credentials in the Fabric connector. The test image is based on the [ws-identity server](https://github.com/brioux/ws-identity). To build that upstream image locally:

```bash
npm install
npm run build
docker build . -t ws-identity
```

## Testing

The package contains unit and integration test sources but does not define a standalone Jest script in the current demos workspace. Validate compilation and repository checks from the root:

```bash
yarn run build:dev:backend
yarn run lint
```

Integration suites require Docker and may pull large ledger images.

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

## Acknowledgments

The ledger helpers wrap upstream development images and are maintained for Cacti integration testing.
