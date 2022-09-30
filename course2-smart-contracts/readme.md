# Smart Contracts

## Smart Contract Basics


Smart contract origins

* In the first course of the specialization, blockchain basics, we discussed how proven algorithms and techniques for encryption, hashing and peer to peer networks have been creatively applied to the innovation of blockchain, a decentralized, trusted, distributed, immutable ledger. 
* The concept of the smart contract was there well before the advent of the Bitcoin. 
    * Computer scientist Nick Szabo detailed his idea of cryptocurrency Bit gold as a sort of a precursor for Bitcoin. He also outlined the concept of smart contract in his 1996 publication. In fact, Szabo coined the term smart contract more than 20 years ago. 
    * Smart contract is a centerpiece and main thrust of Ethereum blockchain. 
    
Similar technology

* Bitcoin has a script feature that includes rules and policies. 
* Linux Foundation's Hyperledger blockchain has a smart contract feature called Chaincode. The Chaincode is written in go language, and executed in a docker environment.

We'll be using [remix](remix.ethereum.org) for this course.

Learning Objectives:

* Explain the elements of a smart contract.
* Discuss the syntax and semantics of a smart contract programming language, Solidity.
* Solve a problem and design a smart contract solution.
* Use Remix development environment for building and testing a smart contract.
* Deploy a smart contract using Remix and invoke the contract from a simple web interface.

### Why Smart Contracts?

Bitcoin blockchain is primarily meant for transferring digital currency. Bitcoin added a simple conditional transfer of value through an embedded script. Recall from the blockchain basics course, course one, that this is a conditional feature that was bootstrapped as a softfork in Bitcoin. The script was limited in its capabilities. It enabled simple conditional transfers. After Bitcoin, evolved Ethereum. 

The founders of Ethereum developed smart contract keeping Nick Szabo's idea of a smart contract from over 20 years ago in mind. A significant contribution of Ethereum is a working smart contract layer that supports any arbitrary code execution over the blockchain. Smart contract allows for user-defined operations of arbitrary complexity. This feature enhances the capability of Ethereum blockchain to be a powerful decentralized computing system.

 Why would you want to transfer currency? Cryptocurrencies such as Bitcoin, enable transfer of values such as money or currency from peer-to-peer without any intermediaries. For what? To gift somebody, to buy a product, maybe even renew a driver's license, or send flowers to someone. Let us elaborate further. We may want the gift to be delivered on a certain date. Buy a product of a particular color and quality. We may need some credentials verified for renewing the license. And we may need a specific tulip bouquet to be delivered to Buffalo. 
 
 This introduces conditions, rules, policies beyond that of which a simple money transfer cryptocurrency protocols can handle. Smart contract addresses this need for application specific validation for blockchain applications. Smart contract has some advantages including, a smart contract facilitates transaction for transfer of assets other than value or cryptocurrency. 
 
 Smart contract allows specification of rules for an operation on the blockchain. It facilitates implementation of policies for transfer of assets in a decentralized network. It also adds programmability and intelligence to the blockchain. 
 
 The smart contract represents a business logic layer, with the actual logic coded in a special high level language. A smart contract embeds function that can be invoked by messages that are like function calls. These messages and the input parameters for a single message are specified in a transaction. 
 
 Let us compare Bitcoin transaction and a smart contract transaction. As you can see in Bitcoin, all the transactions are about send value. In the case of a blockchain that supports a smart contract, a transaction could embed a function implemented by a smart contract. Here we have a voting smart contract. The functions are ValidateVoter, Vote, Count, Declare Winner. Smart contract provides a layer of computation logic that can be executed on the blockchain, thus availing the features enabled by the blockchain framework. 
 
 Recall the layers of a decentralized application that we discussed in course one, module two. Observe that smart contract providing the application framework for a domain application. For example, consider home mortgage application. Smart contract could embed all the business logic and the intelligence for the rules and regulation, to allow for automatic computation and initiation of operation. How might this be different from existing systems? You may ask. Here, all the operations are transparent and are recorded on the blockchain. Customers can directly access the tools without an intermediary like a bank. It is like the ATM for mortgage initiation. You are holding the assets, it's therefore an intermediary. 
 
 Now that we have reviewed the advantages of a smart contract, let's look at what problem or problems a smart contract can solve. Typically, currency transfer is used to buy a service, a product, or a utility from a person or a business. There may be other conditions besides availability of funds while executing a transaction. For example, a business transaction may involve rules, policies, laws, regulations and governing contexts. Smart contract allows for these other real world constraints to be realized on a blockchain, thus a smart contract enables a wide variety of decentralized application of arbitrary complexity to be implemented on the blockchain. This can run the spectrum from supply chains to disaster recovery. It is likely many of the applications for the blockchain technology have not yet been conceived. It is predicted that online shopping will overtake retail shopping for the first time this holiday season, 2017-2018. Some couldn't have even imagined online shopping, mobile application or Uber 20 years ago. 
 
 Smart contract is ushering the next generation blockchain that goes beyond the transfer of value into a visionary realm. Smart contract allows for implementation of rules, policies and with the help of blockchain, supports the methods for governance and provenance.

 Linkage

 * http://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart_contracts_2.html
 * https://blockgeeks.com/guides/solidity/
 * https://remix-ide.readthedocs.io/en/latest/


