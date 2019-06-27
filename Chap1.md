ERC20
===

[![Version](http://img.shields.io/badge/Certik-randombytes.svg)](https://certik.org/) 
[![Version](http://img.shields.io/badge/Solidity-randombytes.svg)](https://solidity.readthedocs.io/en/v0.5.8/) 
[![Version](http://img.shields.io/badge/Ethereum-randombytes.svg)](https://www.ethereum.org/) 
[![Version](http://img.shields.io/badge/BlockChain-randombytes.svg)](https://solidity.readthedocs.io/en/v0.5.8/) 
[![Version](http://img.shields.io/badge/Cryptocurrency/ICO-randombytes.svg)](https://www.investopedia.com/terms/i/initial-coin-offering-ico.asp) 


##1. pre-request

 Before learning the ERC20, we should understand what is BlockChain, Ethereum and smart contract. 

###	-	Blockchain

Blockchain is a chain of blocks, but not in the traditional methods. By analyzing the word "Blockchain", "block" means the digital information and "chain" means public database. Therefore, we actually talk about the digital information in public database. To be more specfic, there are three main parts in blockchain:

*	Blocks store information about transaction scuh as, date, time and money amount of the most recent purchase from stores(any stores; it could be online or offline.) 
* 	Blocks store information that who are participating in transactions. For example, it could report the name and the website where the purchaser buy.
*  	Blocks store information that distinguishes them from other blocks that is using hash function to allow us to tell it apart from every other block. 

For some general informaion, a single block existing in the blockchain can store up to 1 MB of data which depends on the size of transaction. For more information of Blockchain, referencing at [IBM](https://www.ibm.com/blockchain/what-is-blockchain)

###	-	Smart Contract and solidity

A [smart contract](https://en.wikipedia.org/wiki/Smart_contract) is a computer code running on top of a blockchain containing a set of rules under which the parties to that smart contract agree to interact with each other. if the pre-defined requirements are meet, the agreement in the smart contract will automatically enforce. 
>Tips: Smart contract can only be as smart as the people coding taking into account all available information the time of coding

>While smart contracts have the potential to become legal contracts if certain conditions are met, they should not be confused with legal contracts accepted by courts and or law enforcement. However, we will probably see a fusion of legal contracts and smart contracts emerge over the next few years as the technology becomes more mature and widespread and legal standards are adopted.

#####	Solidity Smart Contract example

A contract in the sense of Solidity is a collection of code(function) and data(its state) which stay in a specifc address on the Ethereum. Let's take look a simple contract in Solidity document:

```javascripts

pragma solidity >=0.5.0 <0.7.0;

contract Coin {
    // The keyword "public" makes those variables
    // easily readable from outside.
    address public minter;
    mapping (address => uint) public balances;

    // Events allow light clients to react to
    // changes efficiently.
    event Sent(address from, address to, uint amount);

    // This is the constructor whose code is
    // run only when the contract is created.
    constructor() public {
        minter = msg.sender;
    }

    function mint(address receiver, uint amount) public {
        require(msg.sender == minter);
        require(amount < 1e60);
        balances[receiver] += amount;
    }

    function send(address receiver, uint amount) public {
        require(amount <= balances[msg.sender], "Insufficient balance.");
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```

In the above example, [Pragmas](https://solidity.readthedocs.io/en/v0.5.8/layout-of-source-files.html#pragma) are coomen instructions for compilers about how to treat the source code. the first line expresses the source code is written for solidity version 0.4.0 or anything newer that does not break functionality (up to, but not including, version 0.7.0. ) 

```javascripts
address public minter;
```

The above code declares a [state variable](https://solidity.readthedocs.io/en/v0.5.3/structure-of-a-contract.html) which are "variables whose values are permanently stored in contract storage". In this case, the state variable named minter which is publicly accessible and the variable type is address which is is a 160-bit value and do not allow any arithmetic operations.

```javascripts
mapping(address=>uint) public balances;
```

The above line of code creates a public state variable, but it is a more complex datatype. This type maps addresses to unsigned integers.

Mappings can be seen as hash tables which virtually initialized such that every possible key exists from the start and is mapped to a value whose byte-representation is all zeros

```javascripts
function balances(address _account) external view returns (uint) {
    return balances[_account];
}
```
you can use the above function to query the balance of a single account.

```javascripts
event Sent(address from, address to, uint amount);
```
The above line declares a so-called "event" which is emitted in the last line of the function send. User-interface and server applications of course can listen for those events being emitted on the blockchain without much cost. As soon as it is emitted, the listener will receive the arguments, [from], [to] and [amount] which makes the track of transactions more easily. For more information to read about the listen for this event; reference at [Solidity document](https://solidity.readthedocs.io/en/v0.5.8/introduction-to-smart-contracts.html).

```javascript
    constructor() public {
        minter = msg.sender;
    }
```
The above case is a constructor which is a special function, running during creation of the contract and cannot be called afterwards. It permanently stores the address of the person creating the contract: msg (togetehr with `tx` and `block`) is a global variable that contains some properties which allow access to the blockchain. msg.sender is always the address where the current (external) function call came from.

Finally, the functions that will actually end up with the contract and can be called by users and contracts alike are mint and send. If mint is called by anyone except the account that created the contract, nothing will happen. This is ensured by the special function require which causes all changes to be reverted if its argument evaluates to false. The second call to require ensures that there will not be too many coins, which could cause overflow errors later.

On the other hand, send can be used by anyone (who already has some of these coins) to send coins to anyone else. If you do not have enough coins to send, the require call will fail and also provide the user with an appropriate error message string


###	-	Ethereum 

Ethereum is an open source, public, blockchain-based distributed computing platform and operating system featuring smart contract (scripting) functionality. It supports a modified version of Nakamoto consensus via transaction-based state transitions.

For example, Ether is a token whose blockchain is generated by the Ethereum platform. Ether can be transferred between accounts and used to compensate participant mining nodes for computations performed.[3] Ethereum provides a decentralized virtual machine, the Ethereum Virtual Machine (EVM), which can execute scripts using an international network of public nodes.[4] The virtual machine's instruction set, in contrast to others like Bitcoin Script, is thought to be Turing-complete. "Gas", an internal transaction pricing mechanism, is used to mitigate spam and allocate resources on the network.

For more information learn about [Ethereum](https://www.ethereum.org/).

