# Solidity: Unhandled Exception in Token Transfer Function

This repository demonstrates an uncommon bug in a Solidity smart contract's token transfer function and provides a solution.

The bug lies in the transfer function's lack of handling for the case where recipient address hasn't been initialized. If the contract sends tokens to an address with an uninitialized balance, it fails silently instead of handling the error appropriately. This can cause tokens to be lost and lead to unexpected behavior.

## Bug

The original `transfer` function lacks a check to ensure the recipient address has been initialized in the `balanceOf` mapping.  If it hasn't, the addition of tokens (`balanceOf[to] += amount;`) will produce an unexpected result, most likely a silent failure. 

## Solution

The solution introduces a check to ensure that recipient address exists in the `balanceOf` mapping with a balance of 0 before performing the transfer. This prevents the unhandled exception and improves the reliability and security of the smart contract.
