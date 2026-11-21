<p>
  <a href="https://audren.xyz">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/audren-xyz/audren/main/assets/brand/audren-wordmark-dark.svg" />
      <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/audren-xyz/audren/main/assets/brand/audren-wordmark-light.svg" />
      <img alt="Audren — Private money on Solana" src="https://raw.githubusercontent.com/audren-xyz/audren/main/assets/brand/audren-wordmark-light.svg" height="52" />
    </picture>
  </a>
</p>

**Private money on Solana. Existing tokens. One shared pool.**

Audren is an open-source, self-custodial privacy protocol on Solana (`sBPFv3`). Shield native SOL, Classic SPL tokens, and transferable Token-2022 mints without wrapper tokens; make private transfers, execute single-transaction private swaps through compatible DEX routers, and produce selective disclosure receipts — with local proofs, keys you control, no trusted setup, and no off-chain indexer.

### Repositories

| Repository | Description |
| --- | --- |
| [**`audren-xyz/audren`**](https://github.com/audren-xyz/audren) | Core `#![no_std]` Pinocchio sBPFv3 Solana program, Rust prover & client, published Codama/Anchor IDLs, `@audren/sdk`, self-hostable Privacy Relayer, and `audren.xyz` web app |
| [**`audren-xyz/examples`**](https://github.com/audren-xyz/examples) | Runnable Rust and TypeScript integrations for Solana Mainnet & Devnet |

### On-Chain Verification & Links

- **Live App & Docs:** [audren.xyz](https://audren.xyz) · [Architecture](https://audren.xyz/architecture/) · [Developers](https://audren.xyz/developers/)
- **Solana Program ID (Mainnet & Devnet):** [`AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3`](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3)
- **Solana Verified Build (`v0.2.0`):** [Solana Explorer Verified Build](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/verified-build) · [Program IDL](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/idl) · [Security Metadata](https://explorer.solana.com/address/AUDRBK6kVkQoEGm3EB7swd34SUPqrHZeNEkB5vZWVSv3/security)
- **Reference Privacy Relayer (optional & self-hostable):** [`relay.audren.xyz`](https://relay.audren.xyz/v1/info)
- **Security Disclosures:** `security@audren.xyz` — see [`SECURITY.md`](https://github.com/audren-xyz/audren/blob/main/SECURITY.md)
