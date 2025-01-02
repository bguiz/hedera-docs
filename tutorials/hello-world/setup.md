---
description: >-
  Hello World: Set up a Hedera development environment, including Testnet accounts. Do
  this before any of the other Hello World sequences.
---

# Setup

## Why you need to create and fund an account

Hedera is a distributed ledger technology (DLT). To interact with it, you will need to send transactions to the network, which will then process them and add them to the ledger if they are deemed to be valid. On most web services (web2), you need to authenticate using usernames and passwords to operate your account. On DLTs such as Hedera, it is similar, except that you will need to use cryptographic keys instead of passwords to operate your account. One key difference is that unlike web2, each interaction needs to be paid for using the native currency of the DLT, which is similar to micro-transactions. On Hedera, this currency is HBAR.

### What you will accomplish

* [ ] Initialise a Hedera development environment via interactive prompts
    * [ ] Configuration
    * [ ] Install dependencies
    * [ ] Generate new Testnet accounts
* [ ] Use the Hedera Faucet to create and fund a new account with Testnet HBAR

***

## Prerequisites

Before you begin, you should be familiar with the following:

* [x] [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

You can choose to complete this on Gitpod (a cloud development environment), or on localhost (your own computer). On Gitpod, the set up process is completely automated and takes about 10s for you to get started. On localhost, the set up process is manual, and takes about 20min for you to get started.

<details>

<summary>Set up pre-requisites for Gitpod <strong>⬇</strong></summary>

* [x] Github account
* [x] Browser

</details>

<details>

<summary>Set up pre-requisites for localhost <strong>⬇</strong></summary>

* [x] POSIX-compliant shell
  * For Linux & Mac: The shell that ships with the operating system will work. Either `bash` or `zsh` will work.
  * For Windows: The shells that ship with the operating system (`cmd.exe`, `powershell.exe`) _will not_ work.
    * Recommended: `git-bash` which ships with `git-for-windows`. [Install Git for Windows (Git for Windows)](https://gitforwindows.org/)
    * Recommended (alternative): Windows Subsystem for Linux. [Install WSL (Microsoft)](https://learn.microsoft.com/en-us/windows/wsl/install)
* [x] `git` installed
  * Minimum version: 2.37
  * Recommended: [Install Git (Github)](https://github.com/git-guides/install-git)
* [x] A code editor or IDE
  * Recommended: VS Code. [Install VS Code (Visual Studio)](https://code.visualstudio.com/docs/setup/setup-overview)
* [x] NodeJs + `npm` installed
  * Minimum version of NodeJs: 18
  * Minimum version of `npm`: 9.5
  * Recommended for Linux & Mac: [`nvm`](https://github.com/nvm-sh/nvm)
  * Recommended for Windows: [`nvm-windows`](https://github.com/coreybutler/nvm-windows)
* [x] Docker desktop
  * Minimum version: 4.34.0
  * Minimum Engine version: 27.2.0
  * Minimum Compose version: 2.29.2

</details>

***

## Get started on Gitpod

This is the **recommended approach** if you are developing on Hedera for the first time.

In your browser, be sure to be signed in to your [Github](https://github.com/login) account.

Next, open the following link in a new browser tab:

[![Gitpod open button](https://github.com/hedera-dev/hello-future-world-js/raw/main/img/gitpod-open-button.svg)](https://gitpod.io/?autostart=true&editor=code&workspaceClass=g1-standard#https://github.com/hedera-dev/hello-future-world-js)

> Note that the same link may also be found in the README of the repo:
> https://github.com/hedera-dev/hello-future-world-js

<details>

<summary>If this is your first time using Gitpod <strong>⬇</strong></summary>

* Gitpod will ask you to authenticate using your Github account
* Github will ask you to confirm that you allow Gitpod access to your account
* You will be redirected back to Gitpod, and can continue

</details>

Wait for up to 10 seconds, and you should see Visual Studio Code IDE load up **in** your browser tab.

In the terminal area, you will see 3 different shells, with the `main` shell currently visible. Here there should be a script with interactive prompts. When you see this, you are ready to move on to the next section.

***

## Get started on localhost

This approach is recommended if you are familiar with developing on Hedera, **and** have already met all of the prerequisites listed above.

```shell
# git clone via HTTPS
git clone https://github.com/hedera-dev/hello-future-world-js.git

# git clone via SSH
git clone git@github.com:hedera-dev/hello-future-world-js.git

# enter the directory of the tutorial repo just cloned
cd hello-future-world-js

# install dependencies
./util/03-get-dependencies.sh

# automated setup and configuration
./util/00-main.sh

```

The final command will trigger a script with interactive prompts. When you see this, you are ready to move on to the next section.

***

## Configuration

The script with interactive prompts will set up a `.env` file with configuration based on your inputs.

- Enter a BIP-39 seed phrase: Input nothing - this generates a new one for you
- Enter a number of accounts to generate from your BIP-39 seed phrase: Input nothing - this accepts the default value
- Enter your preferred JSON-RPC endpoint URL: Input nothing - this accepts the default value
- Enter your operator account private key: Input nothing - this uses the first account generated from your seed phrase
- Please ensure that you have funded (account address) - copy the EVM address (it starts with `0x`) and then visit [faucet.hedera.com](http://faucet.hedera.com) to fund it
- Switch back to the browser tab/window with Gitpod, and click in the terminal, then hit the “return” key
- Do you wish to overwrite the `.env` file with the above? - Input `y` for yes

In the file navigation, open the `.env` file and check its output.

***

🎉 _**Now you are ready to start using Hedera Testnet accounts!**_ 🎉

***

## Complete

Congratulations, you have completed the **setup** Hello World task! 🎉🎉🎉

You have learned how to:

* [ ] Initialise a Hedera development environment via interactive prompts
    * [ ] Configuration
    * [ ] Install dependencies
    * [ ] Generate new Testnet accounts
* [ ] Use the Hedera Faucet to create and fund a new account with Testnet HBAR

***

## Next Steps

Now that you are set up, you can interact with the Hedera network. Continue by following along with [the other Hello World tasks](./).

***

**Writer**: [Brendan](https://blog.bguiz.com/) **Editors**: [Abi](https://github.com/a-ridley), [Michiel](https://www.linkedin.com/in/michielmulders/), [Ryan](https://www.linkedin.com/in/ryaneh/), [Krystal](https://www.linkedin.com/in/theekrystallee/)
