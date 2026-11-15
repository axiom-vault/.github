# AxiomVault

An encrypted vault with client-side encryption, written in Rust. Files are encrypted on your device before they reach any storage, so the storage provider only ever sees ciphertext: contents, file names and the directory tree.

> [!WARNING]
> AxiomVault is in early development and not production ready. APIs and formats may still change. Do not use it for sensitive data in production.

## What it does

- **Encryption:** XChaCha20-Poly1305 for content and file names, Argon2id for the password, Blake2b-derived per-file and per-directory keys, and chunked streaming encryption with per-chunk authentication.
- **Storage:** a local folder or Google Drive. Dropbox, OneDrive and iCloud are planned.
- **Sync:** on-demand or periodic, with conflict detection and a choice of how to resolve conflicts.
- **Access:** a command line, an interactive session, a FUSE mount, a WebDAV server and an MCP server over stdio.
- **Hardware keys:** optional YubiKey challenge-response.

## Repositories

| Repository | What it is |
|------------|------------|
| [axiom-core](https://github.com/axiom-vault/axiom-core) | The shared Rust library: crypto, vault engine, storage providers, sync, FUSE, WebDAV, MCP and the C-ABI for mobile clients |
| [axiom-cli](https://github.com/axiom-vault/axiom-cli) | The `axiom` command-line client |
| [axiom-vault.github.io](https://github.com/axiom-vault/axiom-vault.github.io) | Source of the documentation site |
| [homebrew-tap](https://github.com/axiom-vault/homebrew-tap) | Homebrew tap, filled once a stable 2.x release ships |

## Try it

```bash
cargo install --git https://github.com/axiom-vault/axiom-cli axiomvault-cli --bin axiom
axiom vault create --name MyVault --path ~/my-vault
axiom file add --vault-path ~/my-vault --source ~/notes.txt --dest /notes.txt
axiom file list --vault-path ~/my-vault
```

Prebuilt binaries and pre-releases are on the [axiom-cli releases page](https://github.com/axiom-vault/axiom-cli/releases). Documentation: **[axiom-vault.github.io](https://axiom-vault.github.io/)**.

## Security

Please report vulnerabilities privately as described in [SECURITY.md](https://github.com/axiom-vault/axiom-core/blob/main/SECURITY.md), not in public issues.

## License

Apache-2.0.
