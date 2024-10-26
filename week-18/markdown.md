- [x]  **Question 1:** The OZ upgrade tool for hardhat defends against 6 kinds of mistakes. What are they and why do they matter?
  1. Re-deploying an implementation with the same bytecode as one that has already been deployed, saving gas
  2. Re-ordering storage layout (leading to collissions)
  3. Using a constructor that sets variables, but it will only apply in the implementantion without changing the proxy
  4. Letting initialize function only get called once, preventing malicious players from exploiting that function. It does that via the modifier initializable
  5. Separation of concerns with reinitializer modifier which is explicit for contracts that have to be initialized after the first version
  6. Having self-destructs in implementation contracts (versions before selfdestruct upgrade), which would destruct the proxy

- [x]  **Question 2:** What is a beacon proxy used for?
-  A beacon proxy is used for cases where multiple contracts point to one single implementation, making it cheaper to upgrade since you only have to deploy one contract and update the reference of the beacon to that new logic contract. the trade-off is that there is one more call, which makes interactions more costly in terms of gas.

- [ ]  **Question 3:** Why does the openzeppelin upgradeable tool insert something like `uint256[50] private __gap;` inside the contracts? To see it, create an upgradeable smart contract that has a parent contract and look in the parent.
It is used to make sure there are no layout collissions due to mistakes related to the inheritance 

- [ ]  **Question 4:** What is the difference between initializing the proxy and initializing the implementation? Do you need to do both? When do they need to be done?
  
- [ ]  **Question 5:** What is the use for the [reinitializer](https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/master/contracts/proxy/utils/Initializable.sol#L119)? Provide a minimal example of proper use in Solidity


