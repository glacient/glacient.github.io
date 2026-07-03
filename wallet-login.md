---
title: Wallet login
eyebrow: Get started
summary: Sign in to Glacient with any EVM wallet using Sign-In with Ethereum (SIWE). Gasless, non-custodial, and grants no permission to move funds.
permalink: /wallet-login/
---

Glacient supports web3 authentication through [Sign-In with Ethereum](https://eips.ethereum.org/EIPS/eip-4361) (SIWE). Your wallet is your identity: the same address always resolves to the same account, and no email or password is required.

## Supported wallets

Any EVM-compatible wallet works, including:

- MetaMask
- Coinbase Wallet
- Rainbow
- Rabby
- WalletConnect-compatible mobile wallets
- Hardware wallets (Ledger, Trezor) via MetaMask or WalletConnect

Wallets on non-EVM chains (Solana, Bitcoin, Cosmos) are not currently supported for login.

## The login flow

1. On the login screen, click **Login with Wallet**.
2. Your wallet extension prompts you to connect. Pick the address you want to use.
3. Glacient shows a **Confirm Signature** screen displaying the connected address.
4. Click **Finalize Signing**. Your wallet opens a Sign-In with Ethereum prompt containing a plaintext message: the domain, the address, a nonce, and a timestamp.
5. Approve the signature in your wallet.

You're signed in. If this is the first time Glacient has seen the address, a profile is created automatically; there's no separate signup flow.

## What the signature does

The SIWE message is a **login credential**, not a transaction.

- **Gasless.** Signing costs nothing and produces no on-chain footprint.
- **Proves control.** The signature demonstrates that whoever is signing in controls the private key for the address.
- **No permissions granted.** The signature does not authorize Glacient to move funds, approve tokens, submit transactions, or interact with any protocol on your behalf.
- **Scoped to the session.** A fresh nonce and timestamp are used for each login, so the signature cannot be replayed later.

<div class="callout note">
<strong>Glacient will never ask you to sign a transaction during login.</strong> If the wallet prompt shows anything other than a plaintext SIWE message — a token approval, a permit, a contract call, an <code>eth_sendTransaction</code> — reject it and report the issue.
</div>

## Why wallet login

- **No password to lose or leak.** Your wallet's own security (hardware key, passphrase, biometrics) is the login.
- **Same identity across devices.** Sign in from any browser where you have the wallet available.
- **Unlocks My Investments.** Wallet-authenticated accounts can use the discovery flow that surfaces vaults you've already deposited into. See [Self-custody](/concepts/self-custody/) for the read-only details.

## Verifying the prompt

Before approving, confirm the SIWE message in your wallet shows:

- **Domain:** `glacient.ai` (or the exact host you loaded).
- **Address:** the address you intended to sign in with.
- **Statement:** a plain sentence describing the sign-in, with no calls to `approve`, `transfer`, `permit`, or any contract method.

If any of those look wrong, cancel the prompt. Only the real Glacient app will present a SIWE message for its own domain.

## Hardware wallets

For addresses that hold meaningful value, use a hardware wallet for login. The SIWE flow works identically: your software wallet (MetaMask, Rabby) forwards the message to the device, and you confirm the signature on the hardware screen. Because the signature grants no fund-moving authority, this is a safe operation even for cold-storage addresses.

## Sessions

- Closing the login dialog or clicking **Log out** disconnects any active wallet sessions so a stale connection doesn't persist in the background.
- If your session expires, the next request will prompt you to sign in again with a fresh SIWE message.
- Glacient does not keep your wallet connected between visits by default — reconnecting requires a new signature.

## Linking with other methods

You can attach a wallet to an account that was originally created with Google or email, and vice versa, from your account settings. Once linked, any of the methods signs you into the same account. This is useful if you want the convenience of Google login while still using **My Investments**, which requires a connected wallet.

See [Sign in](/sign-in/) for the full list of authentication methods.

## Troubleshooting

**The wallet prompt never appears.** Make sure the wallet extension is unlocked and no other dapp has a pending request. Refresh and try again.

**Signing fails silently.** Some wallets swallow errors when the address is switched mid-flow. Cancel, re-select the address, and restart from **Login with Wallet**.

**Wrong address signed in.** Log out, switch the active address in your wallet, and log back in. Glacient uses whichever address signs the message, not whichever is "selected" in the wallet.

## Related

- [Sign in](/sign-in/) — all three authentication methods and how to link them.
- [Self-custody](/concepts/self-custody/) — what Glacient can and cannot do with a connected wallet.
- [Security model](/security/) — the full picture of what's stored and what's touched.
