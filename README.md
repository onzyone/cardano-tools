# cordano-tools

- [cordano-tools](#cordano-tools)
  - [pull image](#pull-image)

TODO: <https://github.com/sigstore/cosign>
TODO: build matrix for arm and x86

## pull image

1. get PAT token with
    ```quote
    Select the `read:packages` scope to download container images and read their metadata.
    Select the `write:packages` scope to download and upload container images and read and write their metadata.
    Select the `delete:packages` scope to delete container images.
    ```
1. save token someplace safe and then use it to log into docker `cat ~/docker_pat| docker login https://ghcr.io -u onzyone --password-stdin`
1. `docker pull ghcr.io/onzyone/cordano-tools:<branch>`
