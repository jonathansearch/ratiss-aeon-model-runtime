<p align="center">
  <img src="docs/assets/logo.png" alt="RATISS Labs logo" width="180"/>
</p>

[![RATISS Labs](https://img.shields.io/badge/RATISS_Labs-Deep_Tech_Sovereign-06b6d4)](https://github.com/jonathansearch)

# RATISS Aeon Model Runtime

This private repository centralizes the **manifests, fingerprints and startup instructions** of the local models used by RATISS Aeon Prime. Binary weights published with a release are distribution copies; the licensing and provenance reference remains the official card of the vendor.

## Available models

| Model | Format | Size fingerprint | Target usage |
| --- | --- | --- | --- |
| Qwen2.5 0.5B Instruct Q4_K_M | GGUF | about 469 MB on disk | light local inference, routing, extraction and structured generation |
| Qwen2.5 1.5B Instruct Q4_K_M | GGUF | about 1.1 GB on disk | richer local reasoning, structured outputs and multilingual tasks |

## Retrieval and integrity

Download the `.gguf` file from the release matching the chosen model, then check it with the SHA-256 file published in the same assets.

```bash
sha256sum -c SHA256SUMS
```

## Local usage

The simplest way is to use Ollama, which automatically fetches the Q4_K_M version:

```bash
ollama run hf.co/Qwen/Qwen2.5-1.5B-Instruct-GGUF:Q4_K_M
```

To expose the GGUF file through a local OpenAI-compatible API, install `llama.cpp`, then run:

```bash
bash scripts/run-qwen-local.sh ./qwen2.5-1.5b-instruct-q4_k_m.gguf
```

The local API will be available on `http://127.0.0.1:8080/v1`.

## Why not version the binary in Git?

Weights of several hundred MB are not suited to ordinary Git commits. The release provides a versioned and reproducible download, while the repository keeps the documentation, the manifest, the fingerprint and the scripts needed for operation.

## Provenance and license

The models come from the official repositories [Qwen2.5-0.5B-Instruct-GGUF](https://huggingface.co/Qwen/Qwen2.5-0.5B-Instruct-GGUF) and [Qwen2.5-1.5B-Instruct-GGUF](https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct-GGUF). Qwen states an **Apache-2.0** license for these variants. Before any commercial redistribution, check the vendor's current terms.
