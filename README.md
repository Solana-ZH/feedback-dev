# Solana Contract Development: Feedback & Tools

Feel free to leave your feedback for us to improve the Solana developer experience

### 1. Can I generate IDL for non-Anchor programs?

It’s possible to auto-generate IDLs for non-Anchor frameworks, but support varies by tool. Full automation is still limited and depends on how well the framework integrates with Shank or custom tooling.

### 2. [daog1/discriminator](https://github.com/daog1/discriminator)

I've enhanced this library to help analyze on-chain data more efficiently. Notable features:

- Supports base64 discriminator printing for easier web lookup  
- Fixed a bug where discriminators weren’t snake-cased before hashing  
- Added support for event discriminators (previously missing)  

Useful for dynamic parsing of on-chain data.

![discriminator-print](https://user-images.githubusercontent.com/example1.png)  
![discriminator-ui](https://user-images.githubusercontent.com/example2.png)

---

### 3. Is there an equivalent to `openzeppelin-contracts` on Solana?

---

### 4. Solana localnet conflicts with Anchor

Anchor versions need to be compatible with both the Solana CLI and `solana-test-validator`. Version mismatches can cause runtime or build issues. A streamlined solution or compatibility layer would be helpful in the future.

---

### 5. `cargo update` is risky for Anchor

Updating dependencies can break builds due to mismatches between Solana Rust toolchain versions and upstream crates.  
To avoid issues:
- Ensure `cargo build-sbf` uses the same Rust version as Anchor's official toolchain.
- Avoid blind `cargo update` in production projects.

---

### 6. Anchor 0.29 with Rust 1.79.0 support

Many developers still use Anchor 0.29. I've patched my fork to support `proc_macro2 1.0.95` and Rust 1.79.0.  
You can clone and build locally from:  
👉 https://github.com/daog1/anchor/commits/solana17/

---

### 7. Can Solana contracts be verified and viewed in the browser?

Unlike EVM, Solana does not yet support public on-chain contract source viewing in explorers. You must manually locate the code or IDL and use tools like Codama for reverse analysis. It is inconvenient. 

---

### 8. Can a closed program ID be reused? I don't want to change program ID every time.

---

### 9. Surfpool custom account support

Surfpool now supports custom account logic without LiteSVM. However:
- Many features are not fully integrated
- Transactions might not yet appear in Solscan
We hope future updates improve compatibility.

---

### 10. Surfpool flash loan overflow

When testing flash loans on mainnet, Surfpool showed overflow errors due to clock discrepancies. Fix submitted:  
🔗 https://github.com/txtx/surfpool/pull/101

---

### 11. mpl-core error: "All zero account discriminators are not allowed"

This error appears when using `BaseCollectionV1` with all-zero discriminators. Possible discussion and fix:  
🔗 https://github.com/solana-foundation/anchor/issues/3700

---

### 12. Pinoc
Pinocchio does not have `declare_program!` macro, and it seems that it is not possible to call instructions or cpi through idl. I hope it will be supported in the future.
