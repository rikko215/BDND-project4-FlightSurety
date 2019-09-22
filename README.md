# BDND-project4-FlightSurety
Udacity Blockchain Developer Nanodegree project4 (Flight Surety)

## Project overview
- Flight Surety is flight delay insurance for passengers
- Managed as a collaboration between multiple airlines
- Passengers purchase insurance prior to flight
- If flight is delayed due to airline fault, passengers are paid 1.5X the amount they paid for the insurance
- Oracles provide flight status information

## How to set up
`npm install`
`ganache-cli -a 100 -l 9999999`

Rewrite mnemonic in `truffle.js` according to the ganache-cli's mnemonic

truffle compile
truffle test
truffle migrate

### Develop Client
To run truffle tests:

`truffle test ./test/flightSurety.js`

`truffle test ./test/oracles.js`

To use the dapp:

`truffle migrate`

`npm run dapp`

To view dapp:

http://localhost:8000

### Develop Server
`npm run server`
`truffle test ./test/oracles.js`

### Deploy
To build dapp for prod: 
`npm run dapp:prod`

Deploy the contents of the ./dapp folder

## Versions
Truffle v5.0.36 (core: 5.0.36)
Solidity v0.5.8 (solc-js)
Node v10.15.3
Web3.js v1.2.1


## Requirements
1. Separation of Concerns
  - FlightSuretyData contract => data persistence
  - FlightSuretyApp contract => app logic and oracles code
  - Dapp client => triggering contract calls
  - Server app => simulating oracles
2. Airlines
  - Register first airline when contract is deployed
  - Only existing airline may register a new airline until there are at least four airlines registered
  - Registration of fifth and subsequent airlines requires multi-party consensus of 50% of registered airlines
  - Airline can be registered, but does not participate in contract until it submits funding of 10 ether
3. Passengers
  - Passengers may pay upto 1 ether for purchasing flight insurance
  - Flight numbers and timestamps are fixed for the purpose of the project and can be defined in the Daap client
  - If the flight is delayed due to airline fault, passenger receives credit of 1.5X the amount they paid
  - Funds are transferred from contract to the passenger wallet only when they initiate a withdrawal
4. Oracles
  - Oracles are implemented as a server app
  - Upon startup, 20+ oracles are registered and their assigned indexes are persisted in memory
  - Client dapp is used to trigger request to update flight status generating OracleRequest event that is captured by server
5. General
  - Contracts must have operational status control
  - Functions must fail fast -use require() at the start of functions

## Resources

* [How does Ethereum work anyway?](https://medium.com/@preethikasireddy/how-does-ethereum-work-anyway-22d1df506369)
* [BIP39 Mnemonic Generator](https://iancoleman.io/bip39/)
* [Truffle Framework](http://truffleframework.com/)
* [Ganache Local Blockchain](http://truffleframework.com/ganache/)
* [Remix Solidity IDE](https://remix.ethereum.org/)
* [Solidity Language Reference](http://solidity.readthedocs.io/en/v0.4.24/)
* [Ethereum Blockchain Explorer](https://etherscan.io/)
* [Web3Js Reference](https://github.com/ethereum/wiki/wiki/JavaScript-API)
