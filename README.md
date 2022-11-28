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
| `12.2.1_git20220924-r4` `latest` | `sha256:faed983409a84cf927e1dd9b27323890f8d3b6da93326d5a9f9e5381766a968a`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:faed983409a84cf927e1dd9b27323890f8d3b6da93326d5a9f9e5381766a968a) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r3` | `sha256:f0b83d7c71c2d2e2e97b8e12ad80707f2103341b97e2d499ba8e214fda62b025`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f0b83d7c71c2d2e2e97b8e12ad80707f2103341b97e2d499ba8e214fda62b025) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221118` | `sha256:68fcf7e1e7ae56fbdd05bcff0b06f2a8592a00f5c189141a8d1e8ef835910c60`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:68fcf7e1e7ae56fbdd05bcff0b06f2a8592a00f5c189141a8d1e8ef835910c60) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration` `migration-12` `migration-12.2` `migration-12.2.1_git20220924` `migration-12.2.1_git20220924-r4` `migration-20221128` | `sha256:12690069699b704f967bb1d85001fa52ac6e4312cd25fe0c922d06d4e392156b`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:12690069699b704f967bb1d85001fa52ac6e4312cd25fe0c922d06d4e392156b) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221124` | `sha256:fc9001fe1aadd4235b669f58203a3051ab99f16532038dd57dc51cc90e5d8653`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:fc9001fe1aadd4235b669f58203a3051ab99f16532038dd57dc51cc90e5d8653) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221126` | `sha256:dd5b5247bc4075d33665e9a9a774b065dc7503dd0c12a9c37aeffcd5caae4241`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:dd5b5247bc4075d33665e9a9a774b065dc7503dd0c12a9c37aeffcd5caae4241) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221127` | `sha256:4c8ff44c7b8df32a58389cf15e3ab1431c78280679f042b05eaeebd369d42f6c`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:4c8ff44c7b8df32a58389cf15e3ab1431c78280679f042b05eaeebd369d42f6c) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `12.2.1_git20220924-r2` | `sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:6155dbf4b11c4db57dafffa60f0ed26f24cc729fb2b859abec4ecb39e0128b63) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221119` | `sha256:b157be8b613f1a39442eaec30d0d94a4e36e0c90f5e91d87109d1bc16fe5b3b3`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:b157be8b613f1a39442eaec30d0d94a4e36e0c90f5e91d87109d1bc16fe5b3b3) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221121` | `sha256:a6a3cd31c1622701f633cd59fc77e430e39d764a541c42666c3e219af6fb1818`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:a6a3cd31c1622701f633cd59fc77e430e39d764a541c42666c3e219af6fb1818) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221122` | `sha256:f5be3789e050f87c0d182da3178c501fa6643f0cd34b079cc8ce97c346534fb2`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:f5be3789e050f87c0d182da3178c501fa6643f0cd34b079cc8ce97c346534fb2) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221123` | `sha256:c3ca2055d34e86165e6cdc02b0845f95d59dbe054254f264a1ba66caea6191ce`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:c3ca2055d34e86165e6cdc02b0845f95d59dbe054254f264a1ba66caea6191ce) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221120` | `sha256:521ec15ca2dd53ade0e331d57ffa052708cc93f5948f77626667f7748d1ec038`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:521ec15ca2dd53ade0e331d57ffa052708cc93f5948f77626667f7748d1ec038) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |
| `migration-20221125` | `sha256:efcd4cb95d2e7416a25ffe6aa56e0dfb9d37691cb5e7112bf55c7ec371933859`<br/>[View entry in Rekor](https://rekor.tlog.dev/?hash=sha256:efcd4cb95d2e7416a25ffe6aa56e0dfb9d37691cb5e7112bf55c7ec371933859) | `386` `amd64` `arm64` `armv6` `armv7` `ppc64le` `riscv64` `s390x` |


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
        "docker-manifest-digest": "sha256:faed983409a84cf927e1dd9b27323890f8d3b6da93326d5a9f9e5381766a968a"
      },
      "type": "cosign container image signature"
    },
    "optional": {
      "1.3.6.1.4.1.57264.1.1": "https://token.actions.githubusercontent.com",
      "1.3.6.1.4.1.57264.1.2": "schedule",
      "1.3.6.1.4.1.57264.1.3": "58a7a0512eeb6f4158b15d4beb72989509031e31",
      "1.3.6.1.4.1.57264.1.4": "Create Release",
      "1.3.6.1.4.1.57264.1.5": "chainguard-images/gcc-musl",
      "1.3.6.1.4.1.57264.1.6": "refs/heads/main",
      "Bundle": {
        "SignedEntryTimestamp": "MEUCIQD1/bcgG/57HS6X0BkeL20Kxtzn/5NCKU1GXikJ7qQleQIgU8yJvaSea2FRrLHesMC9LeUsEaxZZOKCMYGPgBmUiQo=",
        "Payload": {
          "body": "eyJhcGlWZXJzaW9uIjoiMC4wLjEiLCJraW5kIjoiaGFzaGVkcmVrb3JkIiwic3BlYyI6eyJkYXRhIjp7Imhhc2giOnsiYWxnb3JpdGhtIjoic2hhMjU2IiwidmFsdWUiOiJhMDRjN2QyOWIwMTI0YzRiYTlkNzA5Zjk0MTNjMTBjM2QzMWExNGRlOTkwMzlkOGI2ZGFkNTNjZTJjNWYwMDRmIn19LCJzaWduYXR1cmUiOnsiY29udGVudCI6Ik1FVUNJQmVEdnJDY1MvRzdkc3BDb3VrbHczWURrbmh0YkZNVXI0Y0E1bUNlc1pXVUFpRUF6SmcyaXYzK2MwcnNkWXRnNmhKQ1pKWjFCS0svVE84ck9sL2luSUZOb053PSIsInB1YmxpY0tleSI6eyJjb250ZW50IjoiTFMwdExTMUNSVWRKVGlCRFJWSlVTVVpKUTBGVVJTMHRMUzB0Q2sxSlNVUnpSRU5EUVhwaFowRjNTVUpCWjBsVlNsVmxhMk56UzFScVEwUTVablZxTVVZMlZXcENNVnBFYld4TmQwTm5XVWxMYjFwSmVtb3dSVUYzVFhjS1RucEZWazFDVFVkQk1WVkZRMmhOVFdNeWJHNWpNMUoyWTIxVmRWcEhWakpOVWpSM1NFRlpSRlpSVVVSRmVGWjZZVmRrZW1SSE9YbGFVekZ3WW01U2JBcGpiVEZzV2tkc2FHUkhWWGRJYUdOT1RXcEplRTFVU1RSTlJFRjNUWHBCTlZkb1kwNU5ha2w0VFZSSk5FMUVRWGhOZWtFMVYycEJRVTFHYTNkRmQxbElDa3R2V2tsNmFqQkRRVkZaU1V0dldrbDZhakJFUVZGalJGRm5RVVZEU3pjeVkwWkJNVVpGTW1acVQwUkxWRVJYYWxwT1ZEWnNOSG80WW1acVExZFNNRFVLTTBScmJFUlpOVFZuYkRaTFZVRk9jRWQwTmtoUkwyTlJjekptYjBGYVdXZ3ZVMVF4ZFhGcmR5OW9VWFEwU0hSbGMzRlBRMEZzVlhkblowcFNUVUUwUndwQk1WVmtSSGRGUWk5M1VVVkJkMGxJWjBSQlZFSm5UbFpJVTFWRlJFUkJTMEpuWjNKQ1owVkdRbEZqUkVGNlFXUkNaMDVXU0ZFMFJVWm5VVlZxTWpJM0NraHJaQ3NyTkhrM1VqRkNTMUpWSzNOTmRIQTFaMmhOZDBoM1dVUldVakJxUWtKbmQwWnZRVlV6T1ZCd2VqRlphMFZhWWpWeFRtcHdTMFpYYVhocE5Ga0tXa1E0ZDJGbldVUldVakJTUVZGSUwwSkhRWGRZYjFwallVaFNNR05JVFRaTWVUbHVZVmhTYjJSWFNYVlpNamwwVERKT2IxbFhiSFZhTTFab1kyMVJkQXBoVnpGb1dqSldla3d5WkdwWmVURjBaRmhPYzB4NU5XNWhXRkp2WkZkSmRtUXlPWGxoTWxwellqTmtla3d6U214aVIxWm9ZekpWZFdWWFJuUmlSVUo1Q2xwWFducE1NbWhzV1ZkU2Vrd3lNV2hoVnpSM1QxRlpTMHQzV1VKQ1FVZEVkbnBCUWtGUlVYSmhTRkl3WTBoTk5reDVPVEJpTW5Sc1ltazFhRmt6VW5BS1lqSTFla3h0WkhCa1IyZ3hXVzVXZWxwWVNtcGlNalV3V2xjMU1FeHRUblppVkVGWFFtZHZja0puUlVWQldVOHZUVUZGUTBKQmFIcFpNbWhzV2toV2N3cGFWRUV5UW1kdmNrSm5SVVZCV1U4dlRVRkZSRUpEWnpGUFIwVXpXVlJCTVUxVVNteGFWMGt5V21wUmVFNVVhR2xOVkZaclRrZEtiRmxxWTNsUFZHYzFDazVVUVRWTlJFMTRXbFJOZUUxQ2QwZERhWE5IUVZGUlFtYzNPSGRCVVZGRlJHdE9lVnBYUmpCYVUwSlRXbGQ0YkZsWVRteE5RMmRIUTJselIwRlJVVUlLWnpjNGQwRlJWVVZIYlU1dldWZHNkVm96Vm1oamJWRjBZVmN4YUZveVZucE1NbVJxV1hreGRHUllUbk5OUWpCSFEybHpSMEZSVVVKbk56aDNRVkZaUlFwRU0wcHNXbTVOZG1GSFZtaGFTRTEyWWxkR2NHSnFRMEpwZDFsTFMzZFpRa0pCU0ZkbFVVbEZRV2RTT1VKSWMwRmxVVUl6UVU0d09VMUhja2Q0ZUVWNUNsbDRhMlZJU214dVRuZExhVk5zTmpRemFubDBMelJsUzJOdlFYWkxaVFpQUVVGQlFtaE1kVXhqYzFGQlFVRlJSRUZGWjNkU1owbG9RVTloU1hVM1RFSUtkRXgwVWtJMGEyUjFNV2haZG05aU5IWjZOMm8yVTJsMGR5OURabXA2WVhoV1MyMDBRV2xGUVRaSVlrSjJVV3hOYzNOWE4ydFlaMWg2WVVod1ZYRkVTZ3AwVTFWUWFtRlliREZwVDJGd1RrMXJibWxuZDBObldVbExiMXBKZW1vd1JVRjNUVVJoUVVGM1dsRkpkMVJrVEcxblkwUkRhMmhzTVdsaGFWZDJWVFp3Q21aWVdqWnhaRUY2VFVweUt6WkxWVFZtTlhWSmVITlpTWGR6TjFaQmVHRmlURlpRZEVaRWJWcE5hRXRuUVdwRlFUZDZLek5oTmpCS1NrOVBLemxPTnpFS2F6TmxObXhTVkZkUFJ6UlFja3BxU21ocVRVaDFRMEZMUkRBMk5rdzFRbk42ZDFveFJIWm1OSHB5WjNWb2JFSkVDaTB0TFMwdFJVNUVJRU5GVWxSSlJrbERRVlJGTFMwdExTMEsifX19fQ==",
          "integratedTime": 1669593822,
          "logIndex": 7976633,
          "logID": "c0d23d6ad406973f9559f3ba2d1ca01f84147d8ffc5b8445c224f98b9591801d"
        }
      },
      "Issuer": "https://token.actions.githubusercontent.com",
      "Subject": "https://github.com/chainguard-images/gcc-musl/.github/workflows/release.yaml@refs/heads/main",
      "githubWorkflowName": "Create Release",
      "githubWorkflowRef": "refs/heads/main",
      "githubWorkflowRepository": "chainguard-images/gcc-musl",
      "githubWorkflowSha": "58a7a0512eeb6f4158b15d4beb72989509031e31",
      "githubWorkflowTrigger": "schedule",
      "run_attempt": "1",
      "run_id": "3560558845",
      "sha": "58a7a0512eeb6f4158b15d4beb72989509031e31"
    }
  }
]
```

You can verify that the image was built in Github Actions in this repository from the `Issuer` and `Subject` fields.
</details>

## Build

This image is built with [apko](https://github.com/chainguard-dev/apko).

