# Atlas Network Eigenlayer Testnet AVS Operator

## Prerequisites

- Linux amd64/x86
- Recommended Hardware specifications
  - 2 vCPUs
  - 4GB RAM
  - 40GB Disk
  - 100 Mbps
- Docker >27.x.x

  ```shell
  ## Install latest docker, use `sudo bash` in case of non-root user
  curl -sL get.docker.com | bash
  ```

- Register your operator to EigenLayer using [EigenLayer CLI](https://github.com/Layr-Labs/eigenlayer-cli/blob/master/README.md) and stake holesky ETH

> NOTE: For any Docker based commands, if you have installed as root then you might have to append `sudo` in front of the command.

## Setup Instructions

-
  Clone this repo and execute the following commands:

  ```shell
  git clone https://github.com/nodeops-app/atlas-operator.git
  cd atlas-operator/eigenlayer/testnet
  cp .env.example .env
  ```

-
  Update the `TODO` sections in the `.env` file given in the root directory of the repository with your own details.

  ```bash
  ## TODO: Operators need to set it ecdsa private key in
  ## non hex format, without `0x`.
  PRIVATE_KEY=
  ...
  ```

-
  Use the following command to register your operator on Atlas Network EigenLayer AVS Testnet if you're not register

   ```shell
   docker compose up --profile register
   ```

-
  Run an Operator

   Execute the following command to start the operator:

   ```shell
   docker compose up -d
   ```

   Execute the following command to start auto upgrader

    > Do it at your own risk:

   ```shell
   docker compose up -d
   docker compose up -d --profile autopilot
   ```

  Tear down operator

  ```bash
  docker compose down
  ```
