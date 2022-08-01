# MongoDB

I know mongodb is very big topic as it have MongoDB (shell, compass) but we will focus entierly on MongoDB ATLAS !! Yayyy because it is online and that's what 
we want to be used easily if we deploy our website ok ?

But let's see how you can install your MongoDB locally 

![image](https://user-images.githubusercontent.com/63403330/182085477-ee974451-c805-4603-9ce8-2e422ef5ffb1.png)

https://www.mongodb.com/try/download/community

https://www.mongodb.com/try/download/tools



![image](https://user-images.githubusercontent.com/63403330/182086368-2234783c-c0d7-4b16-bd95-feee57ce2175.png)


confirm your installation like this 

![image](https://user-images.githubusercontent.com/63403330/182086762-72eed64f-3202-4089-afb2-5ca5038f0e8c.png)

Do this 


![image](https://user-images.githubusercontent.com/63403330/182086877-4df20d23-7cbc-404e-85d5-9f33651bf6b0.png)


check the follwing URLs on your own after installing or uninstalling 

C:\Users\1kusp\AppData\Local

C:\Users\1kusp\AppData\Roaming

C:\Program Files

Record structure of mongo (it is similar to json k/as bson (bianry json))

![image](https://user-images.githubusercontent.com/63403330/182087245-7bc3c646-f269-40b0-9283-129fe96fb159.png)

What is promising function ??

it is very important as js in single thread so what happens some functions are promising in nature they say i may take a lot or few seconds meanwhile rest code can execute and I will solve my problem or query and reflect it later

ex: 
```
mongoose.connect('mongodb://localhost:27017/sample', {useNewUrlParser: true , useUnifiedTopology: true})
.then(()=>{
    console.log("DB Integrated");
})
```

You can always use  ```.then()``` to pass callback inside it and do some print to knw when it is done exactly 

Let's see how we can setup a new database named as ```sample``` and a new collection named as ```boy```

```
const mongoose = require("mongoose");
mongoose.connect('mongodb://localhost:27017/sample', {useNewUrlParser: true , useUnifiedTopology: true})
.then(()=>{
    console.log("DB Integrated");
})
.catch((error) => {
            console.log(error);
})
const forma = new mongoose.Schema({ 
id: Number
},
{ timestamps: true } // optional 
);
const mod = new mongoose.model('boy', forma); 
    const mod1 = new mod ({
        id : 23 
    })
    mod1.save()
    console.log("1")
```

u will see a new collection named ```boys``` is created instead of ```boy```

now u see that ```mod1.save()``` returns a promise therfore ```console.log("1")``` is printed first and then it is executed but what if we want to forcefully execute printing of "1" ??

```
const adder = ()=>{
    const mod1 = new mod ({
        id : 23 
    })
    mod1.save()
}
adder();
console.log("1")
```

but listen this is sync function btw fyi, now see the o/p very carefully and observe it.

![image](https://user-images.githubusercontent.com/63403330/182104861-93b53587-f0e9-4816-8a62-25f5f486fd70.png)

```
const adder = async()=>{
    const mod1 = new mod ({
        id : 23 
    })
  const re =  await mod1.save() // pausedddd !! here the function adder bro 
  console.log(re)
}
```

#### Very important concept in JS async and await 

The await expression causes async function execution to pause until a Promise is settled (that is, _fulfilled or rejected_), and to resume execution of the async function after fulfillment. When resumed, the value of the await expression is that of the fulfilled Promise.


clearly in sync function if ```re``` which is the fulfilled value was used below so it may cause some issue right? so to handle we have concept of await.

![image](https://user-images.githubusercontent.com/63403330/182106459-026293ed-d360-419b-83a4-00cd394befd6.png)

now ```re``` is not a promise anymore and u alos can't use .then() with it as it is not a promise anymore .... promise is fulfilled now and hence u can safely proceed in async function to execute further commands!!

> remember async is like it can wait but sync will go sequence by sequence instructions forcefully 

![image](https://user-images.githubusercontent.com/63403330/182111322-6d4d768a-1d48-4090-8fa9-7cb16d67c3b6.png)


So Atlas let you create a cluster and then using browse collection you can navigate to your Database and hence see the collections and finally you can see your records .


