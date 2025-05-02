<h3 align="center">Decentralized Stable Coin</h3>

  <p align="center">
    Algorithmically stable, exogenous collateralized by WBTC and WETH, dollar pegged stable coin
    <br />
  </p>

<p align="center">
  <img src="https://img.shields.io/badge/Solidity-e6e6e6?style=for-the-badge&logo=solidity&logoColor=black" alt="Solidity"/>
  <img src="https://camo.githubusercontent.com/8c47fd6bf4ac8eec4be8caefd7d56b8cdbff9de4985b76e3ff3ab1497d7363e8/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f466f756e6472792d677265793f7374796c653d666c6174266c6f676f3d646174613a696d6167652f706e673b6261736536342c6956424f5277304b47676f414141414e53556845556741414142514141414155434159414141434e6952304e414141456c456c45515652346e483156555568556152673939383459647a42706b7152305a3231307249455349585361624562634867796472704e52526a30306b57617a746a3055314d4f57304d4f49624433303049764c4d7142704d54475978646f71796f524e4455455342445777557550756743535373544d3775304f6a312f2b656664694d636d6e50322f66446437374434662f4f4236784361327572515a626c6c56494359477471616e4b31744c53344164674179414167797a4a615731734e712f756c543474774f4777346650697741474470374f77385656316437625661725257785743772f6b386d67736245786d30776d5a2b4c782b4d2f5872312f2f4363417353566d534a4830314d634c68734145416e45356e782b546b35422f78654a784f70354e39665832737171716978574c686e5474333648413447497646474931475533563164663550652f394431743765486b676b45757a6f3647425054343957576c6f713748613766756a5149546f6344753761745573336d38336936745772326f6b544a2f6a6978517565506e3236357a5053634468736b47555a652f6675625876382b44467633727970626469775161786274343652534954373975336a304e415162393236525656564f54342b5471765679767a38664430594443354e546b3679736248786c43524a2f354b536c41415552794b5254464e546b7741673774363953352f507837362b50713747794d6749392b2f667a394852555149514f336273454b4f6a6f333844734a43554a4144772b2f3042565657376f74486f387073336234797658723343784d514554435954544359544e453044414f546c3553475879304652464f7a5a7377646d73786b564652584c4e545531786d67302b6b4e76622b2f3341474163474269493739363957776367367572712b4f544a4539363764343962746d7a68395054305233574a52494b4251494442594a425455314e73614767674147477a32665465337435664165515a415777754c69347550336e79704f5431656d457747464265586f3761326c6f734c4379676f6145422f6633394d4a6c4d434956436b43514a42773865684e56716863666a51584e7a7331525355694b7458372b2b4445415a71717171334b465169414259554644414d32664f6b4351584678644a6b766676333264685953473958692b765862764732646e5a6a346f446751434c696f716f4b417148686f626f6444712f4d63374e7a556b6c4a535549426f4f7732577a59746d30626c7065587357624e476b784d544f44703036646f61327644344f41674e6d37634349764641704c516452336e7a7033447a70303738664c6c537851564665486475336341674970486a7836392f7a425558356b2b4d4442417439764e5938654f736275376d366c556967634f484b444c3557496d6b79484a7a39544759724563414c734d49506e363965735a54644d49674d2b6550554e58567864753337364e73724979754e3175584c70304357617a476350447733433558464256465766506e6b564e5451313850702b657a5759354d7a507a4f344466414142486a687a704a736c554b71566476486952342b506a624739765a79365849306b754c5330786d55785343454753395076394c4330747064466f5a47566c705361456f4d2f6e757749414b782f37713547526b6239436f5a42515656576350332b657a35382f4a306d6d30326b4f44673779776f554c6a4d5669544b6654744e7674584c74324c5464743271546e63726e6c736247784c49437653557166726c35484a424c68314e54556b6842434a386d4668515832392f6454565655574642547777594d48314857646c7939667071496f65694b52574a71666e3264316458576e4c4d7566377a4d41484431367447642b666e37465a7932627a59724b796b6f644141465156565639635846526b4e5465766e334c75626b357472533058506e6678484534484e384f44772b6e562f79616e70366d782b4f68782b503561494d51676d4e6a59332f5731745a2b74357273537747372b666a78342f37362b76726d3764753332776f4c433030416b45366e3338666a385a6d4844782f2b637550476a5238424a4c3859734374596451494d414c5971696c4b764b456f394150754874792b656748384133476646444a586d786d4d41414141415355564f524b3543594949253344266c696e6b3d6874747073253341253246253246626f6f6b2e676574666f756e6472792e7368253246" alt="Foundry"/>
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="MIT"/>
</p>

# About The Project

## Project Description

This project implements an algorithmically stable, exogenous collateralized by WBTC and WETH, dollar pegged stable coin. The ERC20 implementation of the stablecoin system is governed by DSCEngine.sol, which handles all the minting and redeeming. The system should be always ~200% overcollateralized in order to stay usd pegged (by design). In order to be able to mint 100 DSC, a user needs to have at least 200$ worth of collateral (WBTC, WETH) in the system. If the price of ETH/BTC drops, and the user's collateral balance gets below 200$, the user can be liquidated by others in order to keep the overcollateralization on the desired rate. The liquidater gets 10% bonus for the liquidation. Basically, this project is very loosely based on the MakerDAO DSS (DAI) system, but without direct governance and system fees. 
The current ETH/USD and BTC/USD rates are supplied by [Chainlink Data Feeds](https://docs.chain.link/data-feeds) in order to calculate the collateral USD value. If the Chainlink crushes and price feeds stay stale for more than 3 hours, OracleLib will render the DSCE unusable. 
If the ETH of BTC price collapses drastically, the pegging to the USD can be lost. There are no contermeasures implemented.  

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Project Overview
* Scripts:
    * DeployDSC.s.sol: deploying script
    * HelperConfig.s.sol: Sets the network configuration to chain ID. If working on anvil, also deploys mocks.
* Contracts:
    * DecentralizedStableCoin.sol: ERC20 implementation of the stablecoin system.
    * DSCEngine.sol: Governs the coin, allows users to deposit/redeem collateral in the system, mint/burn DSC and liquidate other users.
    * OracleLib.sol: Renders DSCEngine.sol unusable if price feeds are stale more than 3 hours.


## Tests and Security Overview

* *Static code analysis*: 
    * [Slither](https://github.com/crytic/slither)
    * [Aderyn](https://github.com/Cyfrin/aderyn)
* *Dynamic code analysis*:
    * Unit tests in test/unit
    * Stateful fuzz test in test/fuzz using Foundry 

<p align="right">(<a href="#readme-top">back to top</a>)</p>


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

# License

*Distributed under the MIT license.*

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# Contact

*Flopcatcher* - flopcatcher.audit@gmail.com

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# Disclaimer

*This codebase has not undergone a proper security review and is therefore not suitable for production.*


<p align="right">(<a href="#readme-top">back to top</a>)</p>
