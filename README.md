# local-avalanche-testnet
# local-avalanche-testnet

Steps to get the Contract Deployed:
In Linux machine:
1. `./avash`
2. runscript `scripts/four_node_network.lua`

In VS Code and Postman:
1. (VS Code) `npm run serve` for the faucet-site
2. (VS Code) `npm run serve` for the wallet-site
3. (Postman) Use Keystore API `createUser` to create a new user, make sure to store credentials
4. (Postman) AVM API `createAddress` to create X-Chain address
5. (Postman) Export X-Chain to Private key using AVM `exportKey`
6. (Postman) Import to EVM using `importKey`
7. (Browser) Add funds to the X-Chain address with the faucet (https://localhost:8080)
8. (Postman) Add new variables to environment variables (x-chain, avalancheUsername, avalanchePassword, cchainbech32address (C-ending of the X-Chain))
9. (Postman) Use AVM `export` api call with above variables
10. Go to the command line in truffle project:
    a. (VS Code) `truffle console --network development`
    b. (VS Code) `let account = await web3.eth.personal.newAccount()`
    c. (VS Code) `account`
    d. (VS Code) Copy account number
    e. (VS Code) `await web3.eth.personal.unlockAccount(account)`
    f. (VS Code) `.exit`
11. (Postman) Paste account number cchainAddress in the environment variables
12. (Postman) Use EVM `import` with the above CChain address
13. (VS Code) `truffle migrate --network development`


The Contract should be deployed as long as sufficient funds are in the CChain address

19. *This is for the example contract:
    a. `truffle console --network development`
    b. `let instance = await Storage.deployed()`
    c. `instance.store(1234)`
    d. `let i = await instance.retrieve()`
    e. `i.toNumber()`
The following should return 1234
