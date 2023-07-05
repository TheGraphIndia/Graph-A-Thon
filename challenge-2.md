# 🌱 Challenge II: Deploy your own Subgraph

## Description

Deploy a simple smart contract on the Polygon Mumbai testnet and deploy a subgraph for it.

## Rewards

We can’t wait for you to complete this and claim, **your PFP’s 🖼️** and **$GRT**.

## Hashtags Used

- [ ] `#graphathon`
- [ ] `#graphIndia`

## Steps on how to Contribute ?

 - Open [Remix IDE](https://remix.ethereum.org/). Create a Solidity file `Graphathon.sol` and paste the following code.

```solidity
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

contract Graphathon {

    event ChangeNameEvent (string name);
    event ChangeTwitterNameEvent (string name);
    event TransferEvent(address from, address to, uint amount);

    string public name = "The Graph";
    string public twitterName = "graphprotocol";

    function changeName(string calldata _name) public {
        name = _name;
        emit ChangeNameEvent(_name);
    }

    function changeTwitterName(string calldata _twitterName) public {
        twitterName = _twitterName;
        emit ChangeTwitterNameEvent(_twitterName);
    }

    function transfer(address payable to) public payable {
        to.transfer(msg.value);
        emit TransferEvent(msg.sender, to, msg.value);
    }
}
```
 - Compile the contract and deploy it to Mumbai testnet using `Injected Provider` as the environment. Note down the contract address.
 - Verify and publish your smart contract (Don't know how? See [this](https://medium.com/etherscan-blog/verifying-contracts-on-etherscan-f995ab772327))

 - Go to the [Subgraph studio](https://thegraph.com/studio/) and connect your wallet.

 - Click on `Create a Subgraph`. Name your subgraph and select 'Polygon Mumbai' as the blockchain network. Your subgraph is created 🤩.

 - You need to install The Graph protocol CLI to work with the subgraph.
  ```
  npm install -g @graphprotocol/graph-cli
```
OR
```
  yarn global add @graphprotocol/graph-cli
  ```
 - Create an empty folder and open it in your code editor (I love VSCode ❤️). Change the directory to that folder and fire up your terminal pointing to that folder.
 - Now we will initialize the subgraph using the following command
```
graph init --studio SUBGRAPH_NAME
```
 - Select `ethereum` as Protocol
 - Press Enter for `subgraph slug` and `Directory to create subgraph in`.
 - Select `mumbai` as our network.
 - Enter the contract address of your deployed contract from above. It will automatically fetch the ABI as we have verified our contract.
 - Enter the block number in which the contract is created.
 - Enter `Graphathon` as the contract name.
 - Press Enter for `Index contract events as entities`.

 - You have successfully created your first Subgraph. (YOU ARE AWESOMEEE! 🙇🏻‍♂️)
-------

 - You need to authenticate your subgraph. Refer dashboard for the key.
  ```
  graph auth --studio 5a6288af6001705f65d514e5423b018d
  ```
 - Change the directory to your deployed subgraph folder
  ```
  cd graphathon
  ```

Make use of the dashboard to see the commands

<img width="521" alt="Screenshot 2023-07-03 at 5 58 53 PM" src="https://github.com/TheGraphIndia/Graph-A-Thon/assets/47234407/cbf55a0d-409d-4212-be34-f529f655832f">

 - Now we build our subgraph using the following command
  ```
  graph codegen && graph build
  ```
 - Final Step - Deploy your subgraph. 🥳🥳🥳
  ```
  graph deploy --studio graphathon
  ```
 - You can give the version as `v0.1`

 - Play around with your contract. Transfer some ETH / MATIC or change your name or Twitter username using the Remix IDE.

 - Go to the `Playground` on the dashboard and query the data.

 - Create a new file with title `solution-2.md` and add the contract address and the subgraph endpoint in the file.

 - **[VERY IMPORTANT STEP]**  Add the link of this `solution-2.md` file to this [Graph-A-Thon challenge submission form](https://airtable.com/).
 
 
 (ex: https://github.com/username/Graph-Advocates--Graph-A-Thon-2023/blob/username_graphathon/solution-2.md)

-------
 
## Submission Guidelines

- Create a new branch `username_graphathon`, e.g. `yash251_graphathon`

- Create a file named `solution-2.md` for this challenge. 

- Add the contract address and the subgraph endpoint in the file.

- Submit details on the [**Airtable form**](https://airtable.com/).

-------

[**Submission Challenge II form**](https://airtable.com/)

*This is an important step, please don't skip it.*