### Smart Contracts Defined

For currency transfer, the verification and validation, we're just checking the existence and validity of UTXOs, the balances, and the structural characteristics. When a chain is thrown open for an arbitrary decentralized application requiring trust and immutable recording, conditions to be verified and validated become application-specific.

Structural and meta-level attributes of a transaction are verified at the blockchain protocol level. Smart contract work with the application-specific semantics and constraints of the transaction and verify, validates, and executes them. Most of all, since it is deployed on the blockchain, the smart contract leverages the immutable recording and trust model of the blockchain. Since a smart contract is deployed in the blockchain, it is an immutable piece of code, and once deployed, it cannot be changed. 

Smart contract can store variables in it called state variables. We could retrieve how these variables change over the blocks. 

Contract in the Ethereum blockchain has pragma directive, name of the contract, data or the state variable that define the state of the contract, collection of function to carry out the intent of a smart contract. 




```
    pragma solidity >=0.4.0;

    contract Greeter {
        string public yourName;

        constructor()  {
            yourName = "World";
        }

        function set(string memory name ) public {
            yourName = name;
        }

        function hello() public view returns (string memory)  {
            return yourName;
        }
    }

```

Linkage:

* http://solidity.readthedocs.io/en/develop/structure-of-a-contract.html
* http://solidity.readthedocs.io/en/develop/introduction-to-smart-contracts.html

### Processing Smart Contracts

A smart contract can be created, on behalf of an externally owned account, by application programmatically from the command-line interface and by a script of commands from high level applications and user interface or UI. It can also be created from inside a smart contract.

We need an address for the smart contract to deploy it and invoke its functions.

* The address is computed by hashing the account number of externally owned account UI and the nonce. 

A contract needs to be compiled. Various artifacts are generated including; the bytecode for deploying the contract, and the Application Binary Interface, ABI for the application that smart contract interact with a deployed bytecode. 

* Remix compiler script generates many artifacts in one shot. You can view these items generated by clicking on the Compile button, and then the Details button just below the Compile button. A pop-up screen appears with many details. 
* Some of the artifacts generated by the Remix smart contract compile process and their use. 
    * ABI, Application Binary Interface, the interface schema for a transaction to invoke functions on the smart contract instance bytecode. 
    * Contract bytecode, this is the bytecode that is executed for instantiating a smart contract on the EVM. Think of it like executing a constructor of a smart contract to create an object. 
    * WebDeploy script, this as two items; json script to web application to invoke smart contract function, script for programmatically deploying a smart contract from a web application. 
    * Gas estimates, this provides a gas estimates for deploying the smart contract and for the function invocation. 
    * Function hashes, first four byte of the function signatures to facilitate function invocation by a transaction. 
    * Instance bytecode, the bytecode of the smart contract instance. We will learn more about these and how to use them in building blockchain application in the upcoming lessons. 
    
