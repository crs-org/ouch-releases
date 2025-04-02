# ouch releases for different platforms using GoReleaser

https://github.com/ouch-org/ouch does not have a fresh release yet, so let's build it by yourself

## installation

1. install goreleaser: https://goreleaser.com/install/

2. install zig: https://ziglang.org/learn/getting-started/

3. build ouch

```shell
git clone https://github.com/ouch-org/ouch

cp .goreleaser.yaml ouch/

cd ouch

goreleaser release --clean --snapshot
```

Check out `dist` folder for built binaries.
