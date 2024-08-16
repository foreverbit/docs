# Pod

A block is the container for mined or current transactions, while a pod is the container for passengers that will be executed in the future.

Within a pod, there can be multiple passengers, and all passengers within the same pod will be executed in the same block. The gas limit of the pod is the sum of all passengers' gas limits.

## Pod Contract


The Pod contract is a smart contract that manages Pods in Biternal. However, in Biternal, there is no deployed Pod contract. Instead, the Pod contract is coded within the core code, following the logic of the Pod contract.


```solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.6.0;

contract BlockPod {
    struct Passenger {
        address host;
        uint256 gasLimit;
        uint256 accFailed;
    }

    struct Pod {
        uint256 parent;
        uint256 gap;
        uint256 gasLimit;
        uint256 baseFee;
        uint256 currentGas;
        Passenger[] passengers;
    }

    // pod index => pod
    mapping (uint256 => Pod) public pods;

    // passenger => pod index
    mapping (address => uint256) public nextExecutions;

    // current pod that include passengers
    uint256 public currentPod;
}
```


The address of the Pod contract is `0x0000000000000000000000000000000000706f64`, encoded as the hexadecimal string `pod`.

## Pod RPC API

The Pod contract is not deployed as a separate contract, but rather coded within the core code. Therefore, there is no contract interface available for querying. However, we have added some RPC methods to allow querying of the pod information.


### eth_getExecution


To retrieve the execution information for a specific passenger, you can check the block number associated with the passenger. Here's what the block number indicates:

- If the block number is 0, it means the passenger is not scheduled for execution.
- If the block number is less than the current block, it means the passenger has already been executed in a previous block.
- If the block number is greater than the current block, it means the passenger is scheduled for execution in a future block.


#### Parameters

1. Address - The address of the passenger.
2. QUANTITY|TAG - integer block number, or the string "latest", "earliest", "pending", "safe", or "finalized", see the default block parameter

#### Returns

QUANTITY - integer of the pod index.


```bash
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getExecution","params":[{see above}],"id":1}'
// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x64"
}

```

### eth_getPod

To retrieve the information of a specific pod index, you can query it with or without the passenger result.

#### Parameters

1. Address - The address of the passenger.
2. Boolean - ignorePassengers, if true, it will not return passengers information.
3. QUANTITY|TAG - integer block number, or the string "latest", "earliest", "pending", "safe", or "finalized", see the default block parameter

#### Returns

Object - A pod object, or null when no pod found.

- parent: QUANTITY - integer of the parent pod index.
- gap: QUANTITY - integer of the gap between parent and current pod index.
- gasLimit: QUANTITY - integer of the gas limit of the pod.
- baseFee: QUANTITY - integer of the base fee of the pod.
- currentGas: QUANTITY - integer of the current gas of the pod.
- passengers: Array - An array of passengers.
    - host: DATA, 20 Bytes - The address of the passenger.
    - gasLimit: QUANTITY - integer of the gas limit of the passenger.
    - accFailed: QUANTITY - integer of the accumulated failed count of the passenger.


```bash
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getPod","params":[{see above}],"id":1}'
// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": {
    "parent": "0x60",
    "gap": "0x4",
    "gasLimit": "0x1C9C380",
    "baseFee": "0xa",
    "currentGas": "0x214820",
    "passengers": [
      {
        "host": "0xdAC17F958D2ee523a2206206994597C13D831ec7",
        "gasLimit": "0x214820",
        "accFailed": "0"
      }
    ]
  }
}

```

### eth_currentPod

Get the current pod index.

#### Returns

QUANTITY - integer of the current pod index.

```bash
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_currentPod","params":[],"id":1}'
// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x80"
}

```