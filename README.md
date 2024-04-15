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
![image](https://github.com/Riyatomar14/test-hardhat-contract/assets/143107173/812e987b-7d3b-407c-a80b-d21437624ca7)

- Install the Hardhat plugin for ethers.js, we will use recommended plugins here
    ```bash
    $ npm install --save-dev @nomicfoundation/hardhat-toolbox
    ```
- Add the following lines to `hardhat.config.js`
    ```javascript
    require("@nomicfoundation/hardhat-toolbox");
    ```
    - which will look like this

      

## Writing and compiling contracts


### Writing contracts

- Create a new contract file in the `contracts/` directory
    ```bash
    $ touch contracts/Token.sol
    ```
- Write your contract in the file you just created.
    - [Sample contract](contracts/Token.sol)

### Compiling contracts

- Run the following command to compile your contracts
    ```bash
    $ npx hardhat compile
    Compiled 1 Solidity file successfully (evm target: paris).
    ```
    
## Testing contracts

### Writing tests

- Create a new test file in the `test/` directory
    ```bash
    $ touch test/Token.js
    ```
- Write your tests in the file you just created.
    - [Sample test](test/Token.js)

### Running tests

- Run the following command to run your tests
    ```bash
    $ npx hardhat test
    ```
    - which will look like this

     
    
## Deploying contracts to live network

- To deploy your contracts to a live network, you need to create a new network in the `hardhat.config.js` file.
    - [Sample hardhat.config.js](hardhat.config.js)
