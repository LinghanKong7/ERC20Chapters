*  function transferFrom(address from, address to, uint tokens)

This function transfer tokens from one address to anotehr and it will need a "from" address, "to" address and a "value" which is uint256.

```javascripts
function transferFrom(address sender, address recipient, uint256 amount) public returns (bool) {
        _transfer(sender, recipient, amount);
        _approve(sender, msg.sender, _allowances[sender][msg.sender].sub(amount));
        return true;
    }
```

This function allows a smart contract to automate the transfer process and send a given amount of the token on behalf of the owner.

Seeing this might raise a few eyebrows. One may question why we need both transfer() and transferFrom() functions.

Consider transferring money to pay a bill. It’s extremely common to send money manually by taking the time to write a check and mail it to pay the bill off. This is like using transfer() : you’re doing the money transfer process yourself, without the help of another party.

In another situation, you could set up automatic bill pay with your bank. This is like using transferFrom() : your bank’s machines send money to pay off the bill on your behalf, automatically. With this function, a contract can send a certain amount of the token to another address on your behalf, without your intervention.