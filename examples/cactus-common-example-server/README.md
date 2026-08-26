# @hyperledger-cacti/cactus-common-example-server

## Overview

Shared server-side utilities retained for Cacti demo applications. The package contains verifier, routing interface, business logic plugin, configuration, and transaction-signing helpers.

### Target Audience

- [x] Application developers
- [x] Contributors
- [ ] Operators

> This package supports demonstrations and tests. It is not intended for production use.

## Install

Install repository dependencies from the cacti-demos root:

~~~bash
yarn install
yarn workspace @hyperledger-cacti/cactus-common-example-server run build
~~~

## API Summary

The public API exports:

- Verifier and ledger-event utilities
- Routing types and transaction-management helpers
- Socket.IO server startup and business logic plugin configuration
- BusinessLogicPlugin, BusinessLogicBase, and LedgerOperation
- TransactionSigner and configuration-reading utilities

The implementation builds on [Cacti Common](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-common) and [Cacti Core API](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-core-api).

## Usage

Import only the utility required by the consuming example:

~~~typescript
import {
  BusinessLogicPlugin,
  TransactionSigner,
} from "@hyperledger-cacti/cactus-common-example-server";
~~~

Refer to src/main/typescript/public-api.ts for the complete supported export surface.

## Container Image

The Docker image is primarily a base for demo applications and plugins. Build the TypeScript output before building the image:

~~~bash
yarn workspace @hyperledger-cacti/cactus-common-example-server run build
docker build examples/cactus-common-example-server -t cactus-common-example-server
~~~

## Testing

The package contains unit tests under src/test/typescript/unit. It does not define a standalone test script. From the repository root, validate compilation and repository formatting with:

~~~bash
yarn run build:dev:backend
yarn run lint
~~~

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
