# @hyperledger-cacti/cacti-example-cbdc-bridging-frontend

## Overview

React frontend for the CBDC bridging example. It provides the browser interface for the Fabric-to-Besu workflow implemented by @hyperledger-cacti/cactus-example-cbdc-bridging-backend.

### Target Audience

- [x] Application developers
- [x] Contributors
- [ ] Operators

> This application is an integration example and is not production-ready.

## Install

From the cacti-demos repository root:

```bash
yarn install
```

## Configuration

| Variable               | Default               | Purpose                 |
| :--------------------- | :-------------------- | :---------------------- |
| PORT                   | 2000                  | Development server port |
| REACT_APP_BACKEND_PATH | http://localhost:9999 | CBDC backend base URL   |

The backend endpoint must match the locally running backend configuration.

## API Summary

This package does not expose a reusable programmatic API. It consumes the CBDC backend HTTP API and renders the example user interface.

Relevant Cacti packages are documented by the [CBDC backend](../cactus-example-cbdc-bridging-backend/README.md).

## Usage

Start the development server:

```bash
yarn workspace @hyperledger-cacti/cacti-example-cbdc-bridging-frontend run start
```

Open http://localhost:2000 after the server starts.

### Container Image

Run the published demonstration image:

```bash
docker run -p 2000:2000 aaugusto11/cactus-example-cbdc-bridging-frontend:v2
```

Or build the image locally:

```bash
docker build examples/cactus-example-cbdc-bridging-frontend -t cbdc-app-frontend
docker run -p 2000:2000 cbdc-app-frontend
```

## Testing

Run the React test command:

```bash
yarn workspace @hyperledger-cacti/cacti-example-cbdc-bridging-frontend run test
```

## Contributing

See the repository [contribution guidelines](../../CONTRIBUTING.md).

## License

The package metadata declares the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
