# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in any Audren repository (`audren-xyz/audren`, `audren-xyz/examples`, BN254 Groth16 circuit, SDKs, Privacy Relayer, or web application), please report it privately to:

- **Email:** `security@audren.xyz`
- **Preferred language:** English (`en`)

Please include:
- Affected repository, component, commit hash, tag, or deployed address (`AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3`)
- Clear reproduction steps, proof-of-concept transaction or test case, and impact assessment
- Any suggested remediation if known

Do not open public GitHub issues or disclose active vulnerabilities publicly before coordinated remediation.

## In-Scope Components

- `audren-xyz/audren` — on-chain sBPFv3 Solana program (`program/`), `crates/audren-core/`, `crates/audren-circuits/` (`17,861` R1CS BN254 Groth16 & WASM prover), `crates/client/`, `crates/audren-ffi/` (`45` UniFFI exports), `@audren/sdk` (`packages/sdk/`), `AudrenSDK` (`packages/swift/`), `xyz.audren.sdk` (`packages/kotlin/`), Privacy Relayer (`apps/relay/`), and web application (`apps/web/`)
- `audren-xyz/examples` — official 4-language runnable integrations consuming the Audren SDKs

## Deployment Status & Boundaries

- **Groth16 ceremony provenance & pre-audit status:** `AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3` verifies proofs under BGM17 Groth16 ceremony keys anchored to the official Hermez/PSE Perpetual Powers of Tau (`powersOfTau28_hez_final_15.ptau`, 71+ independent public contributors) + zeroized Phase-2 contributions + live drand Quicknet (`#34194203`) & Solana Mainnet finalized blockhash (`#472705896`) beacon (`ceremony/transcript.json`). Additional community Phase-2 contributions remain open, and the program remains pre-audit and upgradeable until independent third-party audits conclude.
- **On-chain security metadata:** Canonical security metadata is published on-chain via Solana Program Metadata (`ProgM6JCCvbYkfKqJYHePx4xxSUSqJp7rh8Lyv7nk7S`, seed `"security"`) from [`idl/security.json`](https://github.com/audren-xyz/audren/blob/main/idl/security.json) and embedded directly in the sBPFv3 binary as a `.security.txt` section.
- **Reproducible verified builds:** Mainnet releases are built deterministically in the Solana Foundation `solana-verifiable-build` Docker container (`Agave 4.3.0`, `platform-tools v1.57`, `sBPFv3`) and attested on-chain via [`verify.osec.io`](https://verify.osec.io/status/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3).
- **Intentional public boundaries (not vulnerabilities):** Public deposits (`Tag 3`/`Tag 4`), withdrawals (`Tag 6`, including `WITHDRAW_FLAG_UNWRAP_WSOL`), external DeFi CPI execution (`Tag 7 ExecViaEscrow`), stateful DeFi positions opened by deterministic `DefiSessionKeypair` wallets, transaction fee payers, optional 1-input vs 2-input arity selection, and relayer/RPC network metadata are documented public boundaries. See [`ARCHITECTURE.md`](https://github.com/audren-xyz/audren/blob/main/ARCHITECTURE.md#privacy-boundaries-and-effective-anonymity).
