<!-- prettier-ignore-start -->
<!-- omit in toc -->
# Circle's Stablecoin Smart Contracts on EVM-compatible blockchains
<!-- prettier-ignore-end -->

This repository contains the smart contracts used by
[Circle's](https://www.circle.com/) stablecoins on EVM-compatible blockchains.
All contracts are written in [Solidity](https://soliditylang.org/) and managed
by the [Hardhat](https://hardhat.org/) framework.

<!-- prettier-ignore-start -->
<!-- omit in toc -->
## Table of contents
<!-- prettier-ignore-end -->

- [Setup](#setup)
  - [Development Environment](#development-environment)
  - [IDE](#ide)
- [Development](#development)
  - [TypeScript type definition files for the contracts](#typescript-type-definition-files-for-the-contracts)
  - [Linting and Formatting](#linting-and-formatting)
  - [Testing](#testing)
- [Deployment](#deployment)
- [Contracts](#contracts)
- [FiatToken features](#fiattoken-features)
  - [ERC20 compatible](#erc20-compatible)
  - [Pausable](#pausable)
  - [Upgradable](#upgradable)
  - [Blacklist](#blacklist)
  - [Minting/Burning](#mintingburning)
  - [Ownable](#ownable)
- [Additional Documentations](#additional-documentations)

## Deployment

```
carter@laptop:~/Documents/frax/fraxtal-usdc$ yarn forge:broadcast scripts/deploy/deploy-fiat-token.s.sol --rpc-url mainnet
yarn run v1.22.19
$ yarn forge:simulate --broadcast scripts/deploy/deploy-fiat-token.s.sol --rpc-url mainnet
$ forge script -vv --gas-estimate-multiplier $(dotenv -p GAS_MULTIPLIER) --broadcast scripts/deploy/deploy-fiat-token.s.sol --rpc-url mainnet
[⠒] Compiling...
No files changed, compilation skipped
Script ran successfully.

== Return ==
0: contract FiatTokenV2_2 0xF92F9b88238cB890f96366D6Fe008A2ec587D637
1: contract MasterMinter 0xC880F15ad28222bB77BBEeAea077ce8810B09CB1
2: contract FiatTokenProxy 0x6c00BA632b3C5808910B6BB4E6A772f3FC1960c8

== Logs ==
  TOKEN_NAME: 'USDC'
  TOKEN_SYMBOL: 'USDC'
  TOKEN_CURRENCY: 'USD'
  TOKEN_DECIMALS: '6'
  FIAT_TOKEN_IMPLEMENTATION_ADDRESS: '0x0000000000000000000000000000000000000000'
  PROXY_ADMIN_ADDRESS: '0xC4EB45d80DC1F079045E75D5d55de8eD1c1090E6'
  MASTER_MINTER_OWNER_ADDRESS: '0xC4EB45d80DC1F079045E75D5d55de8eD1c1090E6'
  OWNER_ADDRESS: '0xC4EB45d80DC1F079045E75D5d55de8eD1c1090E6'
  PAUSER_ADDRESS: '0xC4EB45d80DC1F079045E75D5d55de8eD1c1090E6'
  BLACKLISTER_ADDRESS: '0xC4EB45d80DC1F079045E75D5d55de8eD1c1090E6'

## Setting up 1 EVM.

==========================

Chain 252

Estimated gas price: 3.000002054 gwei

Estimated total gas used for script: 8865109

Estimated amount required: 0.026595345208933886 ETH

==========================
##
Sending transactions [0 - 13].
⠤ [00:00:00] [#################################################################] 14/14 txes (0.0s)##
Waiting for receipts.
⠠ [00:00:06] [#############################################################] 14/14 receipts (0.0s)
##### fraxtal
✅  [Success]Hash: 0x0adda021b424aafe9f6a4fefcb6a981755ffd4b887016d86f772df437cb8fa63
Contract Address: 0x4723a757955a9B5F1BE2dB07672d14dEB834c403
Block: 4580622
Paid: 0.001282101433777505 ETH (427367 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0xbfb5a8a2f84c6ed26200ba0f5c22f55dd33653cc43c53ff0a74541282c0f69d3
Contract Address: 0xF92F9b88238cB890f96366D6Fe008A2ec587D637
Block: 4580622
Paid: 0.01533839918948997 ETH (5112798 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0xc542fd759b5c0938ac2ef9b80bc1cdbef72e6551138c9ad9afaf0934c5cfdfd9
Block: 4580622
Paid: 0.000321405108742025 ETH (107135 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0xf80c652a263a2a112b2de3b6ed4d8db037ce82354e937af18f254500d1541737
Block: 4580622
Paid: 0.00027439209283596 ETH (91464 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x24fda3b6a15f35708dd1764c1d83376b295c03a2f409ce35f3dc9975e011df07
Block: 4580622
Paid: 0.000147627049947135 ETH (49209 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0xee36f282517581dacfeca94c86e35ac312ec4349bfdc97e7286a9065a8be0877
Block: 4580622
Paid: 0.000104445035337225 ETH (34815 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x9f4464e2b680b3ab1916e4813e2ebcd81a250dddb9086af138e8c6ee79d3bd47
Contract Address: 0x6c00BA632b3C5808910B6BB4E6A772f3FC1960c8
Block: 4580622
Paid: 0.001477449499870245 ETH (492483 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x6d69cf1a848f74e2a9a219144188e2e1126233bc50ff3931f172cedc8b798dea
Contract Address: 0xC880F15ad28222bB77BBEeAea077ce8810B09CB1
Block: 4580622
Paid: 0.003737401264487 ETH (1245800 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x3f8c2b4cd82f35041ba84d279fdaf70074a12d8a59356568f892c39c34dced27
Block: 4580622
Paid: 0.000085035028770175 ETH (28345 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x5a69b0c193fcc16a2d5bce459402f2f38b3db96d2ab1f92877299d2cc5871132
Block: 4580622
Paid: 0.00008475602867578 ETH (28252 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x9e59236af73cd63205328cac176d269d2693550be0f2a29afe09e70e618f1375
Block: 4580622
Paid: 0.00063309021419545 ETH (211030 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x3a56f69d9b791cec263c3c07d6cd759a5d91d5693b704bb804f6ea7f9209000b
Block: 4580622
Paid: 0.00024319208227996 ETH (81064 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x41b73c4ef6aa892777488a73f3f3687fafed15ca179e73d9dfbcf7ffb9ff920a
Block: 4580622
Paid: 0.000169797057447985 ETH (56599 gas * 3.000001015 gwei)


##### fraxtal
✅  [Success]Hash: 0x6db844771ed81b4ce746dbc772c3d0f2a86accb95c1a3d9d0666e71f53906e4b
Block: 4580622
Paid: 0.000132885044959425 ETH (44295 gas * 3.000001015 gwei)



==========================

ONCHAIN EXECUTION COMPLETE & SUCCESSFUL.
Total Paid: 0.02403197613081584 ETH (8010656 gas * avg 3.000001015 gwei)

```

## Setup

### Development Environment

Requirements:

- Node 16.14.0
- Yarn 1.22.19
- [Foundry@f625d0f](https://github.com/foundry-rs/foundry/releases/tag/nightly-f625d0fa7c51e65b4bf1e8f7931cd1c6e2e285e9)

```sh
$ git clone git@github.com:circlefin/stablecoin-evm.git
$ cd stablecoin-evm
$ nvm use
$ npm i -g yarn@1.22.19 # Install yarn if you don't already have it
$ yarn install          # Install npm packages and other dependencies listed in setup.sh
```

### IDE

We recommend using VSCode for the project here with these
[extensions](./.vscode/extensions.json) installed.

## Development

### TypeScript type definition files for the contracts

Types are automatically generated as a part of contract compilation:

```sh
$ yarn compile
```

To generate typing without re-compiling, run

```sh
$ yarn hardhat typechain
```

### Linting and Formatting

To check code for problems:

```sh
$ yarn static-check   # Runs a static check on the repo.
```

or run the checks individually:

```sh
$ yarn typecheck      # Type-check TypeScript code
$ yarn lint           # Check JavaScript and TypeScript code
$ yarn lint --fix     # Fix problems where possible
$ yarn solhint        # Check Solidity code
```

To auto-format code:

```sh
$ yarn fmt
```

### Testing

Run all tests:

```sh
$ yarn test
```

To run tests in a specific file, run:

```sh
$ yarn test [path/to/file]
```

To run tests and generate test coverage, run:

```sh
$ yarn coverage
```

To check the size of contracts in the repo, run the following command.

```sh
$ yarn contract-size # Ignores tests
```

## Deployment

1. Create a copy of the file `.env.example`, and name it `.env`. Fill in
   appropriate values in the `.env` file. This file must not be checked into the
   repository.

```sh
cp .env.example .env
```

2. Create a `blacklist.remote.json` file and populate it with a list of
   addresses to be blacklisted. This file must not be checked into the
   repository.

```sh
echo "[]" > blacklist.remote.json
```

3. Simulate a deployment by running the following command

```sh
yarn forge:simulate scripts/deploy/deploy-fiat-token.s.sol --rpc-url <testnet OR mainnet>
```

4. Validate that all transactions to be broadcasted are filled in with the
   correct values
5. Deploy the contracts by running the following command

```sh
yarn forge:broadcast scripts/deploy/deploy-fiat-token.s.sol --rpc-url <testnet OR mainnet>
```

6. Verify the contracts on an Etherscan flavored block explorer by running the
   following command. Ensure that `ETHERSCAN_KEY` is set in the `.env` file.

```sh
yarn forge:verify scripts/deploy/deploy-fiat-token.s.sol --rpc-url <testnet OR mainnet>
```

## Contracts

The FiatToken contracts adheres to OpenZeppelin's
[Proxy Upgrade Pattern](https://docs.openzeppelin.com/upgrades-plugins/1.x/proxies)
([permalink](https://github.com/OpenZeppelin/openzeppelin-upgrades/blob/65cf285bd36af24570186ca6409341540c67238a/docs/modules/ROOT/pages/proxies.adoc#L1)).
There are 2 main contracts - an implementation contract
([`FiatTokenV2_2.sol`](./contracts/v2/FiatTokenV2_2.sol)) that contains the main
logic for FiatToken's functionalities, and a proxy contract
([`FiatTokenProxy.sol`](./contracts/v1/FiatTokenProxy.sol)) that redirects
function calls to the implementation contract. This allows upgrading FiatToken's
functionalities, as a new implementation contact can be deployed and the Proxy
can be updated to point to it.

## FiatToken features

The FiatToken offers a number of capabilities, which briefly are described
below. There are more [detailed design docs](./doc/tokendesign.md) in the `doc`
directory.

### ERC20 compatible

The FiatToken implements the ERC20 interface.

### Pausable

The entire contract can be frozen, in case a serious bug is found or there is a
serious key compromise. No transfers can take place while the contract is
paused. Access to the pause functionality is controlled by the `pauser` address.

### Upgradable

A new implementation contract can be deployed, and the proxy contract will
forward calls to the new contract. Access to the upgrade functionality is
guarded by a `proxyOwner` address. Only the `proxyOwner` address can change the
`proxyOwner` address.

### Blacklist

The contract can blacklist certain addresses which will prevent those addresses
from transferring or receiving tokens. Access to the blacklist functionality is
controlled by the `blacklister` address.

### Minting/Burning

Tokens can be minted or burned on demand. The contract supports having multiple
minters simultaneously. There is a `masterMinter` address which controls the
list of minters and how much each is allowed to mint. The mint allowance is
similar to the ERC20 allowance - as each minter mints new tokens their allowance
decreases. When it gets too low they will need the allowance increased again by
the `masterMinter`.

### Ownable

The contract has an Owner, who can change the `owner`, `pauser`, `blacklister`,
or `masterMinter` addresses. The `owner` can not change the `proxyOwner`
address.

## Additional Documentations

- [FiatToken design](./doc/tokendesign.md)
- [MasterMinter design](./doc/masterminter.md)
- [Bridged USDC Standard](./doc/bridged_USDC_standard.md)
- [Deployment process](./doc/deployment.md)
- [Preparing an upgrade](./doc/upgrade.md)
- [Upgrading from v2.1 to v2.2](./doc/v2.2_upgrade.md)
- [Celo FiatToken extension](./doc/celo.md)
