# Contributing to Audren

Thank you for contributing to Audren! Every repository under [`audren-xyz`](https://github.com/audren-xyz) enforces strict zero-drift checks, cross-language conformance, and empirical verification in CI.

## Core Protocol & 4 Official SDKs (`audren-xyz/audren`)

See [`audren-xyz/audren/CONTRIBUTING.md`](https://github.com/audren-xyz/audren/blob/main/CONTRIBUTING.md) and [`AGENTS.md`](https://github.com/audren-xyz/audren/blob/main/AGENTS.md). Before opening a PR (in cold-start order):

1. Run `python3 idl/verify-idl.py` (verifies Codama/Anchor IDLs, all 4 SDKs, all 52 synced UniFFI exports + `<REDACTED>` redaction, WASM/PK/worker cache-buster pins, `spec/test-vectors.json`, docs, and toolchain pins).
2. Check isolated sBPFv3 manifests (`program/`, `tests/mock-router/`, `tests/mock-hook/` via `--manifest-path`), build `@audren/sdk` (`pnpm --dir packages/sdk install --frozen-lockfile && pnpm --dir packages/sdk build`), build deterministic sBPFv3 ELFs into `target/deploy/` (`scripts/build-sbf.py`), and build the native FFI shared library (`cargo build -p audren-ffi --release`, required for Swift/Kotlin).
3. Run the full Rust (`cargo test --release --workspace`), TypeScript (`packages/sdk`, `apps/relay`, `apps/web`), Swift (`(cd packages/swift && swift test)` on macOS), and Kotlin (`(cd packages/kotlin && gradle test)` on JDK 21 + Gradle 9.7.1) suites against the real sBPFv3 `audren.so`, `audren_mock_router.so`, and `audren_mock_hook.so`.

## Standardized 4-Language Examples (`audren-xyz/examples`)

See [`audren-xyz/examples/AGENTS.md`](https://github.com/audren-xyz/examples/blob/main/AGENTS.md). Before opening a PR:

1. Never duplicate PDA seeds, account offsets, instruction layouts, or `JUPITER_CPI_EXCLUDED_DEXES` — always import the official SDKs.
2. Keep all 4 `quickstart` examples (`rust`, `typescript`, `swift`, `kotlin`) 100% byte-for-byte identical in canonical stdout (`diff -u` enforced in CI on Linux & macOS).

## Security & Licensing

- **Security issues:** Report privately to `security@audren.xyz` — see [`SECURITY.md`](./SECURITY.md).
- **Secrets:** Never commit keypairs, `.credentials/`, `wrangler.prod.jsonc`, `.dev.vars`, private RPC URLs, or operator configs.
- **License:** All contributions are licensed under Apache-2.0.
