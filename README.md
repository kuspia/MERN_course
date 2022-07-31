# MERN_course

Don't see my grammar or english I am just writting this lavishly and for my understanding ok?

ok I will be referring to 

https://www.youtube.com/watch?v=BSO9C8Z-YV8&list=PLt5mNkGuWcuVbcPh9chXPtIjKwiETteea&ab_channel=6PackProgrammer this ututbe channel to make this ok??

cool so let's start

### https://www.youtube.com/watch?v=BSO9C8Z-YV8&ab_channel=6PackProgrammer All about NODEJS

First google nodejs and install it in your pc. 

Like you know we have javascript so basically you can run it in your frontend that is browser in console section right? but exactly your browser is inbuilt with some kind of JS engine like for chrome we have 
![image](https://user-images.githubusercontent.com/63403330/182020428-be763dcf-471f-4b50-9484-0b83d0f968fc.png)

so bascially nodejs do the same, it doesnot require any js engine of your browser to run js, so nodejs is a kind of server side language and you can run your code at backend. 

like see 

![image](https://user-images.githubusercontent.com/63403330/182020460-410edc9c-d1fd-4702-bad8-95d21540fe0c.png)


so see now you can open visual studio code and make a new .js file write js code in it and then using terminal you can run the commands ok ?
![image](https://user-images.githubusercontent.com/63403330/182021555-7750bb63-aa72-44eb-8dbb-4834fb09291e.png)

what is NPM (node package manager) --> bana banaya code 

use ```npm init``` to intilasize it according to your needs and then you will see a file being created k/as package.json (maintains the whole track of whole folder it records all dependecies and packages ok?)
![image](https://user-images.githubusercontent.com/63403330/182021668-e49ff020-3429-45fc-9840-fcc4c4c8bb68.png)

now do ```npm install``` you will see something will happen as it will try to install from package.json which intially don't have anything as of now, but listen u will see a package-lock.json file being created.

now as you know writing things in js from scatch might be hectic so we have pre-built packages or frameworks like express
so to install you can write ```npm install express``` and observe the changes !!

![image](https://user-images.githubusercontent.com/63403330/182021919-a9be6448-3c76-45ba-9976-a57b02c0054e.png)
![image](https://user-images.githubusercontent.com/63403330/182021937-43548263-4a7d-4a88-b30d-0dc79577e59b.png)

so basically node_modules folder have our deps and packages with their required version ok ?

NOW why we need _package-lock.json_ 

so listen express is a kind of deps but it have its own deps as per the version so to maintain everything it is necessary to store it in a very well desired manner.

to uninstall express ```npm install express```

##### Remember if you want to install all packages of some repo at once and u have package.json file just write 
```npm install```

In nodejs everything (object or function or variable) is module u should knw this !! 

like 

```
const a = 23;
```

OR 

```
const a = ()=>{
    
}
```

Module in Node.js is a simple or complex functionality organized in a single or multiple JavaScript files which can be reused throughout your Node.js.

Types of modules::

1. Transferable module or Filebase module:

see to tranfer module from one js file to other you cna use as shown ....

![image](https://user-images.githubusercontent.com/63403330/182022791-1b1f0358-f276-4e1d-a894-3619aaa44d30.png)


![image](https://user-images.githubusercontent.com/63403330/182022799-1e908089-c54d-4269-b012-ab4ff6ec4d59.png)


![image](https://user-images.githubusercontent.com/63403330/182022876-fa332d07-a9a2-4770-aa82-86a9dbc16392.png)


![image](https://user-images.githubusercontent.com/63403330/182022910-01a4878b-44b7-48ca-854b-5386fe52b9d4.png)



2. Build In module 

the one who should not be downloaded ok 




















