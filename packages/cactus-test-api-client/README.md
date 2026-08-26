# @hyperledger-cacti/cactus-test-api-client

## Overview

Dedicated integration-test package for [@hyperledger-cacti/cactus-api-client](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-api-client). Keeping these tests separate prevents circular test dependencies between the API client and the server-side packages it exercises.

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

This package does not expose a production API. Its tracked test suites verify API-client behavior against Cacti services and plugins, including the [Cacti API server](https://github.com/hyperledger-cacti/cacti/tree/main/packages/cactus-cmd-api-server).

## Usage

Use the test sources under src/test/typescript as integration examples for constructing the generated API clients and invoking Cacti endpoints.

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
