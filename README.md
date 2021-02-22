# Local-Avalanche-Testnet

## Steps to get the Contract Deployed:
In Linux machine:
1. `./avash`
2. runscript `scripts/four_node_network.lua`

## In VS Code and Postman:
1. (__VS Code__) `npm run serve` for the faucet-site
2. (__VS Code__) `npm run serve` for the wallet-site
3. (__Postman__) Use Keystore API `createUser` to create a new user, make sure to store credentials
4. (__Postman__) AVM API `createAddress` to create X-Chain address
5. (__Postman__) Export X-Chain to Private key using AVM `exportKey`
6. (__Postman__) Import to EVM using `importKey`
7. (__Browser__) Add funds to the X-Chain address with the faucet (https://localhost:8080)
8. (__Postman__) Add new variables to environment variables (x-chain, avalancheUsername, avalanchePassword, cchainbech32address (C-ending of the X-Chain))
9. (__Postman__) Use AVM `export` api call with above variables
10. Go to the command line in truffle project:
    1. (__VS Code__) `truffle console --network development`
    2. (__VS Code__) `let account = await web3.eth.personal.newAccount()`
    3. (__VS Code__) `account`
    4. (__VS Code__) Copy account number
    5. (__VS Code__) `await web3.eth.personal.unlockAccount(account)`
    6. (__VS Code__) `.exit`
11. (__Postman__) Paste account number cchainAddress in the environment variables
12. (__Postman__) Use EVM `import` with the above CChain address
13. (__VS Code__) `truffle migrate --network development`


## The Contract should be deployed as long as sufficient funds are in the CChain address

19. *This is for the example contract:
    * `truffle console --network development`
    * `let instance = await Storage.deployed()`
    * `instance.store(1234)`
    * `let i = await instance.retrieve()`
    * `i.toNumber()`
The following should return 1234


## Useful pages to follow if not working
https://medium.com/avalancheavax/how-to-install-and-run-ava-borealis-971286add0c0
https://medium.com/avalancheavax/the-ava-platform-tools-pt-1-the-ava-wallet-b2e849b57632
https://medium.com/avalancheavax/the-ava-platform-tools-pt-2-the-ava-faucet-48f28da57146
