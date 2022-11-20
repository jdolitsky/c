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
| `migration-20221118` | `sha256:68fcf7e1e7ae56fbdd05bcff0b06f2a8592a00f5c189141a8d1e8ef835910c60`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:68fcf7e1e7ae56fbdd05bcff0b06f2a8592a00f5c189141a8d1e8ef835910c60) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration` `migration-12` `migration-12.2` `migration-12.2.1_git20220924` `migration-12.2.1_git20220924-r4` `migration-20221119` | `sha256:b157be8b613f1a39442eaec30d0d94a4e36e0c90f5e91d87109d1bc16fe5b3b3`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:b157be8b613f1a39442eaec30d0d94a4e36e0c90f5e91d87109d1bc16fe5b3b3) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r4` `latest` | `sha256:1a286586dd623e0ab1cbe10a26861e42343e1a2818a61463d72344b4d1968c11`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:1a286586dd623e0ab1cbe10a26861e42343e1a2818a61463d72344b4d1968c11) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r2` | `sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r3` | `sha256:f0b83d7c71c2d2e2e97b8e12ad80707f2103341b97e2d499ba8e214fda62b025`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f0b83d7c71c2d2e2e97b8e12ad80707f2103341b97e2d499ba8e214fda62b025) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
Verification for cgr.dev/chainguard/gcc-musl:latest --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - Any certificates were verified against the Fulcio roots.
[
  {
    "critical": {
      "identity": {
        "docker-reference": "ghcr.io/chainguard-images/gcc-musl"
      },
      "image": {
        "docker-manifest-digest": "sha256:1a286586dd623e0ab1cbe10a26861e42343e1a2818a61463d72344b4d1968c11"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "19ccbecd34028ac7aa14c5038f3f7b80a13ac606",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/gcc-musl",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIEqgEbKNKo2QVkL4ZMGMsvHeq0Z8xcHs2L5wnT11RRGDAiEAiAFgP5vQwMzaKbxj3cIAqGPN3dv9aKPUpB9Z1pja5PM=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI2ZWEyNGRmYzRjNzQ4ZGNmYzk0ZTg5MWU2MGQ5MGQ2NWMxMWEwNmE3ZmQ0YTI2NDE2Yzg2ZmZkODQ2ZDBmMjZmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJUUROSEZZMTkwbUVSUlBmdjhBNlFRR3REV3FWUHlkS1BPRVZRSFl6djRCanJRSWdPbFFzK1BzRDBDczh3MDAzYlVLWkRWSHc4NkxFK1dmd1k1YjJRUkZxSEFvPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnpSRU5EUVhwWFowRjNTVUpCWjBsVlZGTklkakpRT1ZnMk4xY3JWbXREZDNodFRHVjBla0oxTlhoTmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVUlRWTlJFRjZUbXBOTTFkb1kwNU5ha2w0VFZSRk5VMUVRVEJPYWswelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVV6YkRRd2NITlJkbkJxTVVOcGQxRTBabTFPT1ZWRVFXNWtURkJpTDJOV1NuQnlhV3NLY1RJeU4xZFBaV2RNTlM5S1VFMXpTMk5aSzBVNWNHcE9jRVZCVmt0RlZGQnhXVEJ3VTFkTGQyaExNM2RNVW0xRU0yRlBRMEZzVVhkblowcFJUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ1ZGpSV0NuaHFjMjFuY205ck9ESmxXV3RTS3pSRmFuTk1PRk52ZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5WkdwWmVURjBaRmhPYzB4NU5XNWhXRkp2WkZkSmRtUXlPWGxoTWxwellqTmtla3d6U214aVIxWm9ZekpWZFdWWFJuUmlSVUo1Q2xwWFducE1NbWhzV1ZkU2Vrd3lNV2hoVnpSM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoUFYwNXFXVzFXYWxwRVRUQk5SRWswV1ZkTk0xbFhSWGhPUjAweFRVUk5ORnBxVG0xT01razBDazFIUlhoTk1rWnFUbXBCTWsxQ2QwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlJHdE9lVnBYUmpCYVUwSlRXbGQ0YkZsWVRteE5RMmRIUTJselIwRlJVVUlLWnpjNGQwRlJWVVZIYlU1dldWZHNkVm96Vm1oamJWRjBZVmN4YUZveVZucE1NbVJxV1hreGRHUllUbk5OUWpCSFEybHpSMEZSVVVKbk56aDNRVkZaUlFwRU0wcHNXbTVOZG1GSFZtaGFTRTEyWWxkR2NHSnFRMEpwWjFsTFMzZFpRa0pCU0ZkbFVVbEZRV2RTT0VKSWIwRmxRVUl5UVU0d09VMUhja2Q0ZUVWNUNsbDRhMlZJU214dVRuZExhVk5zTmpRemFubDBMelJsUzJOdlFYWkxaVFpQUVVGQlFtaEpNVkV6YUZWQlFVRlJSRUZGWTNkU1VVbG5aR3hVT1c5bFJXTUtTbVpRWms1eU5HOVlVMmxRU0dzdk9EZ3lOMmN4VnpadVFWVTBMMDVOZVhaUWRrbERTVkZFU21ZelJ6VkRlVWxEVkNzMFNub3pabFY2TVcxUWIxb3plQXByWlc5TU5pOTNTV1JuTUhodlNFSlZSMFJCUzBKblozRm9hMnBQVUZGUlJFRjNUbkJCUkVKdFFXcEZRV2htU2xoaVpVSjNVMkZRVGxaSVF6UTFiSHBDQ2tvd1ZWUlFLMGhFVlRaWlZtZFNjR1ZuYVhwUFdIWkdWM1ZZWnpOVWVWZzBPSHBJYm1sNlNtUTJRWG81UVdwRlFXaFBkakJYWlV0d2NFNUhTbkZZU1hVS1ZUTTFXVGR6YjFBd1kwSTNjRlpzVWxoSVNuTTRTUzlzZUhVeGNrSlNNV1Z4VW1ZM1REaElUbTlqU0RSb2NGaFRDaTB0TFMwdFJVNUVJRU5GVWxSSlJrbERRVlJGTFMwdExTMEsifX19fQ==",
          "integratedTime": 1668818231,
          "logIndex": 7382021,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/gcc-musl/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/gcc-musl",
      "githubWorkflowSha": "19ccbecd34028ac7aa14c5038f3f7b80a13ac606",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3501250263",
      "sha": "19ccbecd34028ac7aa14c5038f3f7b80a13ac606"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

