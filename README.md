# Decentralized Stable Coin (DSC)

## Description
This project implements an algorithmically stable, exogenous collateralized by WBTC and WETH, dollar pegged stable coin. The ERC20 implementation of the stablecoin system is governed by DSCEngine.sol, which handles all the minting and redeeming. 
The system should be always ~200% overcollateralized in order to stay usd pegged (by design). In order to be able to mint 100 DSC, a user needs to have at least 200$ worth of collateral (WBTC, WETH) in the system. If the price of ETH/BTC drops, and the user's collateral balance gets below 200$, the user can be liquidated by others in order to keep the overcollateralization on the desired rate. The liquidater gets 10% bonus for the liquidation. Basically, this project is very loosely based on the MakerDAO DSS (DAI) system, but without direct governance and system fees. 
The current ETH/USD and BTC/USD rates are supplied by Chainlink Data Feeds in order to calculate the collateral USD value. If the Chainlink crushes and price feeds stay stale for more than 3 hours, OracleLib will render the DSCE unusable. 
If the ETH of BTC price collapses drastically, the pegging to the USD can be lost. There are no contermeasures implemented.  

Functionality: 
* DecentralizedStableCoin.sol:
    * ERC20 implementation of the stablecoin system.
* DSCEngine.sol:
    * Governs DecentralizedStableCoin.sol
    * Allows users to deposit/redeem collateral in the system, mint/burn DSC and liquidate other users.
* DeployDSC.s.sol:
    * Deploying script
* HelperConfig.s.sol: 
    * Sets the network configuration to chain ID. If working on anvil, also deploys mocks.
* OracleLib.sol:
    * Renders DSCEngine.sol unusable if price feeds are stale more than 3 hours.
* DSCEngineTest.t.sol:
    * Some unit tests.
    * TODO: add some more tests for deploying scripts, DSCEngine and DecentralizedStableCoin.
* Handler.t.sol:
    * Sets reasonable fuction parameters for invariant testing.
* Invariants.sol:
    * Defined invariants for invariant testing.


## Getting Started

### Dependencies

* [foundry](https://github.com/foundry-rs) 
* The contracts use Reentrancy Guard and Ownable from Openzeppelin contract package. In newer versions, Ownable must be declared with an address of the contract owner as a parameter. So there are two possible solutions:
    * Use the 4.8.3 version of Openzeppelin contracts. There is no need to modify the code.
    * For newer versions change the constructor in DecentralizedStableCoin.sol:
    ```
    constructor(address initialOwner) ERC20("DecentralizedStableCoin", "DSC") Ownable(initialOwner){}
    ```
    * When deploying, initialize with address in your possession, and then transfer ownership to the deployed DSCEngine.sol. The deployment scripts must be also adjusted.
    * In newer versions ReentrancyGuard is also located in a different folder: @openzeppelin/contracts/utils/ReentrancyGuard.sol


### Installing

* forge-std:
```
forge install foundry-rs/forge-std --no-commit
```
* Chainlink-brownie-contracts:
```
forge install smartcontractkit/chainlink-brownie-contracts --no-commit
```
* Openzeppelin-contracts:
```
forge install openzeppelin/openzeppelin-contracts@v4.8.3 --no-commit
```

### Executing program

* TODO: Makefile

## Version History

* 0.1
    * Initial Release
