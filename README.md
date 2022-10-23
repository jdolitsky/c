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
| `12.2.1_git20220924-r3` `latest` | `sha256:440f5a7856cbca29218e22521f88012f3b431a408c949ca34a5b682026e7807e`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:440f5a7856cbca29218e22521f88012f3b431a408c949ca34a5b682026e7807e) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r2` | `sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:440f5a7856cbca29218e22521f88012f3b431a408c949ca34a5b682026e7807e"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "1ecb2c9573623865acf1f0471c17e4dac522c9ff",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/gcc-musl",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIAlT8oUUyp8KMCIMS2UtRH69Igjw7zC/mtx7F9pHI4LqAiEA1fQ2uq60Q89cloftTwXdrCpWCCH27PPHrqM460Xgov8=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJmN2E2MzM2MDYwN2MxMTkxZjc3ZWZhZjVjODQ2NmNiNGVlYmIxNGE5OTFlZGI1YjExMDlmODE2YTdjOTZkNTcwIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FWUNJUURiTmRUaDlCcXptc2gyVlF3VXdTazBXQ1NEc3JKbEp1S1kxRTJOYzJ6VUxRSWhBSmhKa1dWTW1iVjRiTCtMKythU2ZabFdWN1JLRExkUG9rc2pvbjFqTmo5UCIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnlWRU5EUVhwVFowRjNTVUpCWjBsVlR6SnVlV1pSVkVOU1YzcEtjbHBtU1RkTVZ6aGtiMGcyWlV0emQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFU1hsTlJFRXdUMVJWTTFkb1kwNU5ha2w0VFVSSmVVMUVRVEZQVkZVelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZOVVZOSGVHdExPVWhYWkd3NFJ6TjNRWFJYY0dsUldXNTJaVmx6WmtwbE5WaGFkRFFLVmtKelEwRnVUREZ6UjJSaVpsUkViakZ4Unl0aE4yWXlaV1p0WW5WcWVtRkhOVzFYYUROS05HWkxSSE4xZFd0T1NqWlBRMEZzVFhkblowcFFUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZ2TldKRUNpODViWFZMZW1VNVNtbFpabWx0UTB4SWRXeG1XSGxuZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5WkdwWmVURjBaRmhPYzB4NU5XNWhXRkp2WkZkSmRtUXlPWGxoTWxwellqTmtla3d6U214aVIxWm9ZekpWZFdWWFJuUmlSVUo1Q2xwWFducE1NbWhzV1ZkU2Vrd3lNV2hoVnpSM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWjNoYVYwNXBUVzFOTlU1VVkzcE9ha2w2VDBSWk1WbFhUbTFOVjFsM1RrUmplRmw2UlROYVZGSnJDbGxYVFRGTmFrcHFUMWRhYlUxQ2QwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlJHdE9lVnBYUmpCYVUwSlRXbGQ0YkZsWVRteE5RMmRIUTJselIwRlJVVUlLWnpjNGQwRlJWVVZIYlU1dldWZHNkVm96Vm1oamJWRjBZVmN4YUZveVZucE1NbVJxV1hreGRHUllUbk5OUWpCSFEybHpSMEZSVVVKbk56aDNRVkZaUlFwRU0wcHNXbTVOZG1GSFZtaGFTRTEyWWxkR2NHSnFRMEpwVVZsTFMzZFpRa0pCU0ZkbFVVbEZRV2RTTjBKSWEwRmtkMEl4UVVGb1oydDJRVzlWZGpsdkNsSmtTRkpoZVdWRmJrVldia2RMZDFkUVkwMDBNRzB6YlhaRFNVZE9iVGw1UVVGQlFtY3ZNSEpCVVZGQlFVRlJSRUZGV1hkU1FVbG5VVVpGTTNGTGR6RUtXR1JWUjJ0TGNFY3pXRTUxT1RNMWNrTlVlRWRvTW1aWGFYZE5NV1pEVGs1RWRHZERTVU5MZG5sSVJubHJOSGhtYjFZd2RHSkZla1JyVkhZM0syeFpNZ3AxZGxSS2JYcEphRzFuWVhSVmJVSXhUVUZ2UjBORGNVZFRUVFE1UWtGTlJFRXlZMEZOUjFGRFRVZHNUV1ZsZDNaNVEwWXJTek5uYjJOTE9XWjJTbkp2Q2xoT1Z6UTFhSGhMZDJsWWVUUkJlR2hpWlRsTWJWTnJjR1Z6VEhsWlUwcGxkMk52WmtkdFJ6VnJRVWwzVWswNGMyRkpjblJEV1hsTlV5OU9XbXMxVG0wS1prMUNaVlY1VFZsU2JUYzFhSHB5WVVkdk1rOUJkMWRxWlhobGJ6QlViakEyTTJSYVprcDJRM041WkZrS0xTMHRMUzFGVGtRZ1EwVlNWRWxHU1VOQlZFVXRMUzB0TFFvPSJ9fX19",
          "integratedTime": 1666399821,
          "logIndex": 5607706,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/gcc-musl/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/gcc-musl",
      "githubWorkflowSha": "1ecb2c9573623865acf1f0471c17e4dac522c9ff",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3301329049",
      "sha": "1ecb2c9573623865acf1f0471c17e4dac522c9ff"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

