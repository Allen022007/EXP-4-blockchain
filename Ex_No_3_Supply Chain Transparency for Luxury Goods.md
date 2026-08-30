## Experiment 4 : Supply Chain Transparency for Luxury Goods
## Date : 13-08-2026
```
Name : W Allen Johnston Ozario
Reg. No : 212224110004
```
# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.
<img width="1128" height="619" alt="image" src="https://github.com/user-attachments/assets/42fe533f-efd7-4963-b4f7-2186e8f10b37" />



Ownership is transferred at every checkpoint.
<img width="1128" height="624" alt="image" src="https://github.com/user-attachments/assets/05c7076c-d17c-49fb-8cc3-f950b6376c0d" />



Buyers can check the authenticity before purchasing.
<img width="1137" height="614" alt="image" src="https://github.com/user-attachments/assets/a0ea9cf8-3f64-408b-ac2b-fbc7f37c801e" />



# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

# RESULT : 

Hence we implemented code for a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
