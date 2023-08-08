---
description: >-
  Hedera Smart Contract Service workshop.
  Smart contracts are a means to enable custom logic and processing in a DLT.
  Developers can harness their power to build their own decentralised applications (DApps).
  Learn how to get started with the Hedera Smart Contract Service (HSCS) in this workshop. 
---

# Hedera Smart Contracts Workshop

Smart contracts are a means to enable custom logic and processing in a DLT. Developers can harness their power to build their own decentralised applications (DApps). Learn how to get started with the Hedera Smart Contract Service (HSCS) in this workshop. 

## What we will cover

- Syntax of Solidity, a programming language used to write smart contracts
- Using the Solidity compiler
- Using Hedera SDK JS to deploy smart contracts onto Hedera networks
- Using Hedera SDK JS to interact with smart contracts on Hedera networks
- Using Hardhat + EthersJs to deploy smart contracts onto Hedera networks
- Using Hardhat + EthersJs to interact with smart contracts on Hedera networks
- Where to go from here

## Prerequisites

Prior knowledge:

- Javascript syntax
- Hedera network core concepts

System setup:

- `git` installed
	- Minimum version: 2.37
	- [Install Git (Github)](https://github.com/git-guides/install-git)
- NodeJs + `npm` installed
	- Minimum version of NodeJs: 18
	- Recommended for Linux & Mac: [`nvm`](https://github.com/nvm-sh/nvm)
	- Recommended for Windows: [`nvm-windows`](https://github.com/coreybutler/nvm-windows)
- POSIX-compliant shell
	- For Linux & Mac: The shell that ships with the operating system will work. Either `bash` or `zsh` will work.
	- For Windows: The shell that ships with the operating system (`cmd.exe`, `powershell.exe`) will *not* work. Recommended alternatives: WSL/2, or git-bash which ships with git-for-windows.
- Internet connection

Optional system setup:

- `jq`
	- For Linux: Use OS package manager
	- For Mac: `brew install jq`
	- For Windows: Install `.exe` file manually: [JQ releases (Github)](https://github.com/jqlang/jq/releases)

## Software libraries and developer tools

Before we begin coding,
let's take a look at the various software libraries and developer tools that
you will need to be familiar with when working with smart contracts on HSCS.

[Hedera SDK JS](https://github.com/hashgraph/hedera-sdk-js)
is a software library that contains functions designed to interact the all
of the services available on the Hedera network:
HCS, HTS, HFS, and HSCS.
That includes smart contracts.

Both [EthersJs](https://docs.ethers.org/v5/)
and [Web3Js](https://web3js.readthedocs.io/en/v1.10.0/)
are software libraries that contain functions designed to interact with
the Ethereum network, and any other EVM-compatible networks.
This means that you can use them to interact with HSCS as well
(but not with HCS, HTS, or HFS).


We've already seen some Solidity syntax,
but we cannot just take the Solidity code and ask HSCS,
or any other EVM implementation for that matter, to run it.
Instead we need [`solc`](https://docs.soliditylang.org/en/v0.8.19/),
the Solidity compiler, to compile it into EVM bytecode,
which can then be executed by any EVM implementation,
including the one in HSCS.

Worth pointing out that Solidity is not the only game in town.
You can actually write smart contracts in any language,
as long as it compiled to EVM bytecode.
The most popular alternative smart contract programming language is
[Vyper](https://docs.vyperlang.org/en/stable/).

In this workshop we will be using **Solidity**.

[Truffle Suite](https://trufflesuite.com/),
[Hardhat](https://hardhat.org/),
and [Foundry](https://getfoundry.sh/)
are developer frameworks that are designed to make it easier to
work with smart contract development workflows
by providing various utilities, scripts, structure, and documentation
that are useful during development.

In this workshop we will be using **Hardhat**.
