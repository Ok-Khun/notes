# [SOLIDITY](https://docs.soliditylang.org/en/v0.8.14/) NOTES
***
Resource: [Click here](https://www.youtube.com/watch?v=gyMwXuJrbJQ&t=9165s&ab_channel=freeCodeCamp.org)

Remix Online IDE: [Click here](https://remix.ethereum.org/)

Add license:
```
// SPDX-License-Identifier: MIT
```

Add version:
```SOL
pragma solidity 0.8.7;
```

Version:

`0.8.7` is one of the stable versions.
`^0.8.7` any version above `0.8.7`
`>=0.8.7 < 0.9.0` any bersion in between.

Define a contract:
```SOL
contract ContractName {

}
```

Data types:
```SOL
bool // true or false
uint // 8 - 256
int // 8 - 256
address
bytes   // bytes32 (max size)
string // "string
```

Visibility:
```SOL
private // only visible from the current contract 
public
external // someone outside can call the function
internal
```

Payable
```SOL
payable
msg.value // a global keyword to access value when someone is sending a token
require(msg.value > 1e18, "Not enough ETH."); // 1e18 = 1 * 10 ** 18 (1 ETH)
```

Variable:

`DataType Visibility VarName = Value;`
note: `Visibility` is optional.


Functions:
```SOL
function name(DataType _arg) public {
 // code here
}
function name(DataType _arg) public view returns(DataType) {
 // code here
}
// if the argument is a string
function name(string memory name) ...
```

```SOL
view // only read state doesn't require to pay for gas fees and you can't update the state
pure // you can't update the state and view the state
```

Every single contract has an address when you deploy it on a block chain.

Struct:
```SOL
struct People {
    string name;
    uint256 favoriteNumber;
}

People public person = People ({
    name : "John",
    favoriteNumber : 1
});
```
Array:
```SOL
People[] public people;
uint256[] public favoriteNumberList;
```
Array methods:
```SOL
People[] public people;
people.push(People(_name, _favoriteNumber));
```

There are six places you can store data:
```SOL
stack
memory // variable only going to exists temporarily (can be modified)
storage // exists outside of the function
calldata // variable only going to exists temporarily (can't be modified)
code
logs
```

Map:
```SOL
mapping(string => uint256) public nameToNumbers;
nameToNumbers[_name] = _number;
```

Codes are compiled down to EVM (Ethereum Virtual Machine). Some EVM compatible blockchains are Avalanche, Fantom, Polygon meaning we can write our solidity code and deploy it to them.

Create a contract from a contract:
```SOL
contract ContractFactory {
    ContractName public contract1;
    function createContract() public {
        contract1 = new ContractName();
    }
}
```

Import a contract:
```SOL
import "./SimpleStorage.sol";
```
Inheritance & Override:
```SOL
contract NewContract is OldContract{
    // Code here
    // you can override OldContract with 
    // virtual override
    // i.e overide for newcontract
    // i.e virutal for oldcontract
}
```

To interact with a contract, you need the contract address or abi (application binary interface). 
Contracts can hold token like a wallet address.

Chainlink & Oracle
Access data outside of blockchain or do external computation by using decentralized oracle networks.

Chainlink documentation: [click here](https://docs.chain.link/)
Kovin testnet tokens request: [click here](https://faucets.chain.link/kovan)

