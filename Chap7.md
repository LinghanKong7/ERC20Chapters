*  transfer(address to, uint tokens)
This function is to transfer token for a specified addres and it needs two parameters. 

###  Requirements:
* - `recipient` cannot be the zero address.
* - the caller must have a balance of at least `amount`.

```javascripts
function transfer(address recipient, uint256 amount) public returns (bool) {
        _transfer(msg.sender, recipient, amount);
        return true;
    }
```
This function lets the owner of the contract send a given amount of the token to another address just like a conventional cryptocurrency transaction.
