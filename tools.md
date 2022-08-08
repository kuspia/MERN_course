# Git

see 1st of all make a .gitignore file in root folder add anything u wanna ignore 

now make a empty repo on git web 

so now type in termianl of vs code as after every succesful setup

```
git init
git add .
git commit -m "Your message here"
git status
git remote add origin <your github .git link>
git push origin master
```

![image](https://user-images.githubusercontent.com/63403330/183232501-772bea44-33a4-4b20-ae17-0548b4777027.png)

now to deploy on heroku 

create a app 

and then do 

```
heroku login
```

on termianl of vs code

and make sure u login and have heroku CLI in your pc 

```
heroku git:remote -a nft-warranty-app
git push heroku master
```


https://dev.to/myogeshchavan97/how-to-deploy-react-node-js-application-to-heroku-4jb4 


check this to deplpoy reactjs + nodejs (note as both run on diff port but after we combine in a build folder the problem get solved)

Infact its good practice to build folder ```build``` when working with reactjs so that server and client are on same port 

and tbh still you can run and make edits ```yarn build``` reflects the changes and observe it 

but still it is not recommened becz everytime to see the changes we need to build but same is not true when we are at two differrent ports 



