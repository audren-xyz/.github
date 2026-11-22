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
  <a href="https://github.com/audren-xyz/audren/releases/tag/v1.0.0"><img src="https://img.shields.io/badge/release-v1.0.0-121210" alt="Release v1.0.0" /></a>
  <a href="https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build"><img src="https://img.shields.io/badge/Solana%20Verified%20Build-sBPFv3-184433" alt="Solana Verified Build" /></a>
  <a href="https://github.com/audren-xyz/audren/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-434039" alt="Apache-2.0 License" /></a>
</p>

**Private money on Solana. Existing tokens. One global multi-asset shielded pool.**

Audren is an open-source, self-custodial privacy protocol on Solana (`sBPFv3`, `#![no_std]`, `pinocchio 0.11.1`, `groth16-solana`). Native SOL, Classic SPL tokens, and transferable Token-2022 mints share one permissionless global 4-ary Depth-20 Multi-Asset Shielded Pool ($4^{20}$ note capacity, 16-lane-capable architecture starting at 4 active lanes) verified on-chain via `192 B` BN254 Groth16 proofs (`17,861` R1CS, `alt_bn128` syscall) in a single Solana Transaction v1 (`0x81`), with protocol-agnostic `ExecViaEscrow` DeFi CPIs (`EXEC_FLAG_FEE_ON_OUTPUT`), atomic WSOL unwrapping (`WITHDRAW_FLAG_UNWRAP_WSOL`), zero-dust sweeps (`DEPOSIT_FLAG_FEE_FROM_AMOUNT`), Mode 1/Mode 2 compliance primitives, and zero-indexer ordinary Solana RPC wallet sync (`CompactWalletStore`).

> **Pre-audit & Groth16 MPC ceremony status:** Audren is pre-audit and currently embeds `DEV_DETERMINISTIC_VK`. A public Phase-2 Groth16 MPC ceremony and independent audit are planned prior to production custody, and the program remains upgradeable until audits and ceremony verification conclude.

### Repositories

| Repository | Description |
| --- | --- |
| [**`audren-xyz/audren`**](https://github.com/audren-xyz/audren) | Core `#![no_std]` Pinocchio sBPFv3 Solana program (`150,848 B`), BN254 Groth16 circuit (`JoinSplit4AryCircuit`, `17,861` R1CS) & WASM prover (`audren_circuits.wasm`), **4 standardized official SDKs** (`Rust`, `TypeScript`, `Swift iOS/macOS`, `Kotlin Android/JVM`, `45` synced UniFFI exports) proven against [`spec/test-vectors.json`](https://github.com/audren-xyz/audren/blob/main/spec/test-vectors.json) and executed against real deterministic `sBPFv3` `audren.so` in LiteSVM CI, published Codama v1.8.0 & Anchor v0.30+ IDLs, self-hostable Privacy Relayer, and `audren.xyz` web app |
| [**`audren-xyz/examples`**](https://github.com/audren-xyz/examples) | Standardized 6-building-block runnable examples across **Rust**, **TypeScript**, **Swift (iOS/macOS)**, and **Kotlin (Android/JVM)** — consuming the official SDKs directly with **100% byte-for-byte canonical stdout parity** (`Rust == TypeScript == Swift == Kotlin`) enforced in CI |

### Standardized Official SDKs & Empirical Verification

All 4 official SDKs implement the exact same **6 standardized building blocks** (`Keys` incl. `DefiSessionKeypair`, `13 PDAs & Decoders`, `Zero-Indexer CompactWalletStore & 90 B SoA Memos`, `Local 192 B BN254 Groth16 Prover & 9 Instruction Builders`, `Mode 1 Selective Disclosure & Mode 2 FullViewingKey`, `Relayer & ExecViaEscrow CPI`), verified continuously in CI:

| Language | Package | Engine | Continuous Empirical Verification |
| --- | --- | --- | --- |
| **Rust** | [`crates/client`](https://github.com/audren-xyz/audren/tree/main/crates/client) | Native `audren-circuits` (`ark-groth16`, ~90–140 ms) | Conformance vectors + LiteSVM E2E & adversarial suites + examples CI parity |
| **TypeScript** | [`packages/sdk`](https://github.com/audren-xyz/audren/tree/main/packages/sdk) | Zero-WASM `@audren/sdk` + `audren_circuits.wasm` (`@audren/sdk/prover`) | Conformance vectors + **real sBPFv3 `audren.so` LiteSVM CI** + examples CI parity |
| **Swift (iOS / macOS)** | [`packages/swift`](https://github.com/audren-xyz/audren/tree/main/packages/swift) | UniFFI over `crates/audren-ffi` (`45` exports, ~120 ms) | `swift test` conformance + **real sBPFv3 `audren.so` LiteSVM CI** + macOS examples CI parity |
| **Kotlin (Android / JVM)** | [`packages/kotlin`](https://github.com/audren-xyz/audren/tree/main/packages/kotlin) | UniFFI + JNA over `crates/audren-ffi` (`45` exports, ~120 ms) | `gradle test` conformance + **real sBPFv3 `audren.so` LiteSVM CI** + examples CI parity |

### On-Chain Verification & Links

- **Live App & Docs:** [audren.xyz](https://audren.xyz) · [Architecture](https://audren.xyz/architecture/) · [Developers](https://audren.xyz/developers/)
- **Solana Program ID (Mainnet & Devnet):** [`AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3`](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3)
- **Canonical Pool `#0` PDA (`audren_v2_pool`):** [`8CN7uxRdQGjuAaZQVVcHRZbptSzvgfUv7tg8EarLHztF`](https://explorer.solana.com/address/8CN7uxRdQGjuAaZQVVcHRZbptSzvgfUv7tg8EarLHztF)
- **On-Chain Metadata & Verified Builds:** [Solana Explorer Verified Build](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build) · [Program IDL](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/idl) · [Security Metadata](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/security)
- **Reference Privacy Relayer (optional & self-hostable):** [`relay.audren.xyz`](https://relay.audren.xyz/v1/info)
- **Security Disclosures:** `security@audren.xyz` — see [`SECURITY.md`](https://github.com/audren-xyz/.github/blob/main/SECURITY.md)
