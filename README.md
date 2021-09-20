# The Friendly Hackathon: Start Building on Casper !
This is my slightly more detailed submission for the "Get started with Casper" project organized as part of the first Casper Blockchain Hackathon. September 2021.
https://gitcoin.co/issue/casper-network/gitcoin-hackathon/29/100026611


--> Five tasks have been completed in order to learn more about the Casper ecosystem :
A screen recording showing my process of completing all the tasks is available on youtube via this link --> https://youtu.be/3pfqtDnjY28 (deploy for the task one can be found in the video below). On this page, I will only show you short but clear screen recordings that show the result of the completion of each task.
<br>
<br>
<h4>1- Create and deploy a simple Casper smart contract using cargo casper, make test and a local network</h4>

To start with we will set up our development environment, this means to install Rust, Cmake and Casper Crates. Then, we will be able to build a sample smart contract and run a few basic tests on our local machine.

https://user-images.githubusercontent.com/87818241/133949088-bcb397a6-1bcc-4048-8fc3-5f73a532e523.mp4

<hr width="10%">
<h4>2- Writing a Casper smart contract</h4>

We will follow the tutorial entitled "A contract Tutorial" which will allow us to familiarize ourselves with the process of deploying and using a contract on a local test network. And then we will write a smart contract called the counter contract, it will be built, deployed and tested by incrementing it twice.

https://user-images.githubusercontent.com/87818241/134003051-77a40f2a-9878-458b-bc61-5b7efe444f28.mp4



<hr width="10%">
<h4>3- Key management concepts by modifying the client in the Multi-Sig tutorial to address the additional scenario 2</h4>

By following the "Multi-Signature Tutorial" we will learn to use Casper’s permissions model to sign transactions with multiple keys. We will use a smart contract called "keys-manager" and a sample client that invokes the multi-signature feature on a local Casper network. At the end, as a practical example,  we will run the additional scenario number two : deploying with two special keys.

https://user-images.githubusercontent.com/87818241/134017388-b131b6b3-2883-4537-9418-fa5e68210427.mp4

- Code used in order to match with the scenario 2 : <br>
```ruby
const keyManager = require('./key-manager');
const TRANSFER_AMOUNT = process.env.TRANSFER_AMOUNT || 2500000000;

(async function () {
    
    // Scenario 2 : deploying with special keys. In this example a new additional account will be added to 
    // the mainAccount, the additional account can perform only deploys, but the main account can perform 
    // both deploys and keys management.
    
    // To achive the task, we will:
    // 1. Set mainAccount's weight to 2.
    // 2. Set keys management threshold to 2.
    // 3. Add an additional new account key with weight 1.

    let deploy;

    // 0. Initial state of the account.
    // There should be only one associated key (facuet) with weight 1.
    // Deployment Threshold should be set to 1.
    // Key Management Threshold should be set to 1.
    let masterKey = keyManager.randomMasterKey();
    let mainAccount = masterKey.deriveIndex(1);
    let firstAccount = masterKey.deriveIndex(2);
    let secondAccount = masterKey.deriveIndex(3);

    console.log("\n0.1 Fund main account.\n");
    await keyManager.fundAccount(mainAccount);
    await keyManager.printAccount(mainAccount);
    
    console.log("\n[x]0.2 Install Keys Manager contract");
    deploy = keyManager.keys.buildContractInstallDeploy(mainAccount);
    await keyManager.sendDeploy(deploy, [mainAccount]);
    await keyManager.printAccount(mainAccount);

    // 1. Set mainAccount's weight to 2
    console.log("\n1. Set mainAccount's weight to 2\n");
    deploy = keyManager.keys.setKeyWeightDeploy(mainAccount, mainAccount, 2);
    await keyManager.sendDeploy(deploy, [mainAccount]);
    await keyManager.printAccount(mainAccount);
    
    // 2. Set keys management threshold to 2.
    console.log("\n2. Set Keys Management Threshold to 2\n");
    deploy = keyManager.keys.setKeyManagementThresholdDeploy(mainAccount, 2);
    await keyManager.sendDeploy(deploy, [mainAccount]);
    await keyManager.printAccount(mainAccount);
    
    // 3. Add an additional new account key with weight 1 (additional account).
    console.log("\n3. Add new account key with weight 1.\n");
    deploy = keyManager.keys.setKeyWeightDeploy(mainAccount, firstAccount, 1);
    await keyManager.sendDeploy(deploy, [mainAccount]);
    await keyManager.printAccount(mainAccount);
      
})();
```


<hr width="10%">
<h4>4- Transfer tokens to an account on the Casper Testnet</h4>

We will transfer in command line 10 CSPR from account 1 to account 2 via the Casper blockchain Testnet. Both accounts have been previously provisioned with CSPR thanks to the faucet tool of the cspr.live website.  

https://user-images.githubusercontent.com/87818241/134028018-ce7dc6d8-14f7-4671-946f-3194ad99f03a.mp4

- Account 1 public_key : ```01117809959ead668a82df3cc0ad1737db1682ab63d180973b0ed7002675241d0c``` <br>
- Account 2 public_key : ```012158b458c095e347653cf4fa625b63e6efa84eae39d08ef8820e9ff7a95b61e0``` <br>
- Transaction deploy_hash : ```c3178fa3cc94713c79aae122b742997be26f166d0143a4179f829fb14e53f6fd```




<hr width="10%">
<h4>5- Delegation and Undelegation on the Casper Testnet</h4>

We are going to use the cspr.live user interface to delegate and then undelegate 10 CSPR to a Casper Testnet validator. The account testnet1 011178.....41d0c will be our delegator/undelegator and the chosen validator will be this one 017d9.....2009e .

https://user-images.githubusercontent.com/87818241/134042097-c1fc3075-5b90-4487-8593-ecaf40961982.mp4

- Delegation deploy_hash : ```020e612b2f822ab3a65c6100a126124a7abae66d3313cfa832b21360805fc899``` <br>
- Undelegation deploy_hash : ```bef1659c2962047dad026bed01ee66d34d415bbb7c7b8e611fc18393d6c835ae``` <br>
- Account testnet1 public_key : ```01117809959ead668a82df3cc0ad1737db1682ab63d180973b0ed7002675241d0c``` <br>
- Validator public_key : ```017d96b9a63abcb61c870a4f55187a0a7ac24096bdb5fc585c12a686a4d892009e``` <br>
