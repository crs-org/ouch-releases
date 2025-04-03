# ouch releases for different platforms using GoReleaser

[![win-x86_64](https://github.com/crs-org/ouch-releases/actions/workflows/win-x86_64.yml/badge.svg)](https://github.com/crs-org/ouch-releases/actions/workflows/win-x86_64.yml)
[![win-aarch64](https://github.com/crs-org/ouch-releases/actions/workflows/win-aarch64.yml/badge.svg)](https://github.com/crs-org/ouch-releases/actions/workflows/win-aarch64.yml)

https://github.com/ouch-org/ouch does not have a fresh release yet, so let's build it by yourself

## installation

0. install rust using `rustup`: https://rustup.sh

```shell
rustc --version

cargo --version
```

1. install `goreleaser`: https://goreleaser.com/install

```shell
goreleaser --version
```

2. install `podman`: https://podman.io

```shell
podman machine init
podman machine start

podman version
```

3. install `cross`: https://github.com/cross-rs/cross

```shell
cross --version
```

4. build an image with edge version of `x86_64-unknown-linux-gnu` target

```shell
podman build --platform=linux/amd64 -f Dockerfile.aarch64-unknown-linux-gnu -t aarch64-unknown-linux-gnu:ouch .

podman build --platform=linux/amd64 -f Dockerfile.x86_64-unknown-linux-gnu -t x86_64-unknown-linux-gnu:ouch .
```

5. build `ouch` from the source code:

```shell
# copy main branch of ouch
git clone https://github.com/ouch-org/ouch
cp .goreleaser.yaml ouch/
cp Cross.toml ouch/
cd ouch

# build
goreleaser build --clean --snapshot --id ouch

# archive ouch by ouch (on Mac)
./dist/ouch_aarch64-apple-darwin/ouch compress ./dist/ouch_x86_64-unknown-linux-gnu ./dist/ouch_x86_64-unknown-linux-gnu.zip
./dist/ouch_aarch64-apple-darwin/ouch compress ./dist/ouch_x86_64-unknown-linux-musl ./dist/ouch_x86_64-unknown-linux-musl.zip
./dist/ouch_aarch64-apple-darwin/ouch compress ./dist/ouch_aarch64-unknown-linux-gnu ./dist/ouch_aarch64-unknown-linux-gnu.zip
./dist/ouch_aarch64-apple-darwin/ouch compress ./dist/ouch_x86_64-apple-darwin ./dist/ouch_x86_64-apple-darwin.zip
./dist/ouch_aarch64-apple-darwin/ouch compress ./dist/ouch_aarch64-apple-darwin ./dist/ouch_aarch64-apple-darwin.zip
```
