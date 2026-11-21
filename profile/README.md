<p>
  <a href="https://audren.xyz">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/audren-xyz/audren/main/assets/brand/audren-wordmark-dark.svg" />
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/audren-xyz/audren/main/assets/brand/audren-wordmark-light.svg" />
      <img alt="Audren — Private money on Solana" src="https://raw.githubusercontent.com/audren-xyz/audren/main/assets/brand/audren-wordmark-light.svg" height="52" />
    </picture>
  </a>
</p>

<p>
  <a href="https://github.com/audren-xyz/audren/actions/workflows/ci.yml"><img src="https://github.com/audren-xyz/audren/actions/workflows/ci.yml/badge.svg" alt="Core & 4 SDKs CI" /></a>
  <a href="https://github.com/audren-xyz/examples/actions/workflows/ci.yml"><img src="https://github.com/audren-xyz/examples/actions/workflows/ci.yml/badge.svg" alt="4-Language Examples Parity CI" /></a>
  <a href="https://github.com/audren-xyz/audren/releases/tag/v0.2.0"><img src="https://img.shields.io/badge/release-v0.2.0-121210" alt="Release v0.2.0" /></a>
  <a href="https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build"><img src="https://img.shields.io/badge/Solana%20Verified%20Build-sBPFv3-184433" alt="Solana Verified Build" /></a>
  <a href="https://github.com/audren-xyz/audren/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-434039" alt="Apache-2.0 License" /></a>
</p>

**Private money on Solana. Existing tokens. One shared pool.**

Audren is an open-source, self-custodial privacy protocol on Solana (`sBPFv3`, `#![no_std]`, `pinocchio 0.11.1`). Shield native SOL, Classic SPL tokens, and transferable Token-2022 mints without wrapper tokens; send private transfers across 32/64/128-slot rings, execute single-transaction private swaps through compatible DEX routers, and produce verifiable selective disclosure receipts — with local proofs, keys you control, no trusted setup, and no off-chain indexer.

### Repositories

| Repository | Description |
| --- | --- |
| [**`audren-xyz/audren`**](https://github.com/audren-xyz/audren) | Core `#![no_std]` Pinocchio sBPFv3 Solana program, **4 standardized official SDKs** (`Rust`, `TypeScript`, `Swift iOS/macOS`, `Kotlin Android/JVM`, `45` synced UniFFI exports) proven against [`spec/test-vectors.json`](https://github.com/audren-xyz/audren/blob/main/spec/test-vectors.json) and executed against the verified Mainnet `audren.so` in LiteSVM CI, published Codama v1.8.0 & Anchor v0.30+ IDLs, self-hostable Privacy Relayer, and `audren.xyz` web app |
| [**`audren-xyz/examples`**](https://github.com/audren-xyz/examples) | Standardized 6-building-block runnable examples across **Rust**, **TypeScript**, **Swift (iOS/macOS)**, and **Kotlin (Android/JVM)** — consuming the official SDKs directly with **100% byte-for-byte canonical stdout parity** (`Rust == TypeScript == Swift == Kotlin`) enforced in CI |

### Standardized Official SDKs & Empirical Verification

All 4 official SDKs implement the exact same **6 standardized building blocks** (`Keys`, `PDAs & Layouts`, `dataSlice[64..1120] Scanner`, `Local ZK Prover`, `Selective Disclosure & Institutional Audit`, `Relayer & Router`), verified continuously in CI:

| Language | Package | Engine | Continuous Empirical Verification |
| --- | --- | --- | --- |
| **Rust** | [`crates/client`](https://github.com/audren-xyz/audren/tree/main/crates/client) | Native `audren-client` (~50 ms `m=5`) | Conformance vectors + 7 LiteSVM E2E/adversarial suites + examples CI parity |
| **TypeScript** | [`packages/sdk`](https://github.com/audren-xyz/audren/tree/main/packages/sdk) | Zero-dep `@audren/sdk` + pure-TS `@audren/sdk/prover` | Conformance vectors + **real Mainnet `audren.so` LiteSVM CI** + examples CI parity |
| **Swift (iOS / macOS)** | [`packages/swift`](https://github.com/audren-xyz/audren/tree/main/packages/swift) | UniFFI over `crates/audren-ffi` (`45` exports, ~50 ms) | `swift test` conformance + **real Mainnet `audren.so` LiteSVM CI** + macOS examples CI parity |
| **Kotlin (Android / JVM)** | [`packages/kotlin`](https://github.com/audren-xyz/audren/tree/main/packages/kotlin) | UniFFI + JNA over `crates/audren-ffi` (`45` exports, ~50 ms) | `gradle test` conformance + **real Mainnet `audren.so` LiteSVM CI** + examples CI parity |

### On-Chain Verification & Links

- **Live App & Docs:** [audren.xyz](https://audren.xyz) · [Architecture](https://audren.xyz/architecture/) · [Developers](https://audren.xyz/developers/)
- **Solana Program ID (Mainnet & Devnet):** [`AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3`](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3)
- **Canonical Pool `#0` (`Permissionless`) PDA:** [`5Bvt5f5QMfsVb9TyX8bzkRMvAX6JSWwRtnymGveF9U3G`](https://explorer.solana.com/address/5Bvt5f5QMfsVb9TyX8bzkRMvAX6JSWwRtnymGveF9U3G)
- **Solana Verified Build (`v0.2.0`):** [Solana Explorer Verified Build](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build) (`0aa268a9...`) · [Program IDL](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/idl) · [Security Metadata](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/security)
- **Reference Privacy Relayer (optional & self-hostable):** [`relay.audren.xyz`](https://relay.audren.xyz/v1/info)
- **Security Disclosures:** `security@audren.xyz` — see [`SECURITY.md`](https://github.com/audren-xyz/.github/blob/main/SECURITY.md)
