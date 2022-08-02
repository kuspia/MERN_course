# ExpressJS

a very popular framework of nodejs for making server (remmember we did the same for http)

![image](https://user-images.githubusercontent.com/63403330/182040062-fb8d2596-0d9b-4fa4-8d63-8cc0d478c629.png)

and tht's wht we see when a browser try making a request on ```localhost:4000/``` since clearly though browser is requesting but server is not repsonding on that url.

![image](https://user-images.githubusercontent.com/63403330/182040145-f24b4d45-5546-4737-8e38-bdb653451871.png)

_see you know_ C R U D _opeartion in db_ right?

![image](https://user-images.githubusercontent.com/63403330/182040475-d140a851-7191-4368-96ad-38961104e384.png)

so here in terms of express we have _POST GET PUT DELETE_

now u should understand that a browser when makes a request can be of four types as shown above so basically 

```app.get(), app.post(), app.put(), app.delete()``` handles those types of request 

> remember in case of http we have to check it from if(req.method === "get") like this to know what kind of request it is 

we will look into get and post carefully and rest u can learn by the time 

#### app.get() and app.post() ?

so what happens when a browser request a server on particular URL or route say ```localhost:3000/about``` so what happens it actually wants or try to get a response from the server
as soon as user hits the  URL or route so we say that a browser is trying to get something from the server which is taken care by ```app.get()```

however sometimes let's say during filling of the form from some URL or route it try to post the content of form from the browser so in this case we say that ```app.post()``` will actually 
take care of that content sent from the browser to the server on same URL or route.

so now before diving in let's make it clear about form 

listen very carefully 

```
 <form action="/api" method="GET">
      <h1>REGISTER</h1>
      <input placeholder="Enter Your Name" type="text" name="name" id="name" />
      <input
        placeholder="Enter Your Email"
        type="email"
        name="email"
        id="email"
      />
      <input
        placeholder="Enter Your Password"
        type="password"
        name="password"
        id="password"
      />
      <input type="submit" value="Login" />
    </form>
  ```
   
now here it says as soon as form will be submitted browser will make a request (it is of 4 types if u cn recall) on the /api route and request type will be a GET so it can be only handled 
by ```app.get('/api' , .... )``` 

now if we change method to POST it will be handled by ```app.post()``` exclusively 

> TODO try both methods one by one with the follwing code and predict the o/p 

```
const express = require("express")
const app = express()
const path = require("path")
app.get("/", (req , res) => {
res.sendFile( path.join(__dirname, 'i.html' ) )
});
app.get("/api" , (req , res)=>{
    console.log("ABOVE")
   return res.send("GET")
})
app.post("/api" , (req , res)=>{
    console.log("BELOW");
   return res.send("POST")
})
app.listen(3000)
```

Can u really execute /api route if the method is post??

answer yes, follow this URL http://localhost:3000/api ( u can actaully do it without submitting the form ) ...... ... . ... . .
  
u can try printing ```req.url``` and see the results for both methods 

u can try printing ```req.body``` and see in both methods 


```
const body-parser = require("body-parser")
app.use(body-parser.urlencoded({extended:false}))
```

use above lines for req.body 


> GET carries request parameter appended in URL string while POST carries request parameter in message body which makes it more secure way of transferring data from client
   
##### but do u know what exactly api is ?? it's ok a kind of route or url but in api we send raw josn on response 

let's see that:

```
app.get("/v2" , (req , res)=>{
   res.json(
      {
     name: "get" 
      }
   )
})
app.post("/v1" , (req , res)=>{
const u = req.body.name 
console.log(u)
res.json(
   {
  success: true
  name: u
   }
)
})
```

![image](https://user-images.githubusercontent.com/63403330/182074937-0d121b3a-5f79-483b-a847-4e388885797f.png)

![image](https://user-images.githubusercontent.com/63403330/182075128-c5b0cb97-30a6-4975-9600-90fd729c15d2.png)


but listen in thunderstorm you also have to write this ```app.use(express.json())``` else you will see empty body however for browser it is not manadatory

![image](https://user-images.githubusercontent.com/63403330/182074994-1f1630eb-a3f0-40a7-a552-743899cf9124.png)

this is browser case and look at it basically we are doing post request via form submit button.

![image](https://user-images.githubusercontent.com/63403330/182075162-b521f802-7ef8-4720-b7d2-08830b214c53.png)

![image](https://user-images.githubusercontent.com/63403330/182075684-84831afc-462f-48aa-a662-28bf553c38cf.png)


Now we want to organize the things and make our ```i.js``` file look better as it will be very hectic with lot of apis and callback function ok?

so we create a dedicated file for callback functions and routes both look at these files one by one 

```
i.js
const express = require("express")
const app = express()
const path = require("path")
const bodyp = require("body-parser")
app.use(bodyp.urlencoded({extended:false}))
app.use(express.json())
const router = require("./route")
app.use(router)
app.get("/", (req , res) => {
res.sendFile( path.join(__dirname, 'i.html' ) )
});
app.listen(3000)
```

```
route.js
const express = require ("express")
const router = express.Router()
const cb = require('./callback')
router.route("/v1").post(cb.v1_cb)
router.route("/v2").get(cb.v2_cb)
module.exports = router
```

```
callback.js

exports.v2_cb = (req , res)=>{
    res.json(
       {
      name: "get" 
       }
    )
 }

exports.v1_cb = (req , res)=>{
    const u = req.body.name 
    console.log(u)
    res.json(
       {
      success: true,
      name: u
       }
    )
} 
```

```
i.html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>FORM</title>
    <style>
      body {
        background-color: rgb(145, 164, 179);
        margin: 0%;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        width: 100vw;
      }

      form {
        display: flex;
        flex-direction: column;
        height: 90vh;
        border-radius: 5px;
        width: 40vw;
        background-color: white;
        align-items: center;
        justify-content: space-evenly;
      }
      form > h1 {
        color: rgba(0, 0, 0, 0.644);
        border-bottom: 1px solid rgba(0, 0, 0, 0.644);
        width: 10vw;
        text-align: center;
        padding-bottom: 1vmax;
        font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
      }
      form > input {
        padding: 1vmax;
        width: 30vw;
        outline: none;
        font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS",
          sans-serif;
        font-size: 1.3vmax;
        border: none;
        border-bottom: 1px solid rgba(70, 70, 70, 0.5);
      }
      form > input[type="submit"] {
        width: 20vw;
        border: none;
        cursor: pointer;
        background-color: #eb4034;
        color: white;
        font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
          "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
        font-size: 1.4vmax;
        transition: all 0.5s;
      }
      form > input[type="submit"]:hover {
        background-color: #c4342a;
      }
    </style>
  </head>
  <body>
    <form action="/v1" method="POST">
      <h1>REGISTER</h1>
      <input placeholder="Enter Your Name" type="text" name="name" id="name" />
      <input
        placeholder="Enter Your Email"
        type="email"
        name="email"
        id="email"
      />
      <input
        placeholder="Enter Your Password"
        type="password"
        name="password"
        id="password"
      />
      <input type="submit" value="Login" />
    </form>
  </body>
</html>
```


Note 

```router.route("/v2").get().post()``` 

i.e for same api or route or path or URL u can define get post put delete and so on  make sure to pass callback functions in it !!

see this trick also to shorten the api path as shown in 1st image 

![image](https://user-images.githubusercontent.com/63403330/182079955-048029a6-3213-4c3d-ac31-1d5246a30d06.png)

Solution:

![image](https://user-images.githubusercontent.com/63403330/182079892-4bdb6ec4-f43a-44ce-ad4f-e844139f908b.png)

use of ```app.set()``` in express

```

var express = require('express');
var app = express();
var PORT = 3000;
  
app.set('title', 'GeeksforGeeks');
  
app.get('/', (req, res) => {
  res.send(app.get('title'));
})
  
app.listen(PORT, function(err){
    if (err) console.log(err);
    console.log("Server listening on PORT", PORT);
}); 
```

![image](https://user-images.githubusercontent.com/63403330/182325312-5273bfc8-0095-4d90-aa01-65e579c449b9.png)

