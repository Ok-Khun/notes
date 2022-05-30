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

Payable:
```SOL
payable
msg.value // a global keyword to access value when someone is sending a token
require(msg.value > 1e18, "Not enough ETH."); // 1e18 = 1 * 10 ** 18 (1 ETH)
```

Address of sender:
```SOL
msg.sender
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

For loop:
```SOL
for(uint256 index=0; index < array.length; index++){
    // do something here
}
```

Create an empty array:
```SOL
arr = new dataType[](0);
// example:
// arr = new address[](0);
```

Transfer from contract
```SOL
payable(msg.sender).transfer(address(this).balance); // if error revert the transaction
payable(msg.sender).send(address(this).balance); // if error return a bool
// this is the recommended way
(bool callSuccess, bytes memory dataReturned) = payable(msg.sender).call{
    value: address(this).balance
}("");
```

Library:
```SOL
// SPDX-License-Identifier: MIT
pragma solidity 0.8.7;
library LibraryName {
    // cant have any state variable
    // all the functions need to be internet
}
```

Import Library
```SOL
import "./LibraryName.sol"

contract ContractName {
    using LibraryName for dataType;
    // code
```

Modifier:
```SOL
modifier onlyOwner {
    require(msg.sender == owner, "Sender is not owner");
    _;
}
function name() public onlyOwner{}
```

Const, Immutable
variables that can't be changed.
```sol
uint256 public constant VARNAME = 1.0; // lowers the gas fees
address public immutable i_owner = 0x...; // lowers the gas fees
```

Custome error
```sol
error NotOwner(); outside of contract
if(msg.sender != i_owner) {
    revert NotOwner(); // saves gas
}
```

Recieve & Fallback:
refer to the documentation
```sol
// triggered when it receives $ (can be 0) without invoking the contract's function
receive() external payable {
    // code here
}
// when it receives $ and data without invoking the contract's function
fallback() external payable {
    // code here
}
```

To interact with a contract, you need the contract address or abi (application binary interface). 
Contracts can hold token like a wallet address.

Chainlink & Oracle
Access data outside of blockchain or do external computation by using decentralized oracle networks.

Features

Chainlink documentation: [click here](https://docs.chain.link/)
Kovin testnet tokens request: [click here](https://faucets.chain.link/kovan)

Chainlink VRF (chainlik verifiable randomness function)
Doc : [click here](https://docs.chain.link/docs/get-a-random-number/)

Chainlink Keepers (decentralized event driven execution)
i.e every event do something
Doc : [click here](https://docs.chain.link/docs/chainlink-keepers/compatible-contracts/)

End-to-end reliabilty
make a http request etc.

Getting current eth usd price:
we need ABI, Address
Chainlink Github: [click here](https://github.com/smartcontractkit/chainlink)
Chainlink AggregatorV3Interface Github: [click here](https://github.com/smartcontractkit/chainlink/blob/develop/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol)

Using AggregatorV3Interface:
```SOL
// Rinkeby address
AggregatorV3Interface public priceFeed = AggregatorV3Interface(0x8A753747A1Fa494EC906cE90E9f37563A8AF630e);
```

Importing from Github:
```SOL
// same directory
// import"./AggregatorV3Interface.sol";

// GITHUB
import "@chainlink/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol";
```

Importing from NPM:
```
https://www.npmjs.com/package/@chainlink/contracts
npm i @chainlink/contracts
```

Safe Math Library:
Link : [click here](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeMath.sol)

