# aumetacraftersremix

this is the public variables i set i choose to make it static just for the sake of testing

    string public tokenName = "Tokneneng";
    string public tokenSymbol = "Token";
    uint256 public totalSupply = 100000;
    address public testAddress = 0x5B38Da6a701c568545dCfcB03FcB875f56beddC4;

this is the mapping for balances

    mapping(address => uint256) public balances;

this is the constructor for balances for the total supply available

    constructor() {
        balances[msg.sender] = totalSupply;
    }

this is where the minting happens, this uses the static address instead of inputing an address manually to save time in testing, can just add a variable to the constructor and add a parameter to the function in the future for dynamic addresses 

    function mint(uint256 _value) public {
        totalSupply += _value;
        balances[msg.sender] += _value;
    }
    
this where the burning happens this also uses the static address instead of inputing an address manually to save time in testing, can just add a variable to the constructor and add a parameter to the function in the future for dynamic addresses 

    function burn(uint256 _value) public {
        require(balances[msg.sender] >= _value, "Insufficient balance");
        require(totalSupply >= _value, "Insufficient total supply");

        balances[msg.sender] -= _value;
        totalSupply -= _value;
    }
    