Summarizing, Remix solidity compiler generate several artifacts as discussed. Here are some important ones: name of the contract, bytecode executed for the contract creation on the EVM, ABI, Application Binary Interface, details functions, parameters and return values, Web3 deploy module that provide the script for invoking the smart contract from web application, gas estimates for execution of a function, actual run-time bytecode of the smart contract.

Linkage:

* http://ethdocs.org/en/latest/contracts-and-transactions/account-types-gas-and-transactions.html

### Deploying Smart Contracts


Let us start by getting into the smart contract deployment process. 
* smart contract solution is written in high-level language and compiled bytecode. An ABI is also generated for high-level language application. Example, Web Apps to interact with the binary smart contract. 
* EVM provides execution environment for a smart contract bytecode. The smart contract requires an address for itself so that transaction can target it for invocation of its function. The contract address is generated by hashing the sender's account address and its nonce. 
* A unique target account is reserved for smart contract creation and deployment. 
    * Target account zero. If a target's address is zero or null, it is meant for creating a new smart contract using its payload feed. 
    * The payload of a transaction contains the bytecode for the smart contract. This code is executed as a part of the transaction execution to instantiate the bytecode for the actual smart contract. Similar to how a constructor creates an object, the execution of a smart contract creation transaction results in the deployment of this smart contract code on the EVM. It is permanently stored in the EVM for future invocation. 
    * This transaction goes through all the regular verification and validation specified in the etherium blockchain protocol. Block creation, transaction confirmation by the full nodes deploys a the same contract on all the nodes. This provides consistent execution when the regular transaction with function messages are invoked on the smart contract. 
    
   There are many other approaches for deploying this smart contract. They can be deployed from Remix IDE, another smart contract, a command line interface, another high-level language application or Web application. 
   
   Remix IDE Deployment Process
   
 * You enter the smart contract code in the Remix IDE and compile. 
 * For the ease of deployment, Remix provides us with the Web3 deployment script which contains a bytecode. Application Binary Interface, ABI, and account detail. 
 * To deploy the smart contract, we could just execute the script. Once the deployment is done, the address is generated by hashing creator's account number and nonce. 
 * To interact with the smart contract, we'll use the smart contract address, ABI definition, and the function hashes.

 Linkage:

 * https://medium.com/@k3no/ethereum-tokens-smart-contracts-80f639f5c46b
 * https://medium.com/all-things-ledger/decoding-the-enigma-of-bitcoin-mining-f8b2697bc4e2

## Solidity

Learning objectives

* Explain basic data types in Solidity language.
* Explain the use of access modifier “public.”
* Illustrate the basic definition of functions.
* Apply the basic data types and functions in constructing a smart contract.

### Structure

Solidity is a high level language
that is a combination of JavaScript, Java, and C++. It is specially designed to
write smart contracts and to target the Ethereum Virtual Machine. 

Recall from our course one that
the format of a smart contract is like the class definition in
the object-oriented programming style. 

Here is am ore detailed
structure of a smart contract. 

* Data or state variables, functions, there
are several types of functions allowed. 
    * Constructor, default or user-specified,
only one, meaning it cannot be overloaded. 
    * Fallback function, there's a powerful
feature of an anonymous function that we'll discuss in later courses. 
    * View functions, pure functions,
no state change, it computes under terms of value,
example math functions. 
    * Public functions, accessible from outside, two transactions,
state changes recorded on the blockchain. 
    * Private function,
accessible only with the current contract. 
    * Internal function, accessible inside the
current contract and inherited contracts. 
    * External functions can be accessed
only from outside the smart contract.
 User defined types in struct and enums.
  Modifiers and, finally, events. 
  Besides its explicit content,

a smart contract can also inherit from other smart contract,
as shown in the following example. 

Function definitions
are similar to functions in any other high level language. 

* Function header, followed by the code,
within curly brackets. 
* Function code contains the local data and statements to process the data and
return the results of processing. 
* Function header can be as simple
as an anonymous noname function to a complex function header
loaded with a lot of details. 

Here is more explanation of each of
the items of the function header. 

* Function is a keyword at
the beginning of all functions.
* Parameters are any number of pairs
type identifier, example, UInt count. 
* returnParameters, return
values can be specified as pair type identifier or just type. 
    * When only type is specified, it has to be explicitly returned
