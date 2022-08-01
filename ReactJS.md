# ReactJS

? yes u should know this if u want something fast crispy exciting and tipsy !!

```do npx create-react-app .``` to install react in ur current _blank_ folder 

![image](https://user-images.githubusercontent.com/63403330/182137472-c940d824-648f-4497-b2dd-5b7925f782e4.png)

now see the folder one by one and delete any test named file, 

now make sure ur folder look like this::

![image](https://user-images.githubusercontent.com/63403330/182139069-7b4d780b-16d0-41f2-a53c-57b5db2f2639.png)

![image](https://user-images.githubusercontent.com/63403330/182139477-aeef4fa3-fb0b-4cc3-a5d9-a221115fd497.png)

![image](https://user-images.githubusercontent.com/63403330/182140219-219fc183-bcf3-4770-8c59-7eefb09ec08c.png)

![image](https://user-images.githubusercontent.com/63403330/182143730-38fa932e-eb42-43ca-84df-d40937656ff2.png)

Now we did good cleaning it's tiem to understand it now.

component first letter is big as shown 

![image](https://user-images.githubusercontent.com/63403330/182139919-a9ab0d02-979d-4f38-81e0-b83f0b2700aa.png)

now see we created App and inside it we made a div that we can render as many times we want inside ```index.js``` now see in index.js we have 

![image](https://user-images.githubusercontent.com/63403330/182140390-d4fc15c9-56e2-4257-9b4b-3b16d7d95d2a.png)

so that means basically this will be rendered in the root div of ```index.html``` which is our main website stuff.

![image](https://user-images.githubusercontent.com/63403330/182140790-324bf685-e0e5-45db-92f0-98c6dd5a9450.png)

now in terimal start the server as ```npm start``` and you will see like that 

![image](https://user-images.githubusercontent.com/63403330/182141294-577339fd-257a-4b4e-b64c-702b9f0097cd.png)

![image](https://user-images.githubusercontent.com/63403330/182141319-66f84e2b-0aa4-4025-a0c4-3756bca5ff56.png)

u see we get a deployed URL on some IP to test it on other device too at the same time.

```
function App() {
  return (
    <div>
     HEELELO
    </div>
  );
}
```

see above is ```JSS``` which is JS + HTML 

see inside <div> u cn write HTML and outisde that you can write JS, u can also use {} inside div to write JS inside it
  
  ![image](https://user-images.githubusercontent.com/63403330/182142247-05d0fc58-c4d9-4db4-9be5-0a6e431eb628.png) Install it 

choose this for your comfort of wrting tags like type h1 or div.class#id and hit enter and see then 
  
![image](https://user-images.githubusercontent.com/63403330/182142930-5d301bd7-1b49-442e-9595-f20746e3866d.png)

![image](https://user-images.githubusercontent.com/63403330/182143580-1214c031-76a0-418a-8480-3c6191b18bbf.png)

  Inline CSS
![image](https://user-images.githubusercontent.com/63403330/182144554-8dd6ee39-ccba-485c-8d79-9226885d0674.png)

![image](https://user-images.githubusercontent.com/63403330/182144709-f777f4c1-f6ee-4324-b76d-b4db9432bb95.png)


Do, 

![image](https://user-images.githubusercontent.com/63403330/182145708-24da93af-9e94-45bb-bbb7-07f6edd6d6b0.png)


nd hit enter to see the magic 

so we created a new component named Navbar 

```
import React from 'react'
const Navbar = () => {
return (
<div>Navbar</div>
)
}

export default Navbar
```

now this we want to use in our ```App.js``` file

so use the component as shown 

![image](https://user-images.githubusercontent.com/63403330/182146680-7606d6eb-ecc3-4dc0-bcda-87cb021dc28a.png)

one more way 
  
![image](https://user-images.githubusercontent.com/63403330/182147053-3d759b6f-626d-4a93-984e-7359b702a0d3.png)

![image](https://user-images.githubusercontent.com/63403330/182147110-3b5b410c-0c81-46ae-b002-2e34ec41514b.png)
  
![image](https://user-images.githubusercontent.com/63403330/182147353-d68044f5-3bf9-4892-bc1e-bbb3df14ab9e.png)


create data.json (https://github.com/meabhisingh/MiStore/blob/master/src/data/data.json) in data folder inside src and also make component name folder inside the same ok?

Now we want to create PreNavbar 
  
  ![image](https://user-images.githubusercontent.com/63403330/182151159-98a52c18-f646-439a-b129-611973bbca96.png)

  
  u see there are 2 navbars I am talking of above one 
  
  change ur directories as shown 
  
  ![image](https://user-images.githubusercontent.com/63403330/182151302-43bf0136-9d63-46ab-bfdc-0a0ff3317fcb.png)

  
  now see there is one way ```import "../styles/PreNavbar.css"``` it is written in PreNavabar component obviously, but let's say css file is not created so select the path and press ```ctrl + click``` in visual studio to open or create it.
  
  use of <link> tag 
  
  ![image](https://user-images.githubusercontent.com/63403330/182160028-8135067b-5a6f-4de3-8b29-98f3a5edc6f6.png)

  we use it because in <a> tht url is open up by reloading but using link we can route it without any loading ok moreoever we can see that 
  
  ![image](https://user-images.githubusercontent.com/63403330/182160444-3493c487-5802-4582-b39c-415358f8b801.png)

  as we redirect to the route then only below components listed to route will be opened up.
  
 
  to create slider or such stuff we install this ok ?
  
  
  ![image](https://user-images.githubusercontent.com/63403330/182165275-debbe490-c3f4-4e9a-8019-ad20720f5317.png)

 ![image](https://user-images.githubusercontent.com/63403330/182166962-b864c409-5aaf-4b16-add7-1ed7d16c15b8.png)

  
  look at slider code 
  
 ```
  import React from 'react'
import Carousel from 'react-bootstrap/Carousel'
import 'bootstrap/dist/css/bootstrap.min.css';

const Slider = ({start}) => {
    return (
        <Carousel fade>
       {start.map((item)=>(
            <Carousel.Item>
            <img
              className="d-block w-100"
              src={item}
              alt="First slide"
            />
          </Carousel.Item>
       ))}
      </Carousel>
    )
}

export default Slider
 ```
  
  ![image](https://user-images.githubusercontent.com/63403330/182168034-56045030-2c13-4433-aaf9-e03c1668ed19.png)

  
  
  
