# SimpleSwap

A minimal Automated Market Maker (AMM) smart contract that supports liquidity provisioning and token swaps using the constant-product formula (`x * y = k`). Inspired by Uniswap V2, this implementation is optimized for educational purposes and simple front-end integration.

> ⚠️ **This contract is for educational and testing purposes only. Do not deploy to mainnet.**

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [How It Works](#how-it-works)
- [Smart Contract](#smart-contract)
  - [Constructor](#constructor)
  - [Modifiers](#modifiers)
  - [Events](#events)
  - [Public Functions](#public-functions)
  - [Internal Functions](#internal-functions)
- [Deployment](#deployment)
- [Author](#author)
- [License](#license)

## Overview
`SimpleSwap.sol` is a minimal AMM contract that allows users to:
- ✅ Add liquidity for a token pair
- ✅ Remove liquidity and redeem their share
- ✅ Swap ERC-20 tokens using constant-product algorithm
- ✅ Get token prices and simulate output amounts

It inherits from `TokenPair`, which handles the LP token logic.

## Features
- 🔹 Constant-product formula: `x * y = k`
- 🔹 ERC-20 compatible liquidity pool token
- 🔹 Min slippage controls (`aMin`, `bMin`, `outMin`)
- 🔹 Deadline protection for all external functions
- 🔹 Secure token transfers
- 🔹 Event emission on all critical operations

## How It Works
1. Liquidity providers deposit token A and token B
2. Contract mints LP tokens in proportion to deposit
3. Swaps adjust reserves while maintaining `x * y = k`
4. Liquidity can be removed by burning LP tokens
5. Reserves are dynamically retrieved from contract balance




- CONTRACT INTERFACE


##Public Functions
##addLiquidity

function addLiquidity(
    address tokenA,
    address tokenB,
    uint256 aDesired,
    uint256 bDesired,
    uint256 aMin,
    uint256 bMin,
    address to,
    uint256 deadline
) external ensure(deadline) returns (uint256 aAmount, uint256 bAmount, uint256 liquidity);

##removeLiquidity

function removeLiquidity(
    address tokenA,
    address tokenB,
    uint256 liquidity,
    uint256 aMin,
    uint256 bMin,
    address to,
    uint256 deadline
) external ensure(deadline) returns (uint256 aAmount, uint256 bAmount);

##swapExactTokensForTokens

function swapExactTokensForTokens(
    uint256 inAmount,
    uint256 outMin,
    address[] calldata path,
    address to,
    uint256 deadline
) external ensure(deadline);


##getAmountOut

function getAmountOut(
    uint256 inAmount,
    uint256 reserveIn,
    uint256 reserveOut
) public pure returns (uint256 outAmount);
Internal Functions

##_calcAmounts

function _calcAmounts(
    uint256 aDesired,
    uint256 bDesired,
    uint256 aMin,
    uint256 bMin,
    uint256 reserveA,
    uint256 reserveB
) internal pure returns (uint256 aAmount, uint256 bAmount);

##_calcLiquidity

function _calcLiquidity(
    uint256 aAmount,
    uint256 bAmount,
    uint256 reserveA,
    uint256 reserveB
) internal view returns (uint256 liquidity);

-----------------------------------------------------------------------------------------------------------------------------------------------------

Deployment Information
Network: Sepolia
Contract Address: [INSERT_CONTRACT_ADDRESS]
Deployer: [YOUR_WALLET_ADDRESS]

💡 Remember to approve() token spending before interacting with the contract

Author
Emiliano Rubinsky
GitHub Profile

License
MIT - See LICENSE for details
