so listen 

```
pragma solidity 0.4.25;
contract Bank 
{
    int bal ;
    constructor() public 
    {
        bal = 1 ;
    }
    function getBalance () view public returns(int)
    {
        return bal ;
    }
    function withdraw ( int amt ) public
    { 

        bal = bal - amt ;
    }
       function deposit ( int amt ) public
    {

        bal = bal + amt ;
    }
}
```

on remix IDE u can run bank content 
so basiclally 
1st of all we build a contract 
which should be deployed 
now u can deploy it on 
main-net or test-net or even local-vm 
1st compile bank.sol by choosing the compiler as 0.4.25 
now u should deploy the contract and u will be charged some gas 
after that u can use deposit, withdraw, or getBalance and u will be charge some gas since u are doing the transactions 
and yeah every transations will have information as shown: (deposit)
```
status	true Transaction mined and execution succeed
transaction hash	0x8cc2c45235873a7350ae45b2f5844ae7736943799b10dbb8fbfb5df538793b1c
from	0x5B38Da6a701c568545dCfcB03FcB875f56beddC4 // this was local vm tbh having 100 ethers intially on remix ide
to	Bank.deposit(int256) 0x7EF2e0048f5bAeDe046f6BF797943daF4ED8CB47
gas	30428 gas
transaction cost	26459 gas 
execution cost	26459 gas 
input	0xf04...0000c
decoded input	{
	"int256 amt": "12"
}
decoded output	{}
logs	[]
val	0 wei
```

getbal 

```
from	0x5B38Da6a701c568545dCfcB03FcB875f56beddC4
to	Bank.getBalance() 0x7EF2e0048f5bAeDe046f6BF797943daF4ED8CB47
execution cost	23366 gas (Cost only applies when called by a contract)
input	0x120...65fe0
decoded input	{}
decoded output	{
	"0": "int256: 25"
}
logs	[]
```
now you see how beautifull transactions are made for deploying or calling of methods of your smart contract 

now let's run it on metamask account so for that just change your environment and choose it.
