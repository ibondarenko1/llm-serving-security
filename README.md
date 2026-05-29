..............# llm-serving-security

A practical security reference for the LLM serving and inference stack -
vLLM, NVIDIA Triton, lmdeploy, BentoML, SGLang, Ollama, and TGI.

Most AI-security material is about model behavior: prompt injection, jailbreaks,
alignment. This repo is about the layer underneath - the process that loads the
weights, deserializes the request, and answers on a port. That layer has its own
vulnerability classes and its own CVEs. It is also where a remote code execution
actually lands.

## What is here

- **[vulnerability-classes.md](vulnerability-classes.md)** - the recurring
  vulnerability classes in serving frameworks: unsafe deserialization, exposed
  ZeroMQ, `trust_remote_code` execution, SSRF in remote-resource loading, path
  traversal, unauthenticated APIs, KV-cache multi-tenancy. Read this first; the
  matrix references it.
- **[cve-matrix.md](cve-matrix.md)** - a tracked list of known CVEs and
  advisories per framework, with the vulnerability class, affected and fixed
  versions, and severity. The page to check before and during a deployment.
- **[hardening.md](hardening.md)** - a deployment hardening checklist: a
  cross-framework baseline plus framework-specific notes.

## Who this is for

Platform and ML-infrastructure engineers who run a serving framework in
production, and security engineers who have to assess one. If you are deploying
vLLM or Triton, the hardening checklist is a pre-flight list and the CVE matrix
tells you what your version exposes.

## Scope

The serving and inference layer only: the framework process, its request
handling, its model-loading path, its inter-process and network surface.

Out of scope: prompt injection, jailbreaks, training-time attacks, and model
alignment. Those are covered well elsewhere; this reference stays narrow on
purpose.

## Status

Work in progress, maintained as new advisories land. The CVE matrix is seeded
and grows by contribution - see [CONTRIBUTING.md](CONTRIBUTING.md). Every entry
should be verifiable against an upstream advisory; if a row is stale or wrong,
open an issue.

## License

MIT. See [LICENSE](LICENSE).
