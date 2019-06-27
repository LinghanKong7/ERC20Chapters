*	function totalSupply() public view returns (uint);

The next thing need to solve is that define the function. In solidity, a function declration in solidity looks like:

```javascripts
function example (string hi){

}
```
The above example is a function named example which take two parameters: a string.

>Note: It's convention (but not required) to start function parameter variable names with an underscore (_) in order to differentiate them from global variables. We'll use that convention throughout our tutorial.

In solidity, functions are public by default. This means anyone can call your contract's function and execute its code. However, it is not always desirable because the function may be more easily to attack. Thus, it is good practice to mark the functions as private by default and then only make public the function you want to expose to the world.

```javascript
uint[] numbers;

function _addToArray(uint _number) private {
  numbers.push(_number);
}

```
This means only other functions within our contract will be able to call this function and add to the numbers array.

##### Function return values function modifiers
To return a value from a function, the declaration looks like this:

```javascripts
string greeting = "What's up dog";

function sayHello() public returns (string) {
  return greeting;
}

```
Function modifiers:
The above function doesn't actually change state in Solidity — e.g. it doesn't change any values or write anything.

So in this case we could declare it as a view function, meaning it's only viewing the data but not modifying it:
```javascripts
function sayHello() public view returns (string) {
```
Solidity also contains pure functions, which means you're not even accessing any data in the app. Consider the following:

```javascripts
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
```
This function doesn't even read from the state of the app — its return value depends only on its function parameters. So in this case we would declare the function as pure.


Let's write another function which can return the total numer of tokens in existence.


```javascripts
function totalSupply() public view returns (uint256) {
        return _totalSupply;
}
```
The above function allows an instances of the contract to calculate and return the total amount of the token that exists in circulation.
references for [view](https://ethereum.stackexchange.com/questions/28898/when-to-use-view-and-pure-in-place-of-constant/28900) type;

