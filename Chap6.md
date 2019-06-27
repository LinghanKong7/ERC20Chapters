*  function allowance(address tokenOwner, address spender) public view returns (uint remaining);

The next function is to check the amount of tokens that an owner allowed to a spender.

```javascripts
function allowance(address owner, address spender) public view returns (uint256) {
        return _allowances[owner][spender];
    }
```

this function is to check the amount of tokens that an owner allowed to a spender. There are two variables "owner": address The address which owns the funds and "spender": address The address which will spend the funds. It returns A uint256 specifying the amount of tokens still available for the spender.
