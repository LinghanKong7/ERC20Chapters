*  approve(address spender, uint tokens)

this function approve the passed address to spend the specified amount of tokens on behalf of msg.sender.

> Beware that changing an allowance with this method brings the risk that someone may use both the old
> and the new allowance by unfortunate transaction ordering. One possible solution to mitigate this
> race condition is to first reduce the spender's allowance to 0 and set the desired value afterwards:

```javascripts
function approve(address spender, uint256 value) public returns (bool){
        _approve(msg.sender, spender, value);
        return true;
    }
```

When calling this function, the owner of the contract authorizes, or approves, the given address to withdraw instances of the token from the owner’s address.

Here, and in later snippets, you may see a variable msg . This is an implicit field provided by external applications such as wallets so that they can better interact with the contract. The Ethereum Virtual Machine (EVM) lets us use this field to store and process data given by the external application.

In this example, msg.sender is the address of the contract owner.