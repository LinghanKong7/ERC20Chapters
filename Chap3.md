Firstly, we need to understand some of the concepts which will be useful in wirtting your own token.

There are different Visibility in solidity and there are differentiate among them. People can use them by defining new variable or function such as, `address private owner`

*	Public functions are part of the contract interface and can be either called internally or via messages. For public state variables, an automatic getter function (see below) is generated.
*	external:	 External functions are part of the contract interface, which means they can be called from other contracts and via transactions. An external function f cannot be called internally (i.e. f() does not work, but `this.f()` works). External functions are sometimes more efficient when they receive large arrays of data.
*	internal:	 Those functions and state variables can only be accessed internally (i.e. from within the current contract or contracts deriving from it), without using `this`.
* 	private: Private functions and state variables are only visible for the contract they are defined in and not in derived contracts.

There is another thing we need to learn which is `Mapping`

Mappping types are declared as `mapping(_KeyType => _ValueType)`. Here `_KeyType` can be almost any type except for a mapping, a dynamically sized array, a contract, an enum and a struct. `_ValueType` can actually be any type, including mappings.

Mappings can be seen as [hash atbles](https://en.wikipedia.org/wiki/Hash_table) which are virtually initialized such that every possible key exists and is mapped to a value whose byte-representation is all zeros: a type’s default value. The similarity ends here, though: The key data is not actually stored in a mapping, only its keccak256 hash used to look up the value.

example of mapping 
`mapping (uint256 => CampaignData) campaigns`

In the above example, uint256 is the `_keytype` and the campaignData is the `_valueType`. `CampaignData` is a struct.

`var campaign = campaigns[nextCampaignId];`
In this line, `nextCampaignId` is mapped as the `KeyType`, and the new `campaign` struct is the `_valueType`.


In the example, the name of mapping type is example, and it map

Try yourself:
In this example, there should be a mapping for balanacs for each account which should be public, another mapping for owner of account approves the transfer of an amount to another account wihch also should be public and an unsigned integers for store.


```javascripts
contract ERC20{

    mapping (address => uint256) public _balances;

    mapping (address => mapping (address => uint256)) private _allowances;

    uint256 public _totalSupply;

}
```
