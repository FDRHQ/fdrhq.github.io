# Contributing to FDR API Gateway

Thank you for your interest in contributing to the FDR API Gateway project! Our goal is to create a production-grade, decentralized API Gateway for our Federated Ride-Hailing system using Kong, Docker, and declarative configuration. We welcome contributions from the community, whether you are fixing bugs, adding features, or improving documentation.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
  - [Reporting Issues](#reporting-issues)
  - [Feature Requests](#feature-requests)
- [Getting Started Locally](#getting-started-locally)
  - [Prerequisites](#prerequisites)
  - [Setting Up Your Environment](#setting-up-your-environment)
  - [Installing decK](#installing-deck)
- [Development Workflow](#development-workflow)
  - [Branching Strategy](#branching-strategy)
  - [Coding Guidelines](#coding-guidelines)
  - [Writing Tests](#writing-tests)
- [Submitting Pull Requests](#submitting-pull-requests)
- [Style Guide](#style-guide)
- [Additional Resources](#additional-resources)
- [License](#license)

## Code of Conduct

We expect all contributors to follow our [Code of Conduct](CODE_OF_CONDUCT.md). Please read it before participating in the project.

## How to Contribute

There are several ways you can contribute:

### Reporting Issues

- **Bug Reports:** Please search the [issue tracker](https://github.com/FDRHQ/fdrhq-api-gateway/issues) to see if your issue has already been reported. If not, open a new issue with a descriptive title and steps to reproduce.
- **Security Issues:** If you find a security vulnerability, please report it privately following our security guidelines (see the [SECURITY.md](SECURITY.md) file).

### Feature Requests

If you have an idea for a new feature or improvement, please open an issue with your proposal. We appreciate detailed suggestions, including use cases and benefits.

## Getting Started Locally

### Prerequisites

- **Docker:** Ensure Docker is installed and running on your machine.
- **IntelliJ IDEA:** Use IntelliJ IDEA for editing code and managing the project.
- **decK:** We use decK for managing Kong's declarative configuration. See the [Installing decK](#installing-deck) section below.

### Setting Up Your Environment

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/FDRHQ/fdrhq-api-gateway.git
   cd fdrhq-api-gateway
   ```

2. **Build and Run Kong Locally:**

   We recommend using Docker Compose to run Kong in DB-less mode. A sample `docker-compose.yml` is provided in the repository. To start up:

   ```bash
   docker-compose up --build
   ```

3. **Verify Kong is Running:**

   Test Kong’s Admin API:

   ```bash
   curl --head http://localhost:8001
   ```

### Installing decK

We use decK to manage our Kong configuration declaratively. To install decK, run:

On macOS/Linux:
```bash
curl -L https://github.com/kong/deck/releases/latest/download/deck_$(uname -s)_$(uname -m).tar.gz | tar zxvf -
sudo mv deck /usr/local/bin/
```

On Windows, download the appropriate binary from the [decK Releases page](https://github.com/kong/deck/releases) and add it to your PATH.

Verify the installation with:
```bash
deck version
```

## Development Workflow

### Branching Strategy

- **Main Branch:** `main` (production-ready code)
- **Development Branch:** `develop` (integration of features)
- **Feature Branches:** Create a branch with a descriptive name (e.g., `feature/rate-limiting-plugin`) from `develop`.

### Coding Guidelines

- **Maintain Readability:** Write clear, well-documented code and add comments where necessary.
- **Follow Language Conventions:** Use standard coding styles and naming conventions for the language in use (JavaScript, Go, Python, etc.).
- **Write Tests:** Ensure new features have accompanying tests, and run all tests before submitting a pull request.

### Writing Tests

- Use the project’s testing framework (e.g., JUnit for Java or pytest for Python) to write unit and integration tests.
- Provide clear, reproducible test cases.

## Submitting Pull Requests

1. Fork the repository.
2. Create your feature branch and commit your changes with clear commit messages.
3. Push your branch to your fork and open a pull request against the `develop` branch.
4. Ensure your pull request adheres to our style guidelines and includes a clear description of the changes.

## Style Guide

- Follow the repository’s coding style for consistency.
- Run linters and formatters as configured (e.g., ESLint for JavaScript, Black for Python, gofmt for Go).
- Document public APIs using comments and, where possible, generate documentation (e.g., using Swagger/OpenAPI for REST endpoints).

## Additional Resources

- [Kong Gateway Documentation](https://docs.konghq.com/gateway/latest/)
- [decK Documentation](https://docs.konghq.com/deck/latest/)
- [Docker Documentation](https://docs.docker.com/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## License

This project is licensed under the [Apache License 2.0](LICENSE).

Thank you for helping improve the FDR API Gateway! Your contributions are greatly appreciated.
