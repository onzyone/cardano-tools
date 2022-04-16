# cardano-tools

- [cardano-tools](#cardano-tools)
  - [build image](#build-image)
  - [pull image](#pull-image)
  - [validate](#validate)

## build image

TODO: <https://github.com/sigstore/cosign>

## pull image

1. get PAT token with
    ```quote
    Select the `read:packages` scope to download container images and read their metadata.
    Select the `write:packages` scope to download and upload container images and read and write their metadata.
    Select the `delete:packages` scope to delete container images.
    ```
1. save token someplace safe and then use it to log into docker `cat ~/docker_pat| docker login https://ghcr.io -u onzyone --password-stdin`
1. `docker pull ghcr.io/onzyone/cordano-tools:<branch>`

## validate

1. startup the cardano node and wallet via docker compose. Note that this will take some time to synk. Note this is for the test network!
    `CARDANO_NETWORK=testnet docker compose up -d`
1. test your locally running node and wallet
    ```bash
    # with curl
    curl http://localhost:8091/v2/network/information -s | jq .sync_progress
    # or with cardano-wallet cli (via docker run)
    docker run --network host --rm inputoutput/cardano-wallet network information
    # or with cardano-cli
    docker run --rm -v spike-cardano-api_node-ipc:/node-ipc ghcr.io/onzyone/cardano-tools query tip --testnet-magic 1097911063
    ```
1. curl wallets
    ```bash
    curl -s http://localhost:8091/v2/wallets | jq
    ```
