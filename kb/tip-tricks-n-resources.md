# resources, tips & tricks

## introduction

Tip, tricks and references useful when working with blockchain and web3...

### official links

- [hardhat](https://hardhat.org/)
- [chai](https://www.chaijs.com/)
- [OpenZeppelin](https://www.openzeppelin.com/)
- [ethers](https://docs.ethers.io/)
- [web3](https://web3js.readthedocs.io/)

### resources

- [CryptoZombies](https://cryptozombies.io/)
- [Cardano wallets](https://developers.cardano.org/docs/get-started/cardano-wallet-js)
- [Cardano react apps](https://developers.cardano.org/docs/get-started/cardano-serialization-lib/create-react-app/)
- [ETH full nove VS ETH light node](https://www.quicknode.com/guides/infrastructure/ethereum-full-node-vs-archive-node)


## assisted learning

> AI Assisted Learning Path:
> Please explain in few steps how to do SmartContract Testing using NodeJS Chai and Hardhat

1. Install Hardhat: Use the command "npm i --save-dev hardhat" in your terminal to install Hardhat.

2. Initialize Hardhat: Run the command "npx hardhat" to initialize Hardhat in your project.

This will create a default hardhat.config.js file and some other necessary files and folders.

3. Install required packages: You will need to install necessary packages such as @nomiclabs/hardhat-waffle, chai and chai-as-promised, eth-waffle and ethers for writing and running tests on Solidity contracts.

You can use the following command to install these packages:
npm install --save-dev @nomiclabs/hardhat-waffle chai chai-as-promised eth-waffle ethers

4. Write tests: Create a new JavaScript file under the "test" directory with a name like "token.test.js".

Then write some basic tests to check the functionality of the token, such as checking the total supply, transferring tokens between accounts, and checking the balance of accounts.

You can use the hardhat-waffle library to interact with the ERC20 contract.

Below is an example of a basic test:

```javascript

const { expect } = require("chai");
describe("Token", function() {
    let Token;
    let token;
    let owner;
    let addr1;
    let addr2;
    beforeEach(async function() {
        Token = await ethers.getContractFactory("Token");
        token = await Token.deploy();
        [owner, addr1, addr2] = await ethers.getSigners();
    });
    it("Should return correct name and symbol", async function() {
        expect(await token.name()).to.equal("MyToken");
        expect(await token.symbol()).to.equal("MTK");
    });
    it("Should mint correct amount of tokens", async function() {
        await token.mint(owner.address, 1000);
        expect(await token.totalSupply()).to.equal(1000);
    });
    it("Should transfer tokens between accounts", async function() {
        await token.mint(owner.address, 1000);
        await token.transfer(addr1.address, 100);
        expect(await token.balanceOf(addr1.address)).to.equal(100);
    });
});
```
5. Run tests: Run the command "npx hardhat test" in your terminal to run your tests.
Hardhat will compile your contracts and run all tests in the "test" folder.
If any of your tests fail, you will see an error message in the terminal.
Congratulations!
You have tested your Solidity ERC20 token using Hardhat.