using a return statement. 
    * If type and identifier are specified
in the return statement, any statechain that happens to the identifier within
the function is automatically returned. 
    * Any number of values can be returned, unlike common programming languages
that allow only one return value. For example, multiple variables,
age and gender, can be assigned return values
from a function getAgeGender. 

Linkage:

* https://blockonomi.com/solidity-guide/
* https://www.youtube.com/watch?v=KkN1O8TChbM
* https://www.youtube.com/watch?v=xWKq86PWG0o

### Basic Data Types and Structure

Solidity supports many of the basic types of a high-level language. 
Default modifier is private. You explicitly state the public modifier, if that is what is intended. 
For every data declared public, accessor or getter function is automatically provided. 

The common statements available in any high-level language are available in solidity with very little variation. Assignment statement, if-else, why, for, etcetera.

 
 The bidder smart contract design is shown as a class diagram. It has three items; name of the contract, the data or states, the functions. The first version of the bidder contract, we add the data. The next thing that we want to do is look at the bidder data, and only the data. 
 
 First version:

 ```
 pragma solidity ^0.4.0; 

contract Bidder {
    string public name;
    uint public bidAmount = 20000;
    bool public eligible;
    uint constant minBid = 1000;
}
```

Next add the functions. Second version:

```
pragma solidity ^0.4.0; 

contract Bidder {
    string public name;
    uint public bidAmount = 20000;
    bool public eligible;
    uint constant minBid = 1000;

    function setName(string nm) public {
        name = nm;
    }

    function setBidAmount(uint amt) public {
        bidAmount = amt;
    }

    function determineBidElegibility() public {
        if(bidAmount >= minBid) eligible = true;
        else eligible = false;
    }
}
```

Linkage:

* https://solidity.readthedocs.io/en/v0.4.24/frequently-asked-questions.html
* http://solidity.readthedocs.io/en/develop/types.html


### Specific Data Types
 
 * Address is a special Solidity define composite data type. It can hold a 20-byte ethereum address. Recall address is a reference address to access a smart contract. Address data structure also contains the balance of the account in Wei. It also supports a function transfer, to transfer a value to a specific address. 
 * Mapping is a very versatile data structure that is similar to a key value store, it also can be thought of as a hash table. The key is typically a secure hash of a simple Solidity data type such as address and the value in key-value pair can be any arbitrary type. 
 * Message is a complex data type specific to smart contract. It represents the call that can be used to invoke a function of a smart contract. It supports many attributes of which we are interested in two of them now, msg.sender that holds the address of the sender, msg.value that has the value in Wei sent by the sender. 
 
 

 The coin contract

 ```
 pragma solidity ^0.4.0; 

contract Coin {
    address public minter;
    mapping (address => uint) public balances;

    event Sent(address from, address to, uint amount);

    function Coin() public {
        minter = msg.sender;
    }

    function mint(address receiver, uint amount)  public {
        if(msg.sender != minter) return;
        balances[receiver] += amount;
    }

    function send(address receiver, uint amount) public {
        if(balances[msg.sender] < amount ) return;
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        Sent(msg.sender, receiver, amount);
    }
} 
```

From the compiler:

```

 from solidity:
contracts/Coin.sol:9:5: Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function Coin() public {
    ^ (Relevant source part starts here and spans across multiple lines).

    from solidity:
contracts/Coin.sol:22:9: Warning: Invoking events without "emit" prefix is deprecated.
        Sent(msg.sender, receiver, amount);
        ^--------------------------------^
```

Fixed:

```
pragma solidity ^0.4.0; 

contract Coin {
    address public minter;
    mapping (address => uint) public balances;

    event Sent(address from, address to, uint amount);

    constructor() public {
        minter = msg.sender;
    }

    function mint(address receiver, uint amount)  public {
        if(msg.sender != minter) return;
        balances[receiver] += amount;
    }

    function send(address receiver, uint amount) public {
        if(balances[msg.sender] < amount ) return;
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
} 
```

And the latest example:

