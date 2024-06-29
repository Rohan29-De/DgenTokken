# DgenyGamingTokken
# Overview: 
DegenGamingToken (DGN) is an ERC20 token built on the Ethereum blockchain. This token contract uses OpenZeppelin's ERC20 and Ownable contracts to provide standard token functionalities along with additional features such as minting, burning, and redeeming tokens.
# Installation:
To use the DegenGamingToken contract, you need to have the OpenZeppelin library installed in your project. You can install OpenZeppelin using npm:
```
npm install @openzeppelin/contracts
```
# Contract Details:
**Inheritance**
The DegenGamingToken contract inherits from:
* ERC20 - Standard implementation of the ERC20 token.
* Ownable - Provides basic authorization control functions, simplifying the implementation of "user permissions".
# Constructor:
```
constructor() ERC20("Degen", "DGN") Ownable(msg.sender) {}
```
* Sets the token name to "Degen" and the symbol to "DGN".
* Initializes the Ownable contract with the deployer's address as the owner.
# Functions:
**Mint**
```
function mint(address to, uint256 amount) public onlyOwner {
    _mint(to, amount);
}

```
* Mints new tokens to a specified address.
* Only the owner of the contract can call this function.
**Burn**
   ```
   function burn(uint256 amount) public {
    _burn(msg.sender, amount);
   }
    ```  
* Burns a specified amount of tokens from the caller's address.
**TransferToken**
   ```
   function transferToken(address _toAddress, uint _amount) public {
    bool success = transfer(_toAddress, _amount);
    assert(success);
   }
    ```
* Transfers a specified amount of tokens to a specified address.
* Ensures the transfer is successful using assert.
**RedeemToken**
   ```
    function redeemToken(uint _amount) public {
    require(balanceOf(msg.sender) >= _amount, "Insufficient token balance to redeem");
    _burn(msg.sender, _amount);
    emit TokensRedeemed(msg.sender, _amount);
   }
    ```
* Allows a user to redeem a specified amount of tokens.
* The tokens are burned from the caller's address.
* Emits the TokensRedeemed event upon successful redemption.
**CheckTokenBalance**
   ```
   function checkTokenBalance(address _account) public view returns (uint) {
    return balanceOf(_account);
   }
    ```
* Returns the token balance of a specified address.
**Events**
  TokensRedeemed
   ```
   event TokensRedeemed(address indexed user, uint amount);
    ```

* Emitted when tokens are successfully redeemed.
# Usage:
**Deploying the Contract**
1. Ensure you have the OpenZeppelin library installed.
2. Compile and deploy the contract using your preferred Ethereum development environment (e.g., Truffle, Hardhat, Remix).
   
**Interacting with the Contract**
* Minting Tokens: Only the owner can mint new tokens.
* Burning Tokens: Any user can burn their own tokens.
* Transferring Tokens: Users can transfer tokens to any address.
* Redeeming Tokens: Users can redeem and burn their own tokens.
* Checking Balance: Users can check the token balance of any address.


  
   






