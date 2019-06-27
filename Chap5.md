*  function balanceOf(address tokenOwner) public view returns (uint balance);

For this function, it should handle the balance of the specifced address, and it should input a address which is to query the balance of and returns an uint256 representing the amunt owned the pass address.

```javascripts
function balanceOf(address account) public view returns (uint256) {
        return _balances[account];
    }
```

This function allows a smart contract to store and return the balance of the provided address. The function accepts an address as a parameter, so it should be known that the balance of any address is public.

