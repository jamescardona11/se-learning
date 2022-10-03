# JS WEB3

**Compile contract**
`yarn solcjs --bin --abi --include-path node_modules/ --base-path . -o . <contract>`

.wait(1) es esperar un block para poder continuar

**Compile and deploy** with hardhat
yarn hardhat compile
yarn hardhat run <folder> --network rinkeby

npm
solidty coverage
gasreporter

### hardhat 
- Deploy: Install hardhat deploy to do this and delete the deploy script
- Create deploy scripts
- configurar otras networks con hardhat
- Mocks

### Interact with contract
- compile our solidity
- get bytecode
- get abi
- connecting blockchain
- create contract
- get last transaction - nonce

### Create transaction
- Build a transaction
- sign
- send 

### sequence
- Provider
- Signer
- Contract
- ABI & Address



### Cómo iniciar un proyecto con HardHat
- yarn add --dev hardhat
- yarn hardhat
  * escoger create an empty hardhat.con
- yarn add --dev @nomiclabs/hardhat-ethers@npm:hardhat-deploy-ethers ethers @nomiclabs/hardhat-etherscan @nomiclabs/hardhat-waffle chai ethereum-waffle hardhat hardhat-contract-sizer hardhat-deploy hardhat-gas-reporter prettier prettier-plugin-solidity solhint solidity-coverage dotenv





@@@ Lotery contract