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
  <a href="https://github.com/audren-xyz/audren/releases/tag/v1.3.0"><img src="https://img.shields.io/badge/release-v1.3.0-121210" alt="Release v1.3.0" /></a>
  <a href="https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build"><img src="https://img.shields.io/badge/Solana%20Verified%20Build-sBPFv3-184433" alt="Solana Verified Build" /></a>
  <a href="https://github.com/audren-xyz/audren/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-434039" alt="Apache-2.0 License" /></a>
</p>

**Private money on Solana. Existing tokens. One global multi-asset shielded pool.**

Audren is an open-source, self-custodial privacy protocol on Solana (`sBPFv3`, `#![no_std]`, `pinocchio 0.11.1`, `groth16-solana`). Native SOL, Classic SPL tokens, and transferable Token-2022 mints share one permissionless global 4-ary Depth-20 Multi-Asset Shielded Pool ($4^{20}$ note capacity, 16-lane-capable architecture starting at 4 active lanes) verified on-chain via `192 B` BN254 Groth16 proofs (`17,861` R1CS, `alt_bn128` syscall) in a single Solana Transaction v1 (`0x81`), with inline dual-ring `GlobalRootHistory` (zero background cranks), inline auto-`OpenPage`, protocol-agnostic `ExecViaEscrow` DeFi CPIs (`EXEC_FLAG_FEE_ON_OUTPUT`), atomic WSOL unwrapping (`WITHDRAW_FLAG_UNWRAP_WSOL`), zero-dust sweeps (`DEPOSIT_FLAG_FEE_FROM_AMOUNT`), Mode 1/Mode 2 compliance primitives, and zero-indexer ordinary Solana RPC wallet sync (`CompactWalletStore`).

> **Groth16 Ceremony & Pre-audit Status:** Audren's `vk_id = 0` parameters are anchored to the official Hermez Perpetual Powers of Tau (`powersOfTau28_hez_final_15.ptau`, 54 public contributions plus a beacon) plus two Audren-generated BGM17 Phase-2 contributions and a public drand Quicknet (`#34194203`) & Solana Mainnet slot `472705896` beacon ([`ceremony/transcript.json`](https://github.com/audren-xyz/audren/blob/main/ceremony/transcript.json)). Until an independent contributor joins, Phase-2 soundness relies on Audren having destroyed its contribution secrets. Additional community Phase-2 contributions remain open (adopted only through a program upgrade), and an independent third-party security audit is pending prior to revoking BPF upgrade authority.

### Repositories

