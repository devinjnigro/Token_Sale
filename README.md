# Token_Sale

## PupperCoin.sol
The first Solidity file created, PupperCoin.sol, contains the ERC20 contract PupperCoin, which inherits ERC20, ERC20Detailed, and ERC20Mintable from Github: 

```
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20Detailed.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20Mintable.sol";
```

## PupperCoinCrowdSale.sol
The second file inherits PupperCoin as well as the following OpenZeppelin resources from Github:

```
import "./PupperCoin.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/Crowdsale.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/emission/MintedCrowdsale.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/validation/CappedCrowdsale.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/validation/TimedCrowdsale.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/distribution/RefundablePostDeliveryCrowdsale.sol";
```

Two contracts are created: PupperCoinSale and PupperCoinSaleDeployer. PupperCoinSale uses the inherited functionality of the above imports to initiate the a crowdsale intended to generate a specified amount of funds within a given time period. Once the required funds have been raised and the period closes, the tokens can be withdrawn by the accounts that paid for them.

PupperCoinSaleDeployer allows the initiator of the contracts to set some dynamic parameter values for PupperCoin and PupperCoinSale, while hard coding others, such as the initial amount of tokens, conversion rate, and opening and closing times.

## Deployment

To initiate the crowdsale, the PupperCoinSaleDeployer contract must be deployed first. The owner of the contract can input values for name, symbol, wallet, and goal. Once deployed, the contract will produce two addresses: one for the token, and one for the sale. When deploying PupperCoin and PupperCoinSale, these two addresses must be input into the At Address box (token address for PupperCoin and token sale address for PupperCoinSale). These two contracts will then deploy with the parameters given in PupperCoinSaleDeployer.

Next, in the PupperCoinSale contract, an investor can buy tokens by setting a value of wei that they are willing to spend in Remix and then inputting their wallet address in the Buy Tokens function. This will automatically update the amount of wei raised. Once the amount of wei raised reaches the goal amount, investors will no longer be able to purchase tokens. 

The crowdsale is set to close 24 weeks after deployment of the PupperCoinSale contract. Once this occurs, as long as the goal has been reached, the crowdale can be finalized using the Finalize function. investors are now able to withdraw their tokens using the withdrawTokens function. After an investor has withdrawn their tokens, they can check their token balance in the PupperCoin contract, which will now be updated.






