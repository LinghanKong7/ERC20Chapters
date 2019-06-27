##2. What is ERC20 Token Standard
The ERC20 token standard describes the functions and events that an Ethereum token contract has to implement.

##3. ERC20 Token Standard Interface

Following is an interface contract declaring the required functions and events to meet the ERC20 standard:


```javascript
contract ERC20Interface {
    function totalSupply() public view returns (uint);
    function balanceOf(address tokenOwner) public view returns (uint balance);
    function allowance(address tokenOwner, address spender) public view returns (uint remaining);
    function transfer(address to, uint tokens) public returns (bool success);
    function approve(address spender, uint tokens) public returns (bool success);
    function transferFrom(address from, address to, uint tokens) public returns (bool success);

    event Transfer(address indexed from, address indexed to, uint tokens);
    event Approval(address indexed tokenOwner, address indexed spender, uint tokens);
}
```
We will use the above ERC20interface to create our own token and there will be more details come out in next tutorials.