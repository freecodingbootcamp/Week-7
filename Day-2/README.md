# Week-7 -- Day-2

## CRUD

**CRUD** --> **C**reate, **R**ead, **U**pdate, **D**elete

This is just a concept. It's nothing concrete or tangible. It's not a framework or programming language. It's just saying that most apps generally support CRUD functionality. But what do you create, read, update, or delete? Usually this is reference to an object in the database. So let's say we have a social networking app and we have a **USER** in the database.

 - So signing up a new user is **CREATING** a **USER**  
 - checking out a user profile is **READING** a **USER**
 - changing your user profile picture is **UPDATING** a **USER**  
 - finally deleting your account is **DELETING** a **USER** (except in facebook)

In most coding bootcamps you will hear the CRUD term being tossed around quite a bit. As in *make sure you app supports CRUD*. *When is the CRUD app due?*

#### CRUD --> HTTP Calls

What is interesting is that HTTP calls such **POST, GET, PUT/PATCH, DELETE** directly correlate to CRUD.

CREATE is POST, GET is READ, PUT/PATCH is UPDATE and DELETE is well DELETE.

Don't worry if you don't know too much about HTTP calls just yet. But in case you are interested, google *"REST calls"*.

## MVC

**MVC** --> **M**odel **V**iew **C**ontroller

Again this is one of those non-concrete, non-tangible things. It's a concept or idea. It makes sense though. It saying that code can generally be divided into three categories. It's either related to the Model (e.g. update a user in the db), View (e.g. Profile HTML page) and Controller (e.g. List all posts)

Don't worry if it's not 100% clear where everything falls into. It takes time to get a better understanding of MVC and once you see MVC in action it will make a lot more sense.  

## Express Generator

Let's say you want to get up and running with a fully functionality Express app relatively quickly.  Express has a package for that. It's called `express-generator`

Here is how you can install it on your mac computer. Run the following command in your terminal.

    npm install express-generator -g

Then `cd` into the newly created folder if you are not already inside of it.

Now do an `npm install`

    npm install

I think that should do it. You should be ready to launch your new app by running the following command:

    npm start

Make sure you do it in the root directory of your app.

If everything went well you should be  able to see a valid page in the browser if you visit:

[http://localhost:3000/](http://localhost:3000/)

![enter image description here](https://raw.githubusercontent.com/Team-FCB/Assets/master/express_1.png)
