# gcc-musl

<!---
Note: Do NOT edit directly, this file was generated using https://github.com/chainguard-images/readme-generator
-->

[![CI status](https://github.com/jdolitsky/gcc-musl/actions/workflows/release.yaml/badge.svg)](https://github.com/jdolitsky/gcc-musl/actions/workflows/release.yaml)

Minimal container image for building C applications (which do not require glibc).

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/gcc-musl:latest
```

## Supported tags

| Tag | Digest | Arch |
| --- | ------ | ---- |
| `migration-20221125` | `sha256:efcd4cb95d2e7416a25ffe6aa56e0dfb9d37691cb5e7112bf55c7ec371933859`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:efcd4cb95d2e7416a25ffe6aa56e0dfb9d37691cb5e7112bf55c7ec371933859) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r3` | `sha256:f0b83d7c71c2d2e2e97b8e12ad80707f2103341b97e2d499ba8e214fda62b025`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f0b83d7c71c2d2e2e97b8e12ad80707f2103341b97e2d499ba8e214fda62b025) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration` `migration-12` `migration-12.2` `migration-12.2.1_git20220924` `migration-12.2.1_git20220924-r4` `migration-20221129` | `sha256:ed04fb485ca0d6e84493ab559f3c398a971184942543a7b868d51d75de3a91f1`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:ed04fb485ca0d6e84493ab559f3c398a971184942543a7b868d51d75de3a91f1) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221122` | `sha256:f5be3789e050f87c0d182da3178c501fa6643f0cd34b079cc8ce97c346534fb2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f5be3789e050f87c0d182da3178c501fa6643f0cd34b079cc8ce97c346534fb2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221124` | `sha256:fc9001fe1aadd4235b669f58203a3051ab99f16532038dd57dc51cc90e5d8653`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fc9001fe1aadd4235b669f58203a3051ab99f16532038dd57dc51cc90e5d8653) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221118` | `sha256:68fcf7e1e7ae56fbdd05bcff0b06f2a8592a00f5c189141a8d1e8ef835910c60`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:68fcf7e1e7ae56fbdd05bcff0b06f2a8592a00f5c189141a8d1e8ef835910c60) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221119` | `sha256:b157be8b613f1a39442eaec30d0d94a4e36e0c90f5e91d87109d1bc16fe5b3b3`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:b157be8b613f1a39442eaec30d0d94a4e36e0c90f5e91d87109d1bc16fe5b3b3) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r6` | `sha256:57ec52cb975dc52960aa5a55d79bbd7fea2d3447c55a3abf7f666875ca9d6bf7`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:57ec52cb975dc52960aa5a55d79bbd7fea2d3447c55a3abf7f666875ca9d6bf7) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221120` | `sha256:521ec15ca2dd53ade0e331d57ffa052708cc93f5948f77626667f7748d1ec038`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:521ec15ca2dd53ade0e331d57ffa052708cc93f5948f77626667f7748d1ec038) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221127` | `sha256:4c8ff44c7b8df32a58389cf15e3ab1431c78280679f042b05eaeebd369d42f6c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4c8ff44c7b8df32a58389cf15e3ab1431c78280679f042b05eaeebd369d42f6c) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12` `12.2` `12.2.1_git20220924-r9` `latest` | `sha256:0743b31f16f937f5949a79805c719ad759a9144a4eb3abd1e137a630229b9200`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:0743b31f16f937f5949a79805c719ad759a9144a4eb3abd1e137a630229b9200) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r5` | `sha256:20d3db4f63243ef85f21bbde0005f29a4a843af282de7573bf837b9ec7dc7011`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:20d3db4f63243ef85f21bbde0005f29a4a843af282de7573bf837b9ec7dc7011) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r7` | `sha256:7ec5082b1218362be2f0c4d878bb5dca44ce3bd8929e987299bca7a0b6662e2f`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:7ec5082b1218362be2f0c4d878bb5dca44ce3bd8929e987299bca7a0b6662e2f) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r8` | `sha256:fc873f15cee962ca65d153c1ee6d6cfaa642a015ae56cc78198f6dd42ceffef0`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fc873f15cee962ca65d153c1ee6d6cfaa642a015ae56cc78198f6dd42ceffef0) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221121` | `sha256:a6a3cd31c1622701f633cd59fc77e430e39d764a541c42666c3e219af6fb1818`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a6a3cd31c1622701f633cd59fc77e430e39d764a541c42666c3e219af6fb1818) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221123` | `sha256:c3ca2055d34e86165e6cdc02b0845f95d59dbe054254f264a1ba66caea6191ce`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c3ca2055d34e86165e6cdc02b0845f95d59dbe054254f264a1ba66caea6191ce) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221126` | `sha256:dd5b5247bc4075d33665e9a9a774b065dc7503dd0c12a9c37aeffcd5caae4241`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:dd5b5247bc4075d33665e9a9a774b065dc7503dd0c12a9c37aeffcd5caae4241) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221128` | `sha256:28833fb36fbe26e8b5c24ecb4bad301d4a3b89aa9061817f6f122039869df6ca`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:28833fb36fbe26e8b5c24ecb4bad301d4a3b89aa9061817f6f122039869df6ca) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r2` | `sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r4` | `sha256:89e87965be80853be40c41a5dce1816e1e2a697106f1aef69b67ea0e0810154a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:89e87965be80853be40c41a5dce1816e1e2a697106f1aef69b67ea0e0810154a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


## Usage

To build the C application in [examples/hello/main.c](examples/hello/main.c):

```
$ docker run --rm -v "${PWD}:/work" cgr.dev/chainguard/gcc-musl examples/hello/main.c -o hello
```

This will write a Linux binary to `./hello`. If you're on Linux and have the musl library, you
should be able to run it directly. Otherwise you can run it in a container e.g:

```
$ docker run --rm -v "$PWD/hello:/hello" cgr.dev/chainguard/musl-dynamic /hello
Hello World!
```

We can also do this all in a multi-stage Dockerfile e.g:

```Dockerfile
FROM cgr.dev/chainguard/gcc-musl as build

COPY hello.c /work/hello.c
RUN cc hello.c -o hello

FROM cgr.dev/chainguard/musl-dynamic

COPY --from=build /work/hello /hello
CMD ["/hello"]
```

And we can also compile statically to be used in environments without musl:


```Dockerfile
FROM cgr.dev/chainguard/gcc-musl as build

COPY hello.c /work/hello.c
RUN cc --static hello.c -o hello

FROM cgr.dev/chainguard/static

COPY --from=build /work/hello /hello
CMD ["/hello"]
```


## Signing

All Chainguard Images are signed using [Sigstore](https://sigstore.dev)!

<details>
<br/>
To verify the image, download <a href="https://github.com/sigstore/cosign">cosign</a> and run:

```
COSIGN_EXPERIMENTAL=1 cosign verify cgr.dev/chainguard/gcc-musl:latest | jq
```

Output:
```
Error: --certificate-identity or --certificate-identity-regexp is required for verification in keyless mode
main.go:74: error during command execution: --certificate-identity or --certificate-identity-regexp is required for verification in keyless mode
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

