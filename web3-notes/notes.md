# [SOLIDITY](https://docs.soliditylang.org/en/v0.8.14/) NOTES

Remix Online IDE: [Click here](https://remix.ethereum.org/)

Add license
```
// SPDX-License-Identifier: MIT
```

Add version 
```SOL
pragma solidity 0.8.7;
```

Version

`0.8.7` is one of the stable versions.
`^0.8.7` any version above `0.8.7`
`>=0.8.7 < 0.9.0` any bersion in between.

Define a contract
```SOL
contract ContractName {

}
```

Data types
```SOL
bool // true or false
uint // 8 - 256
int // 8 - 256
address
bytes   // bytes32 (max size)
string // "string
```

Visibility
```SOL
private // only visible from the current contract 
public
external // someone outside can call the function
internal
```

Variable

`DataType Visibility VarName = Value;`
note: `Visibility` is optional.


Functions
```SOL
function name(DataType _arg) public {
 // code here
}
function name(DataType _arg) public view returns(DataType) {
 // code here
}
```

```SOL
view // only read state doesn't require to pay for gas fees and you can't update the state
pure // you can't update the state and view the state
```

Every single contract has an address when you deploy it on a block chain.