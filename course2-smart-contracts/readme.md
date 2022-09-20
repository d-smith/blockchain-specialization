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

For currency transfer, the verification and validation, we're just checking the existence and validity of UTXOs, the balances, and the structural characteristics. When a chain is thrown open for an arbitrary decentralized application requiring trust and immutable recording, conditions to be verified and validated become application-specific. At the completion of this lesson, you will be able to define the structure of a smart contract, apply this knowledge to understand with a real contract written in Solidity language, use a web development environment Remix to invoke and interact with a smart contract. Structural and meta-level attributes of a transaction are verified at the blockchain protocol level. How were the application-specific constraints? The answer is in the critical role played by the smart contract. Smart contract work with the application-specific semantics and constraints of the transaction and verify, validates, and executes them. Most of all, since it is deployed on the blockchain, the smart contract leverages the immutable recording and trust model of the blockchain. Since a smart contract is deployed in the blockchain, it is an immutable piece of code, and once deployed, it cannot be changed. We will have to redeploy the code as a new smart contract, or somehow redirect the calls from a old contract to the new one. Smart contract can store variables in it called state variables. We could retrieve how these variables change over the blocks. 

Contract in the Ethereum blockchain has pragma directive, name of the contract, data or the state variable that define the state of the contract, collection of function to carry out the intent of a smart contract. Other items, we'll discuss in the later lessons. Identifiers representing these elements are restricted to ASCII character set. Make sure you select meaningful identifiers and follow camel case convention in naming them. We'll learn these concepts using simple contracts written in high level language called Solidity. We will use a web integrated development environment, IDE, called Remix to create, deploy, execute, and explore the working of few representative smart contracts. Welcome to Remix IDE. This is available at Remix.ethereum.org. Here is the environment that is available as a web interface. On the left side, you see the file browser, where you can see all the smart contracts that you have created. You can create a new one, and it'll have an entry here. In the middle is the editor window, where you'll type in the smart contract. At the bottom is a console or the output window. On the right side, you have the tools compile, run, settings, analysis, debugger, and support. At the bottom will be the web interface, and ability to create a smart contract will be somewhere in this middle. With all these features, Remix is indeed a one-stop environment to develop, deploy, and test a smart contract. We will examine two very simple smart contracts, greeter and one integer storage, simple storage. These two examples are modified versions of the example given in Solidity documentation. Our goal is to get an overview of the structure of a smart contract without getting into the details of the Solidity language. However, we'll explain every item in the smart contract we plan to explore. Let's look at three steps in the development of a smart contract: design, code, and test. Here is the design of the Greeter contract. This is the Hello World of smart contract. Greeter has a string variable named yourName, the constructor Greeter, a set function to set the name, and a hello function that returns a string name so that you can use it to greet the world. Here, we see the code for the Greeter contract. It begins with the pragma that provides a version number so that the compiler knows which version of Solidity this was developed in. You also see the name of the contract Greeter, the state variable yourName. Note that it is in camel notation. This is followed by functions, the constructor Greeter that initializes yourName variable, set function that sets a variable to a name supplied by the users message as a parameter, and a hello function that retrieves the name for use by the invoking application. Remix is where we test. Now, let's look at the Greeter contract. Here is a Greeter contract. At the first line, you see pragma Solidity. This provides the version of the Solidity. Then, it starts with the contract name, followed up by the data or the state variables, followed up by the functions. There are three functions here: Greeter, which is a constructor, and a set function which is setting the data variable, and then, a hello function which extracts the values of the state variable and returns it. The state variable here is yourName and it has a public visibility modifier, and the function Greeter, the constructor initializes yourName to World, and the function set initializes yourName to the name provided by the sender. Hello returns whatever value that was set in the state variable. Let's run it and see. I'm going to start by compiling it, and then, running it. When I run, I have to deploy the smart contract on a JavaScript VM. I'm going to change it to JavaScript VM, and I'm going to create it. When I create it, this is the web interface where you will see all the public variables. YourName is a public variable that's available there. Hello is a public function that is available there, and set is another public function that is available there. When I just simply say yourName, the current yourName given is World that shows up. I'm going to set the name to Buffalo. If I set the name to Buffalo and I click on yourName, yourName shows up at Buffalo. If I click on the function hello, hello will return the current yourName that happens to be Buffalo, and it will show up.


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