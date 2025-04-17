# FDR API Gateway

FDR API Gateway is the central component of our Federated Ride-Hailing system. Built on Kong, it provides secure and scalable API routing, load balancing, and plugin-based enhancements for a decentralized, multi-region architecture.

## Features

- Declarative configuration via decK and YAML files
- Secure routing and load balancing using Kong
- Plugin support for rate limiting, authentication, logging, and more
- Integration with Infisical for secret management
- Production-grade configuration for both local development and cloud deployment

## Getting Started

### Prerequisites

- **Docker**: Ensure Docker is installed and running.
- **IntelliJ IDEA**: For code editing and project management.
- **Git**: For version control.
- **Infisical CLI**: For secure secret injection.

### Setting Up Locally

1. **Clone the Repository**

   ```bash
   git clone https://github.com/FDRHQ/fdr-api-gateway.git
   cd fdr-api-gateway
   ```

2. **Install Infisical CLI**

   ```bash
   curl -fsSL https://infisical.com/install.sh | bash
   ```

3. **Login to Infisical**

   ```bash
   infisical login
   ```

4. **Run Docker Compose with Infisical**

   Inject secrets securely using Infisical:

   ```bash
   infisical run --env=prod -- docker-compose up --build
   ```

   Verify that Kong is running by checking the Admin API:

   ```bash
   curl --head http://localhost:8001
   ```

## Installing decK

We use decK to manage Kong's configuration declaratively. To simplify setup for all developers, an installation script is included.

1. **Run the Installation Script**

   From the repository root, execute:

   ```bash
   bash scripts/install-deck.sh
   ```

   This script will:
    - Retrieve the latest version of decK from GitHub.
    - Download the appropriate binary for your operating system.
    - Verify the file and extract the binary.
    - Suggest moving the binary to `/usr/local/bin/` if needed.

2. **Verify decK Installation**

   ```bash
   deck version
   ```

## Managing Kong Configuration with decK

The declarative configuration file (`kong.yml`) resides in the `config/` directory. You can use decK to validate and sync your configuration:

- **Validate Configuration:**

  ```bash
  deck file validate config/kong.yml
  ```

- **Sync Configuration to Kong:**

  ```bash
  deck gateway sync config/kong.yml
  ```

## Using Infisical to Manage Secrets

1. **Install Infisical CLI**

   ```bash
   curl -fsSL https://infisical.com/install.sh | bash
   ```

2. **Login to Infisical**

   ```bash
   infisical login
   ```

3. **Initialize a Project and Environment**

    - Go to https://app.infisical.com
    - Create a project (e.g., `fdrhq-api`)
    - Create an environment (e.g., `prod`)
    - Add secrets like:
        - `POSTGRES_PASSWORD=supersecurepassword`

4. **Run with Secrets Injected**

   ```bash
   infisical run --env=prod -- docker-compose up --build
   ```

   This automatically injects secrets from Infisical as environment variables.

## Deployment

When ready for production, package the API Gateway using the provided `Dockerfile` and deploy on your chosen free-tier cloud provider (Fly.io, Render, Railway, etc.). Configure environment variables and security settings as needed.

## Contributing

Contributions are welcome! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on reporting issues, proposing features, and submitting pull requests.

## License

This project is licensed under the [Apache License 2.0](LICENSE).
