yixxas

high

# `slash()` can be frontrunned to avoid the penalty imposed on them

## Summary
I believe `slash()` is used to take funds away from a user when they misbehave. However, a malicious user can frontrun this operation or the `pause()` function and call `fullClaimAndExit()` to fully exit before the penalty can affect them. 

## Vulnerability Detail
Malicious users who have intentionally committed some offenses that would lead to getting slashed can listen to the mempool and frontrun the `slash()` or `pause()` function call by the protocol to protect all his assets before slashing can happen.

## Impact
Slashing mechanism implemented can be bypassed by malicious user.

## Code Snippet
https://github.com/sherlock-audit/2022-11-telcoin/blob/main/contracts/StakingModule.sol#L403-L406

https://github.com/sherlock-audit/2022-11-telcoin/blob/main/contracts/StakingModule.sol#L202-L207

## Tool used

Manual Review

## Recommendation
I implore the sponsors to explore alternatives to this slashing mechanism as they can be easily bypassed, especially so by sophisticated users who presumably are the ones who will be getting slashed.
