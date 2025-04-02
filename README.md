# ouch releases for different platforms using GoReleaser

[![windows-build](https://github.com/crs-org/ouch-releases/actions/workflows/windows-build.yml/badge.svg)](https://github.com/crs-org/ouch-releases/actions/workflows/windows-build.yml)

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

4. build `ouch` from the source code:

```shell
git clone https://github.com/ouch-org/ouch

cp .goreleaser.yaml ouch/

cd ouch

# if on MacOS:
rustup toolchain add stable-x86_64-unknown-linux-gnu --profile minimal --force-non-host

# build
goreleaser release --clean --snapshot
```

Check `dist` folder out to see built binaries.
