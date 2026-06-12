---
title: Sign in
eyebrow: Get started
summary: Three ways to authenticate, and how to link them to the same account.
permalink: /sign-in/
---

Glacient supports three authentication methods. Each is designed to leave you in control of your identity and your funds.

## Google

The fastest way to start. Click **Signup with Google** or **Login with Google**, pick the account, and you're in. There's no verification email and no separate password to manage.

Google authentication leverages Google's two-factor protection if you have it enabled on your account.

## Wallet (SIWE)

Connect any EVM wallet (MetaMask, Coinbase Wallet, Rainbow, Ledger via WalletConnect, and others).

1. Click **Login with Wallet**. Your extension prompts you to connect.
2. Glacient shows a **Confirm Signature** screen with the address you just connected.
3. Click **Finalize Signing**. Your wallet displays a Sign-In with Ethereum message.
4. Approve.

<div class="callout note">
<strong>What the signature does.</strong> SIWE proves you control the address. It is gasless, free, and grants no permission to move funds, approve tokens, or sign transactions. Glacient will never ask you to sign a transaction during login.
</div>

If you sign in with a wallet you have not used before, a profile is created automatically against that address. There's no separate signup flow.

## Email and password

Traditional account flow with email verification and password recovery.

- **Signup.** Enter your email, set a password, click the verification link in your inbox.
- **Login.** Enter the same credentials.
- **Forgot password.** Use the link on the login screen to send a recovery email.

Passwords are stored hashed; Glacient never sees them in plaintext.

## Linking methods

You can attach more than one method to the same Glacient account from your account settings. For example, sign up with Google, then later add a wallet so you can use the **My Investments** discovery flow.

## Session safety

Closing the login dialog or clicking **Log out** disconnects any active wallet sessions to prevent stale connections from persisting in the background. If your session expires, you'll be asked to sign in again on your next request.
