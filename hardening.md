# Deployment Hardening Checklist

A pre-flight checklist for putting an LLM serving framework into production. The
**baseline** applies to every framework; the per-framework sections capture
specifics. Each item maps to a class in
[vulnerability-classes.md](vulnerability-classes.md).

## Baseline - every framework

### Network surface
- [ ] The serving API is not exposed to the public internet. It sits behind an
      authenticated gateway or on a private network.
- [ ] Metrics, admin, and model-management endpoints are not publicly reachable.
- [ ] Inter-process channels (ZeroMQ and similar) bind to localhost or a Unix
      socket, never a routable interface.

### Model loading
- [ ] `trust_remote_code` is off by default; enabling it is an explicit,
      per-model decision tied to a trusted model source.
- [ ] Model files load from a known, controlled location, not a caller-supplied
      path.
- [ ] Where the framework loads tensors, it uses `weights_only=True` or
      safetensors rather than unbounded pickle.

### Request handling
- [ ] The API authenticates callers.
- [ ] Request size, concurrency, and generation length are bounded.
- [ ] Any feature that fetches a remote resource (image, audio, or document URL)
      runs through an allowlist and blocks internal and metadata addresses.

### Process and host
- [ ] The framework runs as a non-root user, inside a container or VM boundary.
- [ ] Multi-tenant deployments isolate tenants at the process or instance level,
      not in-process.
- [ ] The framework version is current and tracked against
      [cve-matrix.md](cve-matrix.md).

## vLLM

_Framework-specific notes - contributions welcome._

## NVIDIA Triton

_Framework-specific notes - contributions welcome._

## lmdeploy

_Framework-specific notes - contributions welcome._

## BentoML

_Framework-specific notes - contributions welcome._

## SGLang

_Framework-specific notes - contributions welcome._

## Ollama

_Framework-specific notes - contributions welcome._

## TGI

_Framework-specific notes - contributions welcome._
