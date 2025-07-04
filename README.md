## Task 2: ERC Token Creation(ArjunCoin)

## Description:
This Project is a part of Codtech Blockchain Internship.

## Requirements:
- 1.Ganache
- 2.Truffle
- 3.Node.js

## Deployment Steps:
- 1.Install truffle
  ``` 
   npm install -g truffle
   ```
- 2.Create project folders and initialize
 ``` 
   mkdir ArjunCoin
 cd ArjunCoin
truffle init
   ```
- 3.Install Ganache

- 4.Create a file in contracts/ArjunCoin.sol
 ``` 
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract ArjunCoin is ERC20 {
    constructor(uint256 initialSupply) ERC20("ArjunCoin", "ARJ") {
        _mint(msg.sender, initialSupply * 10 ** decimals());
    }
}
```
- 5.Create file in migrations/2_deploy_token.js
```
const ArjunCoin = artifacts.require("ArjunCoin");

module.exports = async function (deployer) {
  const initialSupply = 1_000_000; // 1 million ARJ
  await deployer.deploy(ArjunCoin, initialSupply);
};
 ```
6.Configure Ganache in truffle-config.js
```
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 7545, // Ganache GUI default
      network_id: "*"
    }
  },
  compilers: {
    solc: {
      version: "0.8.20",
      settings: {
        optimizer: {
          enabled: true,
          runs: 200
        },
        evmVersion: "london"
      }
    }
  }
};
 ```
7.Compile 
 ``` 
   truffle compile 
   ```
- 8.Make sure that Ganache is Running
- 9.Deploy
 ``` 
   truffle migrate
   ```
## Results
