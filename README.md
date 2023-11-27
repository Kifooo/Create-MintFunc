# Create and Mint Contract

## Description
This Solidity smart contract, entitled "Create and Mint Function," includes basic token minting and burning functionality. It has features like public variables, a mapping structure, and token minting and burning events.

## Getting Started

### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.


Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

import "@openzeppelin/contracts@4.9.0/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@4.9.0/access/Ownable.sol";

contract myToken is ERC20, Ownable {
    constructor(uint256 initialSupply) ERC20("Erc20", "ETH") {
        _mint(msg.sender, initialSupply);
    }

    function mint(uint256 amount) public onlyOwner {
        _mint(msg.sender, amount);
    }

    function burn(uint256 amount) public {
        require(amount > 10, "The amount should be greater than 10");
        require(amount <= balanceOf(msg.sender), "Insufficient balance to burn");
        _burn(msg.sender, amount);
    }

    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }
}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Func&Error.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Func&Error" contract from the dropdown menu. 

After that, click the drowndown menu located at the right side of deploy, then put any name of your choosing and symbol. Then, click transact.

After that transactions was recorded, you can now run the program. Mint for adding and burn for subtracting. Have fun exploring the program