```
pragma solidity ^0.8.4;
contract Coin {
    address public minter;
    mapping (address => uint) public balances;
    event Sent(address from, address to, uint amount);

    constructor() {
        minter = msg.sender;
    }

    function mint(address receiver, uint amount) public {
        require(msg.sender == minter);
        balances[receiver] += amount;
    }

    error InsufficientBalance(uint requested, uint available);

    function send(address receiver, uint amount) public {
        if (amount > balances[msg.sender])
            revert InsufficientBalance({
                requested: amount,
                available: balances[msg.sender]
            });
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```

Linkage:

* https://www.youtube.com/watch?v=8UhO3IKApSg
* http://solidity.readthedocs.io/en/develop/units-and-global-variables.html
* https://ethereumbuilders.gitbooks.io/guide/content/en/solidity_tutorials.html


### Data Structures

Struct

* Struct is a composite data type of a group of related data that can be referenced by a single, meaningful, collective name. Individual elements of the struct can be accessed using the dot notation. 

Ballot Smart Contract



```
pragma solidity ^0.4.0; 


contract Ballot {

    struct Voter {
        uint weight;
        bool voted;
        uint8 vote;
    }

    struct Proposal {
        uint voteCount;
    }

    address chairperson;
    mapping(address => Voter) voters;
    Proposal[] proposals;

    constructor(uint8 _numProposals) public {
        chairperson = msg.sender;
        voters[chairperson].weight = 2;
        proposals.length = _numProposals;
    }

    function register(address toVoter) public {
        if(msg.sender != chairperson || voters[toVoter].voted) return;
        voters[toVoter].weight = 1;
        voters[toVoter].voted = false;
    }

    function vote(uint8 toProposal) public {
        Voter storage sender = voters[msg.sender];
        if(sender.voted || toProposal >= proposals.length) return;
        sender.voted = true;
        sender.vote = toProposal;
        proposals[toProposal].voteCount += sender.weight;
    }

    function winningProposal() public constant returns (uint _winningProposal) {
        uint256 winningVoteCount = 0;
        for(uint p=0; p < proposals.length; p++) {
            if (proposals[p].voteCount > winningVoteCount) {
                winningVoteCount = proposals[p].voteCount;
                _winningProposal = p;
            }
        }
    }
}
```


Time

* In a blockchain application, all the participants and nodes have to synchronize to one universal time. For this purpose, blockchain proposals include a time server that serves the Unix Epoch time or time since January 1st 1970 in seconds. 
* This time is used in timestamping the block time. When a block is added to the blockchain, all the transaction confirmed by the block also have the same block time as their confirmation time. 
* A variable called "Now" defined by solidity, returns the block timestamp. This variable is often used for evaluating time related conditions. 
* The now variable in a function is not the time at which function transaction was initiated, but it is the time when it was confirmed. 
* Time is defined as unit time; seconds, minutes, hours, days, weeks and years.

Enum data types

* Enum or enumerator data type, allows for user defined data types with limited set of meaningful values. It is mostly used for internal use and are not supported currently at the ABI level of solidity. However, it serves an important purpose of defining states or phases of a smart contract. 

```
pragma solidity ^0.4.0;
contract StateTransV2 {

    enum Stage {Init, Reg, Vote, Done}
    Stage public stage;
    uint startTime;
    uint public timeNow;
    
     constructor() public {
       stage = Stage.Init;
      startTime = now;
    }
    
    //Assuming the Stage change has to be enacted APPROX every 1 mintute
    //timeNow variable is defined for underatanding the process, you can simply use 
    // "now" Solidity defined varaible 
    // Of course, time duration for the Stages may depend on your application
    //1 minutes is set to illustrate the working 
    function advanceState () public  {
        timeNow = now;
        if (timeNow > (startTime + 10 seconds)) {
        startTime = timeNow;  
        if (stage == Stage.Init) {stage = Stage.Reg; return;}
        if (stage == Stage.Reg) {stage = Stage.Vote; return;}
        if (stage == Stage.Vote) {stage = Stage.Done; return;}
        return;
        }
    }
}
```

Linkage

* http://solidity.readthedocs.io/en/develop/types.html
* http://solidity.readthedocs.io/en/develop/types.html#enums
* https://beta.techcrunch.com/2018/02/24/liquid-democracy-uses-blockchain/
