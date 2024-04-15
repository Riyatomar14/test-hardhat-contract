# setting up the environment 

```
sudo apt update
sudo apt install curl git
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

* In case of error in libnode file (remove file , install dependencies , upgrade node , remove unwanted elements)

```
sudo apt remove libnode-dev
sudo apt install -f
sudo apt upgrade nodejs
sudo apt autoremove
```

* We'll install Hardhat using the Node.js package manager (npm)
  
## Open a new terminal and run these commands to create a new folder:

```
mkdir hardhat-tutorial
cd hardhat-tutorial
```

* Then initialize an npm project

```
npm init
```

* Now we can install Hardhat:

```
npm install --save-dev hardhat

```

* In the same directory where you installed Hardhat run:

```
npx hardhat init
```
![Screenshot 2024-04-15 230154](https://github.com/Riyatomar14/test-hardhat-contract/assets/143107173/62c7afd6-ba7b-43fb-b86f-8bb2b937ac26)

- Install the Hardhat plugin for ethers.js, we will use recommended plugins here
    ```bash
    $ npm install --save-dev @nomicfoundation/hardhat-toolbox
    ```
- Add the following lines to `hardhat.config.js`
    ```javascript
    require("@nomicfoundation/hardhat-toolbox");
    ```
    - which will look like this

  ![image](https://github.com/Riyatomar14/test-hardhat-contract/assets/143107173/42c97fb4-d9e1-453e-9735-4ddb4a212239)


## Writing and compiling contracts


### Writing contracts

* Start by creating a new directory called ``` contracts ``` and create a file inside the directory called ``` Token.sol ```
    ```bash
    $ mkdir contracts
    $ sudo vi Token.sol
    ```
- Write your contract in the file you just created.
   Token.sol(write above)

### Compiling contracts

- Run the following command to compile your contracts
    ```bash
    $ npx hardhat compile
    Compiled 1 Solidity file successfully (evm target: paris).
    ```
![Screenshot 2024-04-15 230230](https://github.com/Riyatomar14/test-hardhat-contract/assets/143107173/714c7127-7e03-4bbe-9aa7-cb03bd49c899)
 
## Testing contracts

### Writing tests

* Create a new directory called ``` test ``` inside our project root directory and create a new file in there called ```Token.js```
    ```bash
    $ mkdir test
    $ touch Token.js
    ```
- Write your tests in the file you just created.
  
```
const { expect } = require("chai");

describe("Token contract", function () {
  it("Deployment should assign the total supply of tokens to the owner", async function () {
    const [owner] = await ethers.getSigners();

    const hardhatToken = await ethers.deployContract("Token");

    const ownerBalance = await hardhatToken.balanceOf(owner.address);
    expect(await hardhatToken.totalSupply()).to.equal(ownerBalance);
  });
});
```  

### Running tests

- Run the following command to run your tests
    ```bash
    $ npx hardhat test
    ```
    - which will look like this
![Screenshot 2024-04-15 220004](https://github.com/Riyatomar14/test-hardhat-contract/assets/143107173/3f2002d7-2546-4fe6-b9ff-35e82271ef1a)

    
## Deploying contracts to live network

- To deploy your contracts to a live network, you need to create a new network in the `hardhat.config.js` file.
- 
   sample you take

  ```
  const { buildModule } = require("@nomicfoundation/hardhat-ignition/modules");

  const TokenModule = buildModule("TokenModule", (m) => {
  const token = m.contract("Token");

  return { token };
  });

  module.exports = TokenModule;
  ```

![Screenshot 2024-04-15 220152](https://github.com/Riyatomar14/test-hardhat-contract/assets/143107173/4f7b0408-a9a8-4291-a9cd-91a5deb0e020) 
