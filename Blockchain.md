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

getBalance

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


![image](https://user-images.githubusercontent.com/63403330/183685729-62c13b6e-3102-44ed-b875-368c33cd9148.png)


![image](https://user-images.githubusercontent.com/63403330/183685773-a9c419e4-ef82-4c9f-912c-b7587ca9cfb1.png)

see how you are notified 

now u can see full detail on etherscan 

![image](https://user-images.githubusercontent.com/63403330/183686188-bcecb13f-084d-4815-a966-a128d7f0fb04.png)

to connect this with your web-app u need abi and contract addrees correct 


```
[
	{
		"constant": true,
		"inputs": [],
		"name": "getBalance",
		"outputs": [
			{
				"name": "",
				"type": "int256"
			}
		],
		"payable": false,
		"stateMutability": "view",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"name": "amt",
				"type": "int256"
			}
		],
		"name": "withdraw",
		"outputs": [],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"constant": false,
		"inputs": [
			{
				"name": "amt",
				"type": "int256"
			}
		],
		"name": "deposit",
		"outputs": [],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "function"
	},
	{
		"inputs": [],
		"payable": false,
		"stateMutability": "nonpayable",
		"type": "constructor"
	}
]
```

so u see the abi above and clearly contract address is that from which u created the contract u can find it easily, now the idea is to conenct it with our .js app in backend and do it so how we can do ???


 _to fetch the bal_

![image](https://user-images.githubusercontent.com/63403330/183704688-0308fe84-ab6e-4d0f-bf78-e4cc4dd44039.png)



 depositing ....  
![image](https://user-images.githubusercontent.com/63403330/183689730-17d69cb5-e0d3-46a1-a821-3c0e52732a77.png)

![image](https://user-images.githubusercontent.com/63403330/183689894-0b6266a8-fcb0-48d6-806f-fe4ab5ca3b2d.png)




