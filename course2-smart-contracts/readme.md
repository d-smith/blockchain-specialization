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


## Smart Contracts Defined

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

## Processing Smart Contracts

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

## Deploying Smart Contracts


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
 * To interact with the smart contract, we'll use the smart contract address, ABI definition, and the function hashes. S

 Linkage:

 * https://medium.com/@k3no/ethereum-tokens-smart-contracts-80f639f5c46b
 * https://medium.com/all-things-ledger/decoding-the-enigma-of-bitcoin-mining-f8b2697bc4e2
 