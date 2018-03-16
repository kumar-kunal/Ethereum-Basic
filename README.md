# Ethereum-Basic

### What is Ethereum
- In traditional web application, All the clients interact with this one central application.Clients can be a browser, another api consuming your service etc. When a client makes a request to the server, the server does it’s magic, talks to the database and/or cache, reads/writes/updates the database and serves the client.But, in this method, data is controlled by specific body. i.e. Data is not in public domain. 
suppose ,you are a seller at Flipkart. You have great reviews and rating. your bussiness is booming out. but, due to some reason , flipkart block your account. now, they are asking you to give much more commission. so what would you do?
 What if there was a way to eliminate flipkart altogether from the transaction between buyer and seller so you save on commission and also you have access to all your data? This is where decentralized applications come in to picture. Ethereum makes it very easy to build Dapps (decentralized applications).
 
In DAPP, every client (browser) communicates with it’s own instance of the application. There is no central server to which all clients connect to. This means, every person who wants to interact with a dapp (Decentralized Application) will need a full copy of the blockchain running on their computer/phone etc. That means, before you can use an application, you have to download the entire blockchain and then start using the application. This might sound ridiculous at first but it has the advantage of not relying on a single central server which might disappear tomorrow.

In reality, you don’t need to spend lot of your hard disk and RAM downloading the entire blockchain. There are a few workarounds/optimizations to keep the application decentralized yet make the interaction quick and easy.


#### Setup for Ethereum

You need to have (npn,nodeJs,Ganache) in your system.

 - nodeJs and npn
 
 You can download the file from the browser or from the console. The latter is shown below (Note: the specific Node.js version might be different for you):
 
`` wget https://nodejs.org/dist/v8.10.0/node-v8.10.0-linux-x64.tar.xz ``

To make sure you can unpack the file, install xz-utils:

 ``sudo apt-get install xz-utils``
 
Next, execute the following command to install the Node.js binary package in /usr/local/:

``tar -C /usr/local --strip-components 1 -xJf node-v4.4.4-linux.x64.tar.xz``

Now, create project directory

`` mkdir voting_dapp ``

Get inside project folder

`` cd voting_dapp ``

create a folder for node and ganache-cli inside project folder...

`` mkdir node_modules ``

install Ganache-cli and web3

`` npn install ganache-cli web3@0.20.2 ``

now 

`` node_modules/.bin/ganache-cli ``

Ganache is running now...


## creating , compiling and deploying the dapp

Open new terminal and change current dir with project dir

To compile the solidity code, we will first install npm module called solc

`` npm install solc ``


open node in terminal

 ``Web3 = require('web3')``
 
 
 ``web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));``
 
 
`` code = fs.readFileSync('Voting.sol').toString()``


 ``solc = require('solc')``
 
 
 ``compiledCode = solc.compile(code)``
 
 ``abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)``
 
 ``VotingContract = web3.eth.contract(abiDefinition)``
 
 ``byteCode = compiledCode.contracts[':Voting'].bytecode ``
 
 `` deployedContract = VotingContract.new(['Rama','Nick','Jose'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000}) ``
 
 ``deployedContract.address``
 
 ``contractInstance = VotingContract.at(deployedContract.address)``
 


Note : change "address" field with your address in "index.js" file.

``contractInstance = VotingContract.at('---address---');``  

you can get address by executing `` contractInstance.address`` in your nodeJs console.
