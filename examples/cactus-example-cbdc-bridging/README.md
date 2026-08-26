# CBDC Bridging Example

## Overview

End-to-end demonstration of a CBDC-style asset bridging workflow between Hyperledger Fabric and Hyperledger Besu. The example combines the backend orchestration service with a React frontend.

### Target Audience

- [x] Application developers
- [x] Contributors
- [ ] Operators

> This example is intended for development and evaluation. It is not production-ready.

## Install

Install repository dependencies from the cacti-demos root:

```bash
yarn install
```

Docker is required by the backend test-ledger infrastructure.

## Components

- [Backend](../cactus-example-cbdc-bridging-backend/README.md): Cacti connectors, gateways, storage plugins, and the bridging workflow.
- [Frontend](../cactus-example-cbdc-bridging-frontend/README.md): Browser interface for initiating and observing the workflow.
- fabric-contracts/: Fabric chaincode used by the example.
- fabric-asset-transfer/: Fabric asset-transfer chaincode used by the example.

The backend README links each relevant source package in the main Cacti repository.

## Configuration

Configure the backend through examples/cactus-example-cbdc-bridging-backend/process.env. Configure the frontend with PORT and REACT_APP_BACKEND_PATH as described in its README.

## API Summary

The umbrella directory does not publish a package API. The backend provides the HTTP contract, and the frontend consumes it.

## Usage

Start the backend from the repository root:

```bash
yarn workspace @hyperledger-cacti/cactus-example-cbdc-bridging-backend run start
```

After the backend reports that CbdcBridgingApp is running, start the frontend in another terminal:

```bash
yarn workspace @hyperledger-cacti/cacti-example-cbdc-bridging-frontend run start
```

Open http://localhost:2000. Keep the configured ports aligned across both components.

## Testing

Run the backend suites from the repository root:

```bash
yarn workspace @hyperledger-cacti/cactus-example-cbdc-bridging-backend run test
yarn workspace @hyperledger-cacti/cactus-example-cbdc-bridging-backend run test:integration
```

The backend suites require Docker. The frontend test command is documented in the frontend README.

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).
