![istockphoto-1054934320-612x612](https://user-images.githubusercontent.com/53797436/169498822-a345a929-4e06-4674-bf84-143f94655833.jpg)

# Smart Contract Lottery

## Overview

### Background
This is a repo to work with and create a truely random smart contract lottery in a python environment. Anyone can enter the lottery and a random winner will be selected. 

### Flow

1. Users can enter the lottery with ETH based on a USD fee. Players addresses will be tracked using a dynamic array.
2. An admin will choose when the lottery is over (Not truly decentralized but could build out with a DAO being admin, or automatically close due to time parameters using chainlink keepers)
3. The Lottery will select a random winner using ChainLink VRF (Verifiable randomness function)
4. Once the random number has been returned by the ChainLink VRF, we calculate the position of the winner in our players array using the Modulus operation and once determined, transfer the balance of the lottery to that address and finally, reset the lottery.


## Deploy to a testnet / Scripts

```
brownie run scripts/1_deploy_lottery.py
brownie run scripts/2_start_lottery.py
brownie run scripts/3_enter_lottery.py
brownie run scripts/4_end_lottery.py
```
This will deploy the lottery, fund it with LINK, start the lottery, we will then enter it, and then end the lottery.

We can deploy and work with a local network by deploying mocks. 
## Testing

There are 2 types of tests in this project. They follow the arrange, act and assert approach.

- unit tests, which run on a local blockchain.
- integration tests, which run on a testnet

To run the unit tests:
```
brownie test
```
integration tests:
```
brownie test --network <network>
```

## Key Topics Covered
| Area      | Comments |
| ----------- | ----------- |
| Oracle Feeds      | Data feeds that connect Ethereum to off-chain, real-world information       |
| Ownable Contracts   | Provides basic authorization control functions beneficial for preventing misuse or reducing gas fees       |
| Blockchain Randomness | ChainLink VRF creates a random number and proof that is cryptographic in nature using request and recieve model |
| Request and Recieve | One transaction is a request, second txn chainlink node will make function call and return data to smart contract | 
| Funding Contracts | | 
| Working with Mocks | | 
| Working with Interfaces | | 
| Testing | | 
| Events & Emit | | 
