# Atlas Network Eigenlayer Testnet AVS Operator

## Prerequisites

- Linux `amd64/x86` based instance
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

- Othentic CLI

  ```shell
  ## Node version LTS
  npm i -g @othentic/othentic-cli
  ```

- Make sure you some eth on Ethereum `holesky` and on Arbitrum `Sepolia` for operator registration tx

- Register as operator on EigenLayer if you're not using [EigenLayer CLI](https://github.com/Layr-Labs/eigenlayer-cli/blob/master/README.md) and stake holesky ETH

- Staked atleast `0.1stETH` or any strategy that is supported by AVS, more info [here](https://docs.othentic.xyz/main/avs-framework/quick-start#activate-your-operator-by-depositing-into-eigenlayer). **After depositing** wait for around **5-10 min** till it'll get synced across l1/l2 by synceR

  ```shell
  ## Stake 0.1stETH
  othentic-cli operator deposit --strategy stETH --shares 0.1
  ```

  If you don't have stETH, Convert ETH to stETH and stake using below command, change the amount as per your convenience

  ```shell
  ## Convert 0.0101ETH to stETH and stake 0.01stETH
  othentic-cli operator deposit --strategy stETH --convert 0.0101 --shares 0.01
  ```

> NOTE: For any Docker based commands, if you have installed as root then you might have to append `sudo` in front of the command.

## Setup Instructions

- Use othentic cli to register your operator on Atlas Network EigenLayer AVS Testnet. if you're not operator on eigenlayer then it'll prompt you for the details. Would recommand using same private key and signer key which could be operator key.

  ```shell
  ## AVS Governance address: 0x590dDF9A1a475bF46F10627A49051036d5286a61
  othentic-cli operator register --l1-chain holesky --l2-chain arbitrum-one-sepolia
  ```

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
  ## TODO: Signer key
  ...
  ```

-
  Run an Operator

   Execute the following command to start the operator:

   ```shell
   docker compose up -d
   ```

- Upgrade: By default auto operator upgrade is enable using autopilot. you can disable it by commenting out autopilot service in `docker-compose.yaml` and manual upgrade using below command

  ```shell
  docker compose pull
  docker compose up -d
  ```

-
  Tear down operator

  ```bash
  docker compose down
  ```
