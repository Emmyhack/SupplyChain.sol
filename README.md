# SupplyChain Smart Contract

## Overview

The `SupplyChain` smart contract is a simple supply chain management solution built on the Ethereum blockchain. It allows the owner to add, update, and manage products within a supply chain context. The contract includes functionalities for tracking product status and managing ownership, while ensuring security against reentrancy attacks.

## Features

- **Product Management**: Add, update, and manage products in the supply chain.
  
- **Product Status Tracking**: Update the status of products as they move through the supply chain.
  
- **Ownership Control**: Only the contract owner can modify product details.
  
- **Reentrancy Protection**: The contract uses a simple non-reentrancy guard to prevent reentrant calls during fund withdrawals.
  
- **Ether Management**: The contract allows the owner to withdraw Ether accumulated in the contract.



## Contract Structure
## This section would highlight and explain the main function and syntax used in the contract.

### Enums

- `Status`: Represents the status of a product, which can be one of the following:
  - `Created`
  - `Shipped`
  - `Delivered`
  - `Canceled`


### Structs

- **`Product`**: Represents a product in the supply chain with the following properties:
  - **`name`**: The name of the product.
  
  - **`price`**: The price of the product (normalized to 18 decimals).
    
  - **`quantity`**: The available quantity of the product.
    
  - **`status`**: The current status of the product.
    
  - **`exists`**: A flag indicating whether the product exists.



### Events

- **`ProductAdded`** : shows when a new product is added.
  
- **`ProductUpdated`**: shows when an existing product is updated.
  
- **`ProductStatusUpdated`**: shows when the status of a product is updated.
  
- **`FundsWithdrawn`**: shows when the owner withdraws funds from the contract.


  

### Modifiers

- **`onlyOwner`**
   This modifier restricts access to certain functions, allowing only the contract owner to execute them. It checks if the `msg.sender` (the address calling the function) is the same as the `owner` of the contract address. If it is not thesame, it reverts the transaction with the message "Not the contract owner".

- **`nonReentrant`**
   This modifier prevents reentrant calls to functions that use it. It sets a `locked` state to true at the beginning of the function execution, and resets it to false at the end. If a function marked with this modifier is called again while it is still executing, the transaction will revert with the message "Reentrant call".



## Functions
## This section would help you understand the funtions.

### `addProduct(uint256 productId, string memory name, uint256 quantity)`

- **Description of the addProduct**
  Adds a new product to the supply chain.
  
- **the Parameters in the bracket**:
  - **`productId`**
     A unique identifier for the product.
    
  - **`name`**
     The name of the product.
    
  - **`quantity`**
     The initial quantity of the product.
    
- **Requirements to execute  the function above**:
  - Only the contract owner can call this function.
  - The product ID must be unique.
  - The product name cannot be empty.


### `updateProduct(uint256 productId, uint256 quantity)`

- **Description of updateProduct function**
 Updates the price and quantity of an existing product.

- **Parameters**

  - **`productId**
The identifier of the product to update.

  - **`quantity`**
The new quantity of the product.

- **Requirements to execute the function above**:
  - Only the contract owner can call this function.
  - The product must exist.
  

### `updateProductStatus(uint256 productId, Status status)`

- **Description of updateProductStatus function**
Updates the status of a product.
**The status would include what you have seen in the enum**

- **Parameters**

  - **`productId`**
The identifier of the product.

  -**`status`**
The new status of the product.

- **Requirements to execute the function above**:
  - Only the contract owner can call this function.
  - The product must exist.



### `getLatestPrice()`

- **Description of getlatestPrice**
Simulates fetching the latest price for a product. (This function is a placeholder and should be replaced with actual price fetching logic.)

- **Returns**: A simulated normalized price (currently returns a fixed value for demonstration).



### `withdrawFunds()`

- **Description of withdrawFunds**
Withdraws all Ether from the contract to the owner's address.

- **Requirements to execute the function**:
  - Only the contract owner can call this function.
  - The contract must have a positive balance.



### Fallback Functions

- **`receive()`**
A fallback function that allows the contract to receive Ether.



## Deployment

You can deploy the contract on your remix IDE to test the functionalities. Before we can go ahead to VSCODE to continue previously updated contract the  we can develop using Hardhat framework.

**License**
This project is licensed under the MIT License.

**Note**
This should guide individuals understanding in doing the documentation on the use case. 
