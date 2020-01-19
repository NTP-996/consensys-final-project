# Avoiding Common Attacks

## Integer Overflow and Underflow

Through out the EthStore contract, all math calulation are performed using SafeMath.

https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/math/SafeMath.sol

```javascript
import "openzeppelin-solidity/contracts/math/SafeMath.sol";

using SafeMath for uint256;
```
