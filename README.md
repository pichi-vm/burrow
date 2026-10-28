# burrow

burrow owns the kernel catalog (`KERNELS` / `Entry` / `resolve`) and download
cache for the pichi-vm test suites. Consumers must use this catalog and must not
fork the table.

`fetch(url)` downloads a URL once into a cache directory under the cargo
`target/` tree and returns the local path; later calls reuse it.
Keyed by URL, not content — a cache, not a verifier;
callers that need integrity pin the URL to an immutable artifact. Concurrent
callers are serialized per URL with an advisory file lock.

Intended as a dev-dependency for test suites that need real, cached fixtures
(e.g. kernel images) without re-downloading on every run.

## License

Apache-2.0 — see [LICENSE](LICENSE).
