# Contributing to Audren

Thank you for contributing to Audren! Every repository under [`audren-xyz`](https://github.com/audren-xyz) enforces strict zero-drift checks, cross-language conformance, and empirical verification in CI.

## Core Protocol & 4 Official SDKs (`audren-xyz/audren`)

See [`audren-xyz/audren/CONTRIBUTING.md`](https://github.com/audren-xyz/audren/blob/main/CONTRIBUTING.md) and [`AGENTS.md`](https://github.com/audren-xyz/audren/blob/main/AGENTS.md). Before opening a PR:

1. Run `python3 idl/verify-idl.py` (verifies Codama/Anchor IDLs, all 4 SDKs, all 45 synced UniFFI exports, `spec/test-vectors.json`, docs, and toolchain pins).
2. Run Rust, TypeScript, Swift, and Kotlin conformance suites + `AUDREN_REQUIRE_SBF=1 cargo test -p audren-ffi --test cross_sdk_litesvm -- --nocapture` against the real sBPFv3 `audren.so`.

## Standardized 4-Language Examples (`audren-xyz/examples`)

See [`audren-xyz/examples/AGENTS.md`](https://github.com/audren-xyz/examples/blob/main/AGENTS.md). Before opening a PR:

1. Never duplicate PDA seeds, account offsets, instruction layouts, or `JUPITER_CPI_EXCLUDED_DEXES` — always import the official SDKs.
2. Keep all 4 `quickstart` examples (`rust`, `typescript`, `swift`, `kotlin`) 100% byte-for-byte identical in canonical stdout (`diff -u` enforced in CI on Linux & macOS).

## Security & Licensing

- **Security issues:** Report privately to `security@audren.xyz` — see [`SECURITY.md`](./SECURITY.md).
- **Secrets:** Never commit keypairs, `.credentials/`, private RPC URLs, or operator configs.
- **License:** All contributions are licensed under Apache-2.0.
