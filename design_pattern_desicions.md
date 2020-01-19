## Application Design 

# Main
```javascript
    Struct IParticipant{
        address  account ;
        String fullName;
        String email;
        unit numberOfSession;
        uint deviation;
    }
    Mapping(address=>IParticipant) public participants
    address[] public sessions
    address public admin
    uint public nParticipants
    address[] public iParticipants
```
# Main function
```javascript
addSession()
register()
increNumSessionOfParticipant()
getDeviation()
setDeviation()
updateParticipantInfo()
getAccountOfParicipants()
```

# Session
```javascript
address public mainContract
Main Maincontract
uint proposedPrice;
address public creator
enum State {CREATED,ONGOING,CLOSED,FINISHED,STOPPED}
State  public state
uint public timeStop
uint public timeout
string public name
string public description
string public image 
address[] public iParticipants
mapping(address => uint) public pricings
uint public proposedPrice
uint public nParticipants
```

# Session function
```javascript
constructor Session()
modifier validState()
modifier onlyAdmin()
modifier validRegister()
startSession()
closeSession()
stopSession()
priceProduct()
calulateFinalPrice()
updateProduct()
```