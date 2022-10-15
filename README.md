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
| `12.2.1_git20220924-r2` `latest` | `sha256:f4300c32d45f7dd9b32d03f655005b8b494b66770a62d6927df6ed6eec8feeba`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f4300c32d45f7dd9b32d03f655005b8b494b66770a62d6927df6ed6eec8feeba) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:f4300c32d45f7dd9b32d03f655005b8b494b66770a62d6927df6ed6eec8feeba"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "72db5d0675c2ede586c53615da0073228bab2c3d",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/gcc-musl",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEQCIFJyvNuhnUhsTXzWg/XDkuosd2Rqjf/S3ziztrDSa/vQAiBF4VKef0XGnOQmujecSoomFwmLC5oCKh/ukuRNawqcsA==",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiI4NGUzZDVhMTFkYWY2NDMxYzhlMGI5ODc3NmJmYWJjMGUwZDQzNjVkNTk5YjdlODYyYmE5MWExMTVlODI1YTM2In19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQml0ZysyZHlLWUo5ZENQUjVzQVdqQW9rcG1lVW5XeUdodGZvV2NsZUgyd0FpRUEyd3lFdGdSeGpIMU40R3gwQzhLV1dNTVl0WjR2aWd0cHpoNEpsQVdhUFBvPSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnlla05EUVhwWFowRjNTVUpCWjBsVlprWkxWbXRYT0c4NGVrOXRTRkJwZDB0SVR6aEdWelJvUnpFd2QwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFFUlRCTlJFRXhUbFJCTTFkb1kwNU5ha2w0VFVSRk1FMUVSWGRPVkVFelYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZUYlRabVVERlJVaXRXTUdjd2RIVmtVRnBZVGxJdlIyZENibkF5TldGR1drbDZSa3dLYTAxU2VrbFJOVEJJYlhabldVczBjREZHVVdScFRETndkeTgxY2xaQlFuQlNkMnhpYWtaeWREUnRkV2RtUVVKMlpVdFBRMEZzVVhkblowcFJUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZNY1VGdkNtaEtVVk12ZDJKQ2MyeE9PRzB2VjJseFZTOVpjRU5SZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5WkdwWmVURjBaRmhPYzB4NU5XNWhXRkp2WkZkSmRtUXlPWGxoTWxwellqTmtla3d6U214aVIxWm9ZekpWZFdWWFJuUmlSVUo1Q2xwWFducE1NbWhzV1ZkU2Vrd3lNV2hoVnpSM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpOTmJWSnBUbGRSZDA1cVl6Rlpla3BzV2tkVk1VOUVXbXBPVkUweVRWUldhMWxVUVhkT2VrMTVDazFxYUdsWlYwbDVXWHBPYTAxQ2QwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlJHdE9lVnBYUmpCYVUwSlRXbGQ0YkZsWVRteE5RMmRIUTJselIwRlJVVUlLWnpjNGQwRlJWVVZIYlU1dldWZHNkVm96Vm1oamJWRjBZVmN4YUZveVZucE1NbVJxV1hreGRHUllUbk5OUWpCSFEybHpSMEZSVVVKbk56aDNRVkZaUlFwRU0wcHNXbTVOZG1GSFZtaGFTRTEyWWxkR2NHSnFRMEpwWjFsTFMzZFpRa0pCU0ZkbFVVbEZRV2RTT0VKSWIwRmxRVUl5UVVGb1oydDJRVzlWZGpsdkNsSmtTRkpoZVdWRmJrVldia2RMZDFkUVkwMDBNRzB6YlhaRFNVZE9iVGw1UVVGQlFtYzVVRGd6VUhOQlFVRlJSRUZGWTNkU1VVbG5RVzh6U0dWU1YxZ0tRMEZNTmxOak1YVkRTVGRWYlhZMVJtRlJLMjVLVEUxT05FSmxNVUUzTWpsdWQyZERTVkZFU2pocVlYTlFNbGxUUkhsNEszQlZMMFU1WVVsamVWcHRaUXB1TTA5VVRHbExkakExTXpkeWRrTldObXBCUzBKblozRm9hMnBQVUZGUlJFRjNUbTlCUkVKc1FXcEZRU3RPZW01SFdXOUhMekJJZGpCUlVDOTFjVmxtQ21Oa2QzY3laVzB2TWk5NFdVOXJNMFpGT0RsaFFtTXhTbnA1Ym10WWJqaE5WMVZIT0RCaVIyZENSM1F2UVdwQ01EZHRTREJvYmtaNGVYbGhjaTl0UWpVS05HMVZaRE5KWm1Rd2VsUXpLMDg0V0hCclJ5dEZZVFo2WmlzeFpVNW5jbXc0YlcxRWRESk9VSFl3UWpaVlEwVTlDaTB0TFMwdFJVNUVJRU5GVWxSSlJrbERRVlJGTFMwdExTMEsifX19fQ==",
          "integratedTime": 1665708927,
          "logIndex": 5061638,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/gcc-musl/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/gcc-musl",
      "githubWorkflowSha": "72db5d0675c2ede586c53615da0073228bab2c3d",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3246690885",
      "sha": "72db5d0675c2ede586c53615da0073228bab2c3d"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

