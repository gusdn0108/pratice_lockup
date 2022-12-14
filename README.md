Abyss Finance Lockup
=========

Abyss Lockup service allows you to lock any ERC20 and BEP20 token with strict period of withdrawal time:

  - All ERC20 and BEP20 tokens are supported (LP tokens as well).
  - All forms of rebase are supported.
  - 1, 3, 7, 14, 21, 28, 90, 180, and 365 days unlock waiting period available.
  - Service is Free of charge when you hold the Abyss Tokens at all steps of 1, 3, 7, 14, 21, and 28 days unlock waiting period and without any requirements for a 90, 180, and 365 days unlock waiting period.

Contracts
=========

Below is a list of contracts we use for this service:

<dl>
  <dt>SafeERC20, Ownable, Address, ReentrancyGuard</dt>
  <dd>Openzepellin smart contracts. The first one allows to transfer and to approve ERC20 or BEP20 tokens safely. The second one allows for managing ownership. The third one allows to check if the address is a smart contract or not. The last one protects from re-entrance attacks.</dd>
</dl>

<dl>
  <dt>AbyssLockup</dt>
  <dd>A smart contract that stores tokens requested for withdrawal, as well as through which tokens are transferred from/to user and between contracts.</dd>
</dl>

<dl>
  <dt>AbyssSafeBase</dt>
  <dd>The main smart contract that contains all functions of Safe contracts.</dd>
</dl>

<dl>
  <dt>AbyssSafe1</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 86400 seconds (1 day) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe3</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 259200 seconds (3 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe7</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 604800 seconds (7 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe14</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 1209600 seconds (14 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe21</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 1814400 seconds (21 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe28</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 2419200 seconds (28 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe90</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 7776000 seconds (90 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe180</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 15552000 seconds (180 days) lockup delay setting should be applied on deployment.</dd>
</dl>

<dl>
  <dt>AbyssSafe365</dt>
  <dd>Smart contract responsible for deposits and withdrawal of tokens. 31536000 seconds (365 days) lockup delay setting should be applied on deployment.</dd>
</dl>

Installation
------------

To run lockup service, install [Homebrew](https://brew.sh), [Node.js](https://nodejs.org), [Truffle](https://www.trufflesuite.com), [OpenZeppelin](https://openzeppelin.com) and pull the repository from `GitHub`:

    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    brew install node
    npm install -g truffle
    npm install -g @openzeppelin/contracts
    mkdir projects
    cd projects
    git clone https://github.com/abyssfinance/abyss-lockup
    cd abyss-lockup
    truffle init


Setup your `truffle` environment, write migrations:

    truffle develop
    migrate --reset

Deployment (Ethereum, Binance Smart Chain)
------------

Smart contracts should be deployed in such order:

1. `AbyssLockup.sol` _(100)_
2. `AbyssSafe1.sol`_(Token_address, AbyssLockup_address, 1000000000000000000000)_
2. `AbyssSafe3.sol`_(Token_address, AbyssLockup_address, 1000000000000000000000)_
3. `AbyssSafe7.sol`_(Token_address, AbyssLockup_address, 1000000000000000000000)_
3. `AbyssSafe14.sol`_(Token_address, AbyssLockup_address, 100000000000000000000)_
3. `AbyssSafe21.sol`_(Token_address, AbyssLockup_address, 100000000000000000000)_
3. `AbyssSafe28.sol`_(Token_address, AbyssLockup_address, 100000000000000000000)_
4. `AbyssSafe90.sol`_(Token_address, AbyssLockup_address, 0)_
4. `AbyssSafe180.sol`_(Token_address, AbyssLockup_address, 0)_
4. `AbyssSafe365.sol`_(Token_address, AbyssLockup_address, 0)_
5. Call _initialize(AbyssSafe1_address, AbyssSafe3_address, AbyssSafe7_address, AbyssSafe14_address, AbyssSafe21_address, AbyssSafe28_address, AbyssSafe90_address, AbyssSafe180_address, AbyssSafe365_address)_ function from the `owner` on `AbyssLockup` contract.

How to Use
------------

1. Choose the ERC20 or BEP20 token that you want to lock.
2. Approve `AbyssLockup` contract on that token's smart contract for _115792089237316195423570985008687907853269984665640564039457584007913129639935_ amount from your wallet.
3. Use _deposit()_ function on any `AbyssSafe` smart contract to deposit tokens.
4. Use _request()_ function on any `AbyssSafe` smart contract to request a withdrawal.
5. Use _cancel()_ function on any `AbyssSafe` smart contract to cancel the withdrawal request.
6. Use _withdraw()_ function on any `AbyssSafe` smart contract to withdraw tokens when lockup period passed after you had made a withdrawal request.

Deployed Smart Contracts (Ethereum, Binance Smart Chain):
------------

`AbyssLockup`: <b>0xFEbfF48c603B8d81962785045b864C6b44B67DE7</b><br>
`Safe1`:       <b>0xb2fB84001B6Aba3EffA0dFcC87836F8642502ABB</b><br>
`Safe3`:       <b>0x010c6e73DF06319A523bA81b9Bf238E64AD70204</b><br>
`Safe7`:       <b>0xDD87f30E07A142c623d60677491F2Fd2E7203A1a</b><br>
`Safe14`:      <b>0x2fc16f2Bfc8B71b89b7F53CfBc38573d3a654D77</b><br>
`Safe21`:      <b>0xB966a59F71636EfA49DE961530bE3e26c94bC762</b><br>
`Safe28`:      <b>0x4dC0b5221222E7daC0Df1eC133434b21eFa77F68</b><br>
`Safe90`:      <b>0x7d7518F9D466Ef9AEeE334332baDEB44eaFF7660</b><br>
`Safe180`:     <b>0xf753E42806037C556020F7c4B61D2db09F4d0Bb3</b><br>
`Safe365`:     <b>0xece6b6B14C054DE59A5C4dAE8C17AdF073287968</b>

License
=========

MIT

Discussion
----------

For any concerns or suggestions visit us on [Telegram](https://t.me/abyssfinance) to discuss.

For security concerns, please email [security@abyss.finance](mailto:security@abyss.finance).

_?? Copyright 2020-2021, Abyss Finance_
