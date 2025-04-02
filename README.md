# ouch releases for different platforms using GoReleaser

https://github.com/ouch-org/ouch does not have a fresh release yet, so let's build it by yourself

## installation

0. install rust: https://rustup.sh

1. install goreleaser: https://goreleaser.com/install

2. install zig: https://ziglang.org/learn/getting-started

3. install podman: https://podman.io

4. install cross: https://github.com/cross-rs/cross

5. build ouch

```shell
git clone https://github.com/ouch-org/ouch

cp .goreleaser.yaml ouch/

cd ouch

goreleaser release --clean --snapshot
```

Check `dist` folder out to see built binaries.
