# AIM Qwen3.8 27B-N

Olares app packaging for **AIM Qwen3.8 27B-N** — Qwen3.8-27B served by the
[NInfer](https://github.com/Neroued/ninfer) C++/CUDA inference engine on a single
RTX 5090, published through the custom `market.AImighty` source.

- Engine: upstream `Neroued/ninfer` pinned at `cde57e48` (sm_120a, CUDA 13.1)
- Weights: `neroued/Qwen3.8-27B-nvfp4-NInfer` (NVFP4, container v3), verified by SHA-256
- KV: NVFP4, C=1, 103,936-token context on 24 GB
- Spec decode: MTP3 + proposal head (`--lm-head-draft`), `--preserve-thinking`
- APIs: OpenAI Chat/Responses + Anthropic Messages, `/health`, `/v1/models`

## Image

`ghcr.io/bayerhazard/ninfer:cde57e48` — built by the GitHub Actions workflow in
`.github/workflows/build-ninfer.yml` from the upstream `Dockerfile`.

## Chart

The Helm chart lives in `aimqwen38ninfer/` (with the identical root
`OlaresManifest.yaml`), and is embedded as base64 in the `aimighty-market`
Cloudflare Pages source (`functions/_lib.ts`).