| Repository | Description |
| --- | --- |
| [**`audren-xyz/audren`**](https://github.com/audren-xyz/audren) | Core `#![no_std]` Pinocchio sBPFv3 Solana program (`158,056 B`), BN254 Groth16 circuit (`JoinSplit4AryCircuit`, `17,861` R1CS) & deterministic WASM prover (`audren_circuits.wasm`), **4 optional Apache-2.0 SDKs** (`Rust`, `TypeScript`, `Swift iOS/macOS`, `Kotlin Android/JVM`, `52` synced zero-panic UniFFI exports) verified against [`spec/test-vectors.json`](https://github.com/audren-xyz/audren/blob/main/spec/test-vectors.json) and real deterministic `sBPFv3` `audren.so` in LiteSVM CI, published Codama v1.8.0 & Anchor v0.30+ IDLs, self-hostable Privacy Relayer, and `audren.xyz` web app |
| [**`audren-xyz/examples`**](https://github.com/audren-xyz/examples) | Standardized runnable examples across **Rust**, **TypeScript**, **Swift (iOS/macOS)**, and **Kotlin (Android/JVM)** — consuming the official SDKs with **100% byte-for-byte canonical stdout parity** (`Rust == TypeScript == Swift == Kotlin`) enforced in CI |

### SDKs & Capability Matrix

Integrators can interact directly with the permissionless on-chain program (via the published Codama/Anchor IDLs for deposits/admin and the documented raw binary framing + open-source prover for spends) or use any of the four optional Apache-2.0 SDKs (`12` PDAs, `106 B` SoA memos, `9` instruction tags, `33` error codes):

| Language | Package | Engine & Capabilities | Continuous Empirical Verification |
| --- | --- | --- | --- |
| **Rust** | [`crates/client`](https://github.com/audren-xyz/audren/tree/main/crates/client) | Native `audren-circuits` (`ark-groth16`, ~90–140 ms) · full keys, PDAs, builders, prover, `CompactWalletStore` RPC scanner & witness reconstruction, auto-`OpenPage` & tight CU helpers, Mode 1/2 compliance, `ExecViaEscrow` | Conformance vectors + `ceremony verify` + deterministic WASM SHA-256 + `litesvm_e2e` & `cross_sdk_litesvm` + examples CI parity |
| **TypeScript** | [`packages/sdk`](https://github.com/audren-xyz/audren/tree/main/packages/sdk) | Zero-WASM `@audren/sdk` + `audren_circuits.wasm` (`@audren/sdk/prover`) · full keys, PDAs, builders, prover, `CompactWalletStore` RPC scanner & witness reconstruction, auto-`OpenPage` & tight CU helpers, Mode 1/2 compliance, `AudrenRelayClient`, Tx v1 compiler, `ExecViaEscrow` | Conformance vectors + real `sBPFv3` `audren.so` `cross_sdk_litesvm` + examples CI parity |
| **Swift (iOS / macOS)** | [`packages/swift`](https://github.com/audren-xyz/audren/tree/main/packages/swift) | UniFFI over `crates/audren-ffi` (`52` zero-panic exports: `42` fallible `throws` + `10` infallible, ~120 ms) · keys, Bech32m, PDAs, decoders, memo crypto, native Groth16 proving from a prepared `4,611 B` witness, auto-`OpenPage` planning & tight CU helpers, all 9 instruction builders, Mode 1/2 compliance | `swift test` conformance + macOS examples CI parity (`Swift == Rust`) |
| **Kotlin (Android / JVM)** | [`packages/kotlin`](https://github.com/audren-xyz/audren/tree/main/packages/kotlin) | UniFFI + JNA over `crates/audren-ffi` (`52` zero-panic exports: `42` fallible `@Throws` + `10` infallible, ~120 ms) · keys, Bech32m, PDAs, decoders, memo crypto, native Groth16 proving from a prepared `4,611 B` witness, auto-`OpenPage` planning & tight CU helpers, all 9 instruction builders, Mode 1/2 compliance | `gradle test` conformance + Linux examples CI parity (`Kotlin == Rust`) |

### On-Chain Verification & Links

- **Live App & Docs:** [audren.xyz](https://audren.xyz) · [Architecture](https://audren.xyz/architecture/) · [Developers](https://audren.xyz/developers/)
- **Solana Program ID (Mainnet & Devnet):** [`AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3`](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3)
- **Canonical Pool `#0` PDA (`audren_pool`):** [`5Bvt5f5QMfsVb9TyX8bzkRMvAX6JSWwRtnymGveF9U3G`](https://explorer.solana.com/address/5Bvt5f5QMfsVb9TyX8bzkRMvAX6JSWwRtnymGveF9U3G)
- **GlobalRootHistory PDA (`audren_roots`):** [`249YJTuRtiKAnh346Tc18kF9bHrktdrTzyJMtvUKUgC7`](https://explorer.solana.com/address/249YJTuRtiKAnh346Tc18kF9bHrktdrTzyJMtvUKUgC7)
- **On-Chain Metadata & Verified Builds:** [Solana Explorer Verified Build](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build) · [OtterSec Status](https://verify.osec.io/status/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3) · [Program IDL](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/idl) · [Security Metadata](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/security)
- **Reference Privacy Relayer (optional & self-hostable):** [`relay.audren.xyz`](https://relay.audren.xyz/v1/info)
- **Security Disclosures:** `security@audren.xyz` · [`audren.xyz/.well-known/security.txt`](https://audren.xyz/.well-known/security.txt) — see [`SECURITY.md`](https://github.com/audren-xyz/.github/blob/main/SECURITY.md)
