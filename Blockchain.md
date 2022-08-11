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

## Let'see some solidity stuff 

_Please note for every transaction we need to pay ethers for the gas(fuel) cost now it uis suggested to write a optimized code i.e. don't have unnecssary loops or if something is constant make it ```const``` declare visibilty of functions properly to have less gas cost_

ABI ![image](https://user-images.githubusercontent.com/63403330/184082482-7ad71682-417b-4f48-bce5-f6a1ebd9ca0b.png)

basically abi let u connect your smart contract with the deployed contract address (_from_ vala address) from some other external calls 

Bytecode ![image](https://user-images.githubusercontent.com/63403330/184082691-0c51609d-3701-469f-bc56-74305b5ae0a6.png)

this is what get deployed on EVM _ethereum virtual machine_ 

![image](https://user-images.githubusercontent.com/63403330/184082797-c77d6e06-34ce-4540-b906-6c0229f8ee47.png)


constructor and state variable demonstration: (please note state varaibles have refrences so they are stored on block chain unline local variables that have memory space)

![image](https://user-images.githubusercontent.com/63403330/184083021-546cb8d0-04e2-4bf7-8ccb-1a2a6e26fde8.png)


Global variables: (you can see they are predefined actually)

![image](https://user-images.githubusercontent.com/63403330/184083079-b08afb85-4215-429e-93b2-82d757bac1b0.png)

View function declares that no state (_state vars_) will be changed. Pure function declares that no state variable will be changed or read

![image](https://user-images.githubusercontent.com/63403330/184083362-50dbb1e7-2fc5-4e78-ba21-a99cfe0b95d7.png)

![image](https://user-images.githubusercontent.com/63403330/184083520-494eedb1-230d-49de-8456-9b6707f87ed8.png)


Note some stuffs like strings and struct are by default state vars so use memory with that 

![image](https://user-images.githubusercontent.com/63403330/184083703-99322864-632b-49fb-8639-ceb870de5b52.png)

here also we have such stuufs that u can read 

![image](https://user-images.githubusercontent.com/63403330/184084263-cae53410-c106-46e2-afe0-26b5ff4ea198.png)

![image](https://user-images.githubusercontent.com/63403330/184084322-9c1f3f0d-ce3b-416b-b9ed-6a92fba5d0b5.png)


State Variable Visibility in Solidity

Public means that the variable can be accessed by the contract and by other smart contracts.

Internal means that the variable can only be used with the contract it is defined in and its subclasses.

Private means that the variable can only be accessed within the contract it is defined. Trying to access it outside this contract gives a compilation error.

Function Visibility in Solidity

An external function can be accessed from other contracts or outside (like remix ide or web3 calls )

A public function can be either called internally or via an EVM message call.

An internal function can be accessed in the contract in which it is defined and in its subclasses.

A private function can only be called from the contract in which it is defined.

![image](https://user-images.githubusercontent.com/63403330/184085264-ac948b59-1575-4136-876f-b7b071cad258.png)

events are important things that get printed in blockcahin logs receipt and note, events are emitted from functions and these events logs are clearly taking permannet storage on blockcahin as they are getting printed in logs.

we have also ```indexed``` keyword here that let u help to search in logs

``` require( _mobile_no != 0, "please provide valid mobile number");```, that s how we use require keyword 

Function modeifiers act as middleware tbh (recall midddleware authetication of jwt)

// do u know when u deplpoy a contract it get's its own address which u see in _to_ of blochchain reciept,

so clearly u cn actually send ethers to ur contrract and from that u may send ethers to other contract or addrees? am i right 

![image](https://user-images.githubusercontent.com/63403330/184086550-3f0e6c85-cc46-47af-8f10-5c1326f44e2a.png)


so now there are button colors in remix ide 

Red: payable 

Blue: view, pure or state var 

yellow: simple or transactional type function


![image](https://user-images.githubusercontent.com/63403330/184086907-1ba0799a-3b41-4af3-b8af-361ef4672c8c.png)

you can make a constructor payable that means during deployment u can add ethers to ur contract 

``` 1eth = 10^18 wei```

now we will see how to send eth from contract 

send() : 2300 gas limit, and please note if u don't put require it will not return ur gas if it get failed becz gas milit is exceeded

transfer() : 2300 gas limit unlike send() it does not return anything like bool value but yes it returns ur gas cost if failed 

call(): u can set the gas limit and it retuns bool value and byte return (some data), but it does n't revert gas cost so use require

![image](https://user-images.githubusercontent.com/63403330/184089513-5018a40c-432d-471f-a071-272c8bc02ba3.png)


![image](https://user-images.githubusercontent.com/63403330/184089534-66d19f06-6d3b-4c64-8b89-3b5908550ba2.png)


Immutability in blockchain 

![image](https://user-images.githubusercontent.com/63403330/184089981-e824d5b5-0384-4a8b-9fb3-5b5023c6b169.png)


during deployment when u wanna make something const, tbh u can intialize imuutable things inline also but ya that is spefic to depployment tbh


![image](https://user-images.githubusercontent.com/63403330/184090105-01b7b35d-e9dd-4f74-aa34-53c7a19f3458.png)



?? what is this ?? 

![image](https://user-images.githubusercontent.com/63403330/184090445-01cf0f29-42df-4b82-9ea3-9f2148da861b.png) clealry u take space on blockchain so it cost some gas right.

![image](https://user-images.githubusercontent.com/63403330/184090571-8b16ce7b-a1a2-43ed-84e5-9157e8ba2ce0.png)


now in calldata (also stored in RAM only not a permanet thing), 1st of all u can use it in function i/ps argument list only and it cost less gas becz they can't eb changed 


u seee hpw beautifully things are designed it is just becz of minimiing gas since for ethereum blockchain it cost u ether u have to pay from pocket so we have such small optimizations everywhere


### Truffle tutorial 

this packaage let u compile or deploy solidity codes maybe on ganache or on test/main net 

do ```npm i truffle``` 

then ./node_modules/.bin/truffle init and do ```compile with truffle``` to get a build folder of all contracts that jave json file having abi and bytecode

now how to deploy on ganache (_local blockchain simulator_) ? using truffle 

inside migrations build a new file for  index_Bank.sol as (_do the edits in Bank.sol to include license and change compiler version) and include the content as shown, index is importtant that let u specify the compile order 

```
const Bank = artifacts.require("Bank");

module.exports = function (deployer) {
  deployer.deploy(Bank);
};
```


so u need to install ganache but ok let's skip and see on doing ```truffle migrate``` that's wht we see and yeah make sure in truffle.config file for deployment section set the port as on ur ganache GUI 

```
    // development: {
    //  host: "127.0.0.1",     // Localhost (default: none)
    //  port: 8545,            // Standard Ethereum port (default: none)
    //  network_id: "*",       // Any network (default: none)
    // },
    
 ```
    

![image](https://user-images.githubusercontent.com/63403330/184111318-948b4b81-6583-41c8-942c-7d7a3735822e.png)


do ```truffle migrate --reset``` if u do any change in .sol file else it wn't be reflected 

what's infura? let u connect with testnet or mainnet easily and let u deploy ur contract, since we have seen how truffle help us to deploy the contract on ganache it's time to see on ropsten network 

am i right so do the changes in truffle file as hwon below and understand what we did 

```
const HDWalletProvider = require('@truffle/hdwallet-provider');
mnemonic = provide it yourself



     ropsten: {
    provider: () => new HDWalletProvider(mnemonic, `https://ropsten.infura.io/v3/YOUR-PROJECT-ID`),
      network_id: 3,       // Ropsten's id
     gas: 5500000,        // Ropsten has a lower block limit than mainnet
     confirmations: 2,    // # of confirmations to wait between deployments. (default: 0)
     timeoutBlocks: 200,  // # of blocks before a deployment times out  (minimum/default: 50)
    skipDryRun: true     // Skip dry run before migrations? (default: false for public nets )
   },
    
```

see the syntaxes inside truffle file, (_have a infura url before u proceed_)



