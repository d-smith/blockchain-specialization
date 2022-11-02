# Decentralized Applications (Dapps)

## Week 1 - Decentralized Applications

Learning Objectives

* Explain the high level architecture of a Dapp
* Explain at a high level the access from a web client to the blockchain server
* List a few Ethereum APIs that facilitate Dapp development
* Explain the functions and usage details of various APIs

### Blockchain Server

Decentralized applications or DApps,
open up the features and services of the blockchain to the whole world for
review, interaction, and enjoyment. DApp gives access to people,
applications and systems, not necessarily known to each
other to transact peer to peer. DApp is an end to end
application on a blockchain.


A DApp or a decentralized application
depends on the functionality of a blockchain for
its infrastructure and operations. In its simplest form, a DApp has
a client interface as a front-end, and a back-end that includes a blockchain and
a smart contract.

e prepared to chart your path through the emerging
decentralized software culture. A DApp or a decentralized application
depends on the functionality of a blockchain for
its infrastructure and operations. In its simplest form, a DApp has
a client interface as a front-end, and a back-end that includes a blockchain and
a smart contract. Consider, for example,
a simple wallet application client, and the Bitcoin blockchain
decentralized infrastructure. This is similar to the architecture
of a web browser and a web server, but
with one significant difference. The blockchain enables
a decentralized infrastructure.

Dapp Stack

* Verticals - end user applications
* Application framework - smart contract
* Ethereum blockchain and EVM
* Peer to peer networking and operating systens
* Hardware

Linkage

* https://www.coindesk.com/information/what-is-the-difference-blockchain-and-database/
* https://www.youtube.com/watch?v=gjwr-7PgpN8&t=10s
* https://www.youtube.com/watch?v=WSN5BaCzsbo&t=5s
* https://www.cryptocompare.com/coins/guides/what-is-and-how-to-use-the-ens/
* https://www.npmjs.com/package/ethereum-ens


### Daap Defined

What is a Dapp? A Dapp, or decentralized application,
solves a problem that requires blockchain services and blockchain
infrastructure for realizing its purpose.

If you are programmatically assembling
the Dapp without the help of any development involvement, you copy
the web3 deploy script into your app, say an HTML JavaScript file as a script. Deploy the smart contract using
the functions in the script. And invoke the smart contract function
using the functions in the script, and the ABI, and
the smart contract address.

web app - use web3 js module for json/rpc interaction with eth rpc port/node

Linkage:

* https://blockchainhub.net/decentralized-applications-dapps/
* https://www.youtube.com/watch?v=97ufCT6lQcY
* https://www.freecodecamp.org/news/how-to-transfer-funds-on-the-ethereum-network-using-the-geth-cli-b7eac16aa3a9/

### EThereum APIs

Management APIs

* includes admin, debug, miner, personal, and txpool 
    * admin.addPeer()
    * debug.dumpBlock(16)
    * miner.start()
    * personal.newAccount()
    * txpool.inspect()
* support methods for management of the geth node

Web 3 APIs

* whisper api - web3.ssh
* javascript api
* smart contract deployment

Web 3 Arch

![](dapparch.png)

Linkage

* Plasma - historical - https://ethereum.org/en/developers/docs/scaling/plasma/
* https://cointelegraph.com/news/worlds-first-dapi-decentralized-application-programming-interface
* https://web3js.readthedocs.io/en/v1.2.9/
* https://gavofyork.gitbooks.io/turboethereum/content/cli_tools.html


## Week 2 Truffle IDE

### Truffle

All inclusive IDE - local chain, templates, etc.

Design process

* Design the data and operations
* Add modifiers and validation checks
* Contract test
* Add front end component
* Test full app

Structure: name, data, modifiers, functions

Truffle

* truffle init
* truffle compile
* truffle develop - create local test net
* truffle migrate
* truffle test

Node.js, truffle via npm, metamask - can use VM for this course

For the Ballot1 example

* Create a Ballot1 dir and cd into it
* truffle init

migrations - smart contract to take care of deployments and updates

VM Ware installer - https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html

 sudo npm install -g truffle@4.1.15
 
 copy Ballot.sol into contracts directory
 truffle compile

 Coursera materials - unbelievably frustrating and clunky to test a simple example.

 Here's a working example, assuming you can get the obsolete tools on the base image updated to the slightly less out of date tools for the example.

 Ballot.sol

 ```
 pragma solidity  >=0.4.17;

contract Ballot {

    struct Voter {
        uint weight;
        bool voted;
        uint8 vote;
        // address delegate;
    }

    //modifer
    modifier onlyOwner () {
      require(msg.sender == chairperson);
      _;
    }

    /* struct Proposal {
        uint voteCount; // could add other data about proposal
    } */
    address public chairperson;
    mapping(address => Voter) public voters;
    uint[4] public proposals;

    // Create a new ballot with 4 different proposals.
    function Ballot () public {
        chairperson = msg.sender;
        voters[chairperson].weight = 2;
    }

    /// Give $(toVoter) the right to vote on this ballot.
    /// May only be called by $(chairperson).
    function register(address toVoter) public onlyOwner{
        if(voters[toVoter].weight != 0) revert();
        voters[toVoter].weight = 1;
        voters[toVoter].voted = false;
    }

    /// Give a single vote to proposal $(toProposal).
    function vote(uint8 toProposal) public {
        Voter storage sender = voters[msg.sender];
        if (sender.voted || toProposal >= 4 || sender.weight == 0) revert();
        sender.voted = true;
        sender.vote = toProposal;
        proposals[toProposal] += sender.weight;
    }

    function winningProposal() public view returns (uint8 _winningProposal) {
        uint256 winningVoteCount = 0;
        for (uint8 prop = 0; prop < 4; prop++)
            if (proposals[prop] > winningVoteCount) {
                winningVoteCount = proposals[prop];
                _winningProposal = prop;
            }
    }

    function getCount() public view returns (uint[4] memory) {
        return proposals;
    }
}
```

Migrations.sol

```
pragma solidity >=0.4.17;

contract Migrations {
  address public owner;
  uint public last_completed_migration;

  modifier restricted() {
    if (msg.sender == owner) _;
  }

  function Migrations () public {
    owner = msg.sender;
  }

  function setCompleted(uint completed) public restricted {
    last_completed_migration = completed;
  }

  function upgrade(address new_address) public restricted {
    Migrations upgraded = Migrations(new_address);
    upgraded.setCompleted(last_completed_migration);
  }
}
```


VM Ware - to tab out once the mouse is captured... ctl + alt, the alt + tab

truffle.js file

```
development: {
    host: "127.0.0.1",     // Localhost (default: none)
    port: 9545,            // Standard Ethereum port (default: none)
    network_id: "*",       // Any network (default: none)
}
```

migration file

```
var Ballot = artifacts.require("Ballot");

module.exports = function(deployer) {
  deployer.deploy(Ballot);
};
```


```
truffle develop
truffle migrate --reset
```

console - CLI for interacting with contract, node APIs, etc

Linkage:

* https://www.trufflesuite.com/guides
* https://sites.tufts.edu/cbi/files/2013/01/linux_cheat_sheet.pdf


     