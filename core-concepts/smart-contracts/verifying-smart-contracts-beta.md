# Verifying Smart Contracts (Beta)

Smart contract verification is the process of verifying that the smart contract bytecode uploaded to the network matches the expected smart contract source files. Verification is _not_ required for contracts that are deployed on the Hedera but it is best practice and essential to maintaining the contract's security and integrity by identifying vulnerabilities that could be exploited, as smart contracts are immutable once deployed. It also enables transparency and builds trust within the user community by proving that the deployed bytecode matches the contract's original source code.&#x20;

To initiate verification, you can use a community-hosted Hedera Mirror Node Explorer, like [HashScan](https://hashscan.io/) ([Arkhia](https://explorer.arkhia.io/) and [Dragon Glass](https://app.dragonglass.me/) do not currently support this feature), that integrates with [Sourcify](../../support-and-community/glossary.md#sourcify): A Solidity source code and metadata verification tool. Once you upload your files to the verification tool, Sourcify recompiles the submitted source code and metadata files to check them against the deployed bytecode. If a match is found, the contract's verification status is updated to either a [_<mark style="color:green;">Full (Perfect) Match</mark>_](https://docs.sourcify.dev/docs/full-vs-partial-match/#full-perfect-matches) or a [_<mark style="color:green;">Partial</mark>_ ](https://docs.sourcify.dev/docs/full-vs-partial-match/#partial-matches)_<mark style="color:green;">Match.</mark>_

The verification status is then publicly available across all community-hosted Hedera Mirror Node Explorers. To learn what differentiates a _Full (Perfect) Match_ from a _Partial Match_, check out the Sourcify documentation [here](https://docs.sourcify.dev/docs/full-vs-partial-match/).

{% hint style="info" %}
**Note**: This is an initial beta release, and both the HashScan user interface and API functionalities are scheduled for enhancements in upcoming updates.
{% endhint %}

For verification, you will need the following items:

**➡** [**Smart Contract Source Code**](verifying-smart-contracts-beta.md#smart-contract-source-code)

**➡** [**The Metadata File**](verifying-smart-contracts-beta.md#the-metadata-file)

**➡** [**Deployed Smart Contract Address**](verifying-smart-contracts-beta.md#deployed-smart-contract-address)

***

## Smart Contract Source Code

This is the actual code for your smart contract written in Solidity. The source code includes all the contract's functions, variables, and logic. It's crucial for the verification process, where the deployed bytecode is compared to the compiled bytecode of this source code.

#### Example:

A simple `HelloWorld` Solidity smart contract:

```solidity
pragma solidity ^0.8.17;

contract HelloWorld {
   // the contract's owner, set in the constructor
   address owner;
   
   // the message we're storing, set in the constructor
   string message;
 
   constructor(string memory message_) {
      // set the owner of the contract for 'kill()'
      owner = msg.sender;
      message = message_; 
   }
   
   function set_message(string memory message_) public {
        // only allow the owner to update the message
        if (msg.sender != owner) return;
        message = message_;
    }

    // return a string
    function get_message() public view returns (string memory) {
        return message;
    }
}
```

***

## The Metadata File

When you compile a Solidity smart contract, it generates a JSON metadata file. This file contains settings used when the smart contract was originally compiled. These settings can include the compiler version, optimization details, and more. The metadata file is crucial for ensuring that the bytecode generated during verification matches the deployed bytecode. See Sourcify's Metadata documentation [here](https://docs.sourcify.dev/docs/metadata/#metadata). You can create the metadata file using:&#x20;

<details>

<summary>Hardhat </summary>

To create the `.json` metadata file with Hardhat, compile the contract using the `npx hardhat compile` command. The compiled artifacts will be saved in the `artifacts/` directory and the `.json` metadata file will be under `artifacts/build-info`. See Sourcify Hardhat metadata [here](https://docs.sourcify.dev/docs/metadata/#hardhat).&#x20;

</details>

<details>

<summary>Remix IDE</summary>

To create a metadata file in Remix, compile your smart contract and the compiled artifacts will be saved in the `artifacts/` directory and the `.json` metadata file will be under `artifacts/build-info`. Alternatively, you can copy and paste it from the Solidity compiler tab. Please see the image below.

![](<../../.gitbook/assets/remix metadata.png>)

**Note:** Taking the bytecode and metadata from Remix and then deploying that on Hedera results in a _**full (perfect) match**_. Taking the bytecode and metadata from Remix _after_ deploying the contract on Hedera results in a _**partial match**_.

</details>

<details>

<summary><strong>Solidity compiler</strong></summary>

You can pass the `--metadata` flag to the Solidity command line compiler to get the metadata output printed.&#x20;

```
solc --metadata HelloWorld.sol
```

Write the metadata into a file with

```
solc --metadata HelloWorld.sol > metadata.json
```

</details>

#### Example:

An example metadata file for the `HelloWorld` smart contract:

```json
{
  "compiler": "0.8.17",
  "language": "Solidity",
  "abi": [
    {
      "inputs": [
        {
          "internalType": "string",
          "name": "message_",
          "type": "string"
        }
      ],
      "stateMutability": "nonpayable",
      "type": "constructor"
    },
    {
      "inputs": [],
      "name": "get_message",
      "outputs": [
        {
          "internalType": "string",
          "name": "",
          "type": "string"
        }
      ],
      "stateMutability": "view",
      "type": "function"
    },
    {
      "inputs": [
        {
          "internalType": "string",
          "name": "message_",
          "type": "string"
        }
      ],
      "name": "set_message",
      "outputs": [],
      "stateMutability": "nonpayable",
      "type": "function"
    }
  ]
}
```

***

## Deployed Smart Contract Address

Even though Hedera uses the `0.0.XXXXXXX` account ID format, it accommodates Ethereum's address format for EVM compatibility. Once your smart contract is deployed on Hedera's network, you'll receive an address like the one below. This serves as your deployed smart contract address.

#### Example:

An example deployed EVM smart contract address:

```
0x403925982ef5a6461daba0a103bd6be20b9c4216
```

{% hint style="info" %}
_**Note**: The `0.0.XXXXXXX` smart contract address format can not be used in the verification process._
{% endhint %}

***

## Verify Your Smart Contract

Learn how to verify your smart contract:

{% content-ref url="../../tutorials/smart-contracts/how-to-verify-a-smart-contract-on-hashscan-beta.md" %}
[how-to-verify-a-smart-contract-on-hashscan-beta.md](../../tutorials/smart-contracts/how-to-verify-a-smart-contract-on-hashscan-beta.md)
{% endcontent-ref %}

#### Different Instances of Sourcify: Hedera's Custom Approach

It's important to note that multiple instances of Sourcify do exist, tailored to the specific needs of different networks. Hedera runs an independent instance of Sourcify, distinct from the public-facing Sourcify.dev instances like Etherscan and other Etherscan clones.

Running an independent instance of Sourcify allows Hedera to have more control over the verification process, tailoring it to the custom needs of the Hedera ecosystem. For instance, after a testnet reset, Hedera requires the ability to reset testnet smart contract verifications - something Sourcify.dev cannot accommodate.&#x20;

> _**Verified Smart Contracts Testnet Reset:** When the Hedera Testnet is reset, the contract must be redeployed and verified. The contract will receive a new contract EVM address and contract ID. The smart contract will need to be verified using the new addresses._

An essential detail to remember is that smart contracts verified on Hedera's Sourcify instance won't automatically appear as verified on Sourcify.dev or vice versa. Users interested in having their smart contract recognized across multiple platforms should consider verifying on both instances.

***

## Additional Resources

{% embed url="https://docs.sourcify.dev/docs/full-vs-partial-match/" %}

{% embed url="https://verify.hashscan.io/" %}
[verify.hashscan.io](https://verify.hashscan.io/)
{% endembed %}

{% embed url="https://hashscan.io" %}

{% embed url="https://hardhat.org/hardhat-runner/docs/guides/compile-contracts" %}

{% embed url="https://docs.soliditylang.org/" %}