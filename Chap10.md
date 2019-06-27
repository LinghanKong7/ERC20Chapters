In the last step, Create your own token contract based on the previous function we write. 

it should include different public variables such as, name, decimals, symbol and initialBalance and create a constuctor. Then, you can run your code in our IDE.

```javascripts
contract Certikoin is ERC20 { // CHANGE THIS. Update the contract name.

    /* Public variables of the token */

    string public name;                   // Token Name
    uint8 public decimals;                // How many decimals to show. To be standard complicant keep it 18
    string public symbol;                 // An identifier: eg SBX, XPR etc..
    uint initialBalance= 10;//1000000000000000000*1000000; // 1M tokens
    address public owner = msg.sender;
    // This is a constructor function 
    // which means the following function name has to match the contract name declared above
    constructor () public{
        name = "Certikoin";                                   // Set the name for display purposes (CHANGE THIS)
        decimals = 18;                                               // Amount of decimals for display purposes (CHANGE THIS)
        _totalSupply += initialBalance;
        symbol = "CTK";                                             // Set the symbol for display purposes (CHANGE THIS)
        _balances[owner]=initialBalance;
    }
}
```