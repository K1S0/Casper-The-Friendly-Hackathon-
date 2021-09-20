# The Friendly Hackathon: Start Building on Casper !
This is my slightly more detailed submission for the "Get started with Casper" project organized as part of the first Casper Blockchain Hackathon. September 2021.
https://gitcoin.co/issue/casper-network/gitcoin-hackathon/29/100026611


--> Five tasks have been completed in order to learn more about the Casper ecosystem :
A screen recording showing my process of completing all the tasks is available on youtube via this link --> https://youtu.be/3pfqtDnjY28 (deploy for the task one can be found in the video below). On this page, I will only show you short but clear screen recordings that show the result of the completion of each task.
<br>
<br>
<h4>1- Create and deploy a simple Casper smart contract using cargo casper, make test and a local network</h4>

https://user-images.githubusercontent.com/87818241/133949088-bcb397a6-1bcc-4048-8fc3-5f73a532e523.mp4

<hr width="10%">
<h4>2- Writing a Casper smart contract</h4>

We will follow the tutorial entitled "A contract Tutorial" which will allow us to familiarize ourselves with the process of deploying and using a contract on Testnet, a local test network. And then we will write a smart contract called the counter contract.

https://user-images.githubusercontent.com/87818241/134003051-77a40f2a-9878-458b-bc61-5b7efe444f28.mp4



<hr width="10%">
<h4>3- Key management concepts by modifying the client in the Multi-Sig tutorial to address the additional scenario 2</h4>

By following the "Multi-Signature Tutorial" we will learn to use Casper’s permissions model to sign transactions with multiple keys. We will use a smart contract called "keys-manager" and a sample client that invokes the multi-signature feature on a local Casper network. At the end, as a practical example,  we will run the additional scenario number two : deploying with two special keys.

https://user-images.githubusercontent.com/87818241/134017388-b131b6b3-2883-4537-9418-fa5e68210427.mp4

<hr width="10%">
<h4>4- Transfer tokens to an account on the Casper Testnet</h4>

We will transfer in command line 10 CSPR from account 1 to account 2 via the Casper blockchain Testnet. Both accounts have been previously provisioned with CSPR thanks to the faucet tool of the cspr.live website. Account 1 (01117.....41d0c), Account 2 (01215.....b61e0). Deploy c3178fa3cc94713c79aae122b742997be26f166d0143a4179f829fb14e53f6fd

https://user-images.githubusercontent.com/87818241/134028018-ce7dc6d8-14f7-4671-946f-3194ad99f03a.mp4




<hr width="10%">
<h4>5- Delegation and Undelegation on the Casper Testnet</h4>

We are going to use the cspr.live user interface to delegate and then undelegate 10 CSPR to a Casper Testnet validator. The account testnet1 011178.....41d0c will be our delegator/undelegator and the chosen validator will be this one 017d9.....2009e .

https://user-images.githubusercontent.com/87818241/134042097-c1fc3075-5b90-4487-8593-ecaf40961982.mp4

- Delegation /deploy_hash : 020e612b2f822ab3a65c6100a126124a7abae66d3313cfa832b21360805fc899 <br>
- Undelegation /deploy_hash : bef1659c2962047dad026bed01ee66d34d415bbb7c7b8e611fc18393d6c835ae <br>
- Account testnet1 /public_key : 01117809959ead668a82df3cc0ad1737db1682ab63d180973b0ed7002675241d0c <br>
- Validator /public_key : 017d96b9a63abcb61c870a4f55187a0a7ac24096bdb5fc585c12a686a4d892009e <br>
