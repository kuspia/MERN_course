# NODEJS

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

now do ```npm install``` OR ```npm i``` you will see something will happen as it will try to install from package.json which intially don't have anything as of now, but listen u will see a package-lock.json file being created.

now as you know writing things in js from scatch might be hectic so we have pre-built packages or frameworks like ```express```
so to install you can write ```npm install express``` OR ```npm i express``` and observe the changes !!

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

see to tranfer module from one js file to other you can use as shown ....

![image](https://user-images.githubusercontent.com/63403330/182022791-1b1f0358-f276-4e1d-a894-3619aaa44d30.png)


![image](https://user-images.githubusercontent.com/63403330/182022799-1e908089-c54d-4269-b012-ab4ff6ec4d59.png)


![image](https://user-images.githubusercontent.com/63403330/182022876-fa332d07-a9a2-4770-aa82-86a9dbc16392.png)


![image](https://user-images.githubusercontent.com/63403330/182022910-01a4878b-44b7-48ca-854b-5386fe52b9d4.png)



2. Build In module (https://nodejs.org/api/)

the one who should not be downloaded ok 

like 

![image](https://user-images.githubusercontent.com/63403330/182023302-2625f689-3731-4d5f-a7a9-5d7602e6026d.png)

see one more way of importing readFile from fs and notice now we don't need to use ```fs.``` ok?

![image](https://user-images.githubusercontent.com/63403330/182023785-9aa7843f-b7f7-4aa9-96aa-73830b66a073.png)


now let's say we have a file and you wanna to read something so you can do like above but that will buffered so left to callback function u can provide options too 
as shown,

![image](https://user-images.githubusercontent.com/63403330/182023925-a6fffb26-153f-4e9b-881c-7a28480128a9.png)

now what is ```ASnchronous thing??? ``` above is async. actually see below image 

![image](https://user-images.githubusercontent.com/63403330/182023973-83181b09-fb61-4c7c-a22b-0399da3ca3c6.png)

It don't want the rest things written below to be waited hence we say it is async. now to avoid it u can use it as shown below. A callback is a function which is called when a task is completed, thus helps in preventing any kind of blocking and a callback function allows other code to run in the meantime. Callback is called when task get completed and is asynchronous equivalent for a function.

![image](https://user-images.githubusercontent.com/63403330/182024195-d98e0a88-31a6-4465-a5de-d06accc547d7.png)

![image](https://user-images.githubusercontent.com/63403330/182024334-f6702ad0-6e47-4dba-b9dd-4435f3387cbd.png)

similarly ```path```, ```os```, ```http``` is also a kind of important module u knw and u should knw tht i hope !!


3. Third party module is also a kinda important 

![image](https://user-images.githubusercontent.com/63403330/182024551-58d9929d-026c-4d68-8c25-d8ea3ab9219e.png)

this will use nodemon for any project gloablly and nodemon is lilbit more intresting u knw right !!
![image](https://user-images.githubusercontent.com/63403330/182024670-338d65bb-5740-4cb5-9a1c-fc2d1f0e275d.png)


#### Let's see how we can create server and what is request or response and these stuffs in details 

So basically we will explore ```http``` module of nodejs to illustate the things 

> server sends the response while browser actually request it pls rememeber this concept so when u type google.com u actually request it from ur browser and what you see in browser is response from the server 
> same concept apply on localhost so here u try to request something like localhost:3000/about so u re requesting about from the browser and what u will see after that will be actually response send from the server (nodejs) {http or express} !!

Now ```http.createServer()```  have the follwing def^n

![image](https://user-images.githubusercontent.com/63403330/182038130-f264a211-d8d4-4356-9b70-03d64546631c.png)

notice ```?``` says you may specify it else it will be taken as undefined 

now we define a callback function which is called when server is created (you know that's wht callback is meant for, when task is done it should be called) inside it as shown below to have access to request done by browser (_to know the url or maybe method(like it is get or post) etc_) and hence respond to it via server using reponse variable of callback function. 

```
const http = require('http')
const s = http.createServer( (req , rep)=>{
    rep.end("HI")
    //rep.end("Dgdsgsd") make sure u comment it as u can't do it more than once ok in case u have multiple rep.end() so u can use return or make sure only one is executed 
} )
s.listen(3000  , ()=> {} )

const ss = http.createServer()
console.log(ss)
```
> Note s.listen() have many arguments that you can see and tbh all of them are optional also and ss is just a http server created as shown right?
> you can also send rep.end(home) where home is whole html code that is read from some home.html file as shown 

![image](https://user-images.githubusercontent.com/63403330/182039542-26157e76-a4c5-48b3-a83e-2c9647735129.png)

Now let me tell u more about package.json file 

```
{
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1", 
        "start": "node i.js" 
        
  },
}

// you may specify more like start as per ur need if required
```

now if u do ```npm start``` it will execute start script command written inside package.json file and _pls note it is mandatory when deploying on heroku_  

> The main field is a module (u knw in nodejs everything ur .js file or object or var everything is referred as module which may be simple or complex) ID that is the primary entry point to your program. That is, if your package is named foo, and a user installs it, and then does require("foo"), then your main module's exports object will be returned.


### To deploy the above on heroku 

install CLI and follow heroku instructions

make a ```Procfile``` with the follwing content:


```
web: node i.js
```



remember to set port as ```process.env.PORT``` and hostname as nothing (since it is optional u knw that in http or express both) or website URL 

u may set PORT value here as u want 
![image](https://user-images.githubusercontent.com/63403330/182039804-79667ed5-f7b5-4cde-86f6-53e0860de8dc.png)


Ok !! man now its time to see three techinal terms ```cache``` ```cookies``` and ```sessions```

Let's see the easiset one !!

![image](https://user-images.githubusercontent.com/63403330/182320716-6e1aa2f2-fe11-46c7-b4ca-e31bc6122b16.png)

Let's see cookies !!

![image](https://user-images.githubusercontent.com/63403330/182320852-f2bc5261-7692-47b8-966c-565709465882.png)

now u can see cache is something tht browser itself stores for faster loads and easy access however cookies are something that server stores on the browser like ```session id``` in form of hashed text and u knw many clients can interact to server hence to manage all cleints there is need of creating sessions so that server can recognize the browser or client.

Please note any senstive information is stored on server side while managing the session and it is never stored in browser, and typically cookies are hashed and they just help the server to recognize the browser by sending (request with cookies attached to it) nothing else so u can never know the password or anything from inspecting of browser.

but wait before tht u should knw we also have concept of local storgae like you might have seen code being retirved from your local storgae.

> A session will contain some unique data about that client to allow the server to keep track of the user's state. In session-based authentication, the user's state is stored in the server's memory or a database.

![image](https://user-images.githubusercontent.com/63403330/182339372-3f42ddd6-70b1-4ae3-92e9-2b97b31fd0f2.png)

![image](https://user-images.githubusercontent.com/63403330/182340800-4eea4e5c-9be9-4ae1-b125-18892463e6c7.png)

so let's start !!

```
const express = require("express")
const bodyparser = require("body-parser")
const cookieparser = require("cookie-parser")
const session = require("express-session")
const app = express()
app.use(bodyparser.json());
app.use(bodyparser.urlencoded({extended:true}))
app.use(cookieparser())
app.use(session({ secret: "dsgg"  , resave: false }))
app.get("/set" , (req , res)=>{
if( req.session.count) req.session.count++    
else req.session.count = 1
console.log(req.session.count )
console.log(req.session)
res.send("" + req.session.count )
})
app.get("/" , (req , res)=>{
res.send("DGSg")
})
app.listen(3000 ,()=>{
})
```
now on runnnig it and hitting set api 

![image](https://user-images.githubusercontent.com/63403330/182344145-310e4314-3a5b-4d2f-a9a1-a090acbf4fce.png)


So u see how beautifully we are not losing count and u may change tab it will be recorded.

![image](https://user-images.githubusercontent.com/63403330/182344340-6dc59567-5be7-4614-a8f7-efe82d436f32.png)

see that a session id is created in hashed form by server and stored as a cookie for that hosturl and api path, now whenever bwoser make further requests cookies are attached with it so that server can recognize it.

Please see server JSON image where u see ur variables and so callled cookie as shown.

![image](https://user-images.githubusercontent.com/63403330/182345949-82270eb5-53cf-4bd2-875e-89ecd83e0063.png)

this is amzing it will keep cookie for 1 day so if u close the browser it will be recgonized by the server.

![image](https://user-images.githubusercontent.com/63403330/182346384-9e259c13-4385-4957-bd10-d304995805c0.png)

Please note if server is closed then it will forget who is making the request hence instead of storing sesssion in session mem we prefer it to store it in some online databases.

ok ?

now u see session id as 

![image](https://user-images.githubusercontent.com/63403330/182347597-b31d3eb2-08f8-4db3-94d3-788627773735.png)

Ai4kz48IHS_sihiwTWCZyYxW0T3wrtsL

now in ur browser 

![image](https://user-images.githubusercontent.com/63403330/182347707-e61f2854-ccfd-40a9-a04a-3f7ec954e57f.png)













