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
 * http://remix.readthedocs.io/en/latest/

 