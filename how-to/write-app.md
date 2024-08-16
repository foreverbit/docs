# How to write Biternal application

We are based on Ethereum, so we can use Ethereum tools to develop Biternal applications. For Biternal appliciation, developer should add one `fallback` function for scheduling future execution and the smart contract should be `payable`, Which is not required in Ethereum.

After the Biternal smart contract is deployed, the smart contract should be paied with native `BIT` token for execution fee. In the paied transaction, the smart contract will be scheduled for future execution, and after execution, the smart contract will be executed automatically.

For example, we can write a simple contract like this:

```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.6.0;

contract TestPod {
    uint256 public count;

    constructor() {
        count = 1;
    }

    // fallback function
    fallback() external payable {
        count += 1;
    }
}
```

Or with receive function:

```solidity
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.6.0;

contract TestPod {
    uint256 public count;

    constructor() {
        count = 1;
    }

    // receive function
    receive() external payable {}

    // fallback function
    fallback() external {
        count += 1;
    }
}
```