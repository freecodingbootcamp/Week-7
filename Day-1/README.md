# Week-7 -- Day-1

## Node.js

What is Node.js? Let's see how the web answers this question.

According to **w3schools**:

>  -   Node.js is an open source server environment
>  -   Node.js is free
>  -   Node.js runs on various platforms (Windows, Linux, Unix, Mac OS X, etc.)
>  -   Node.js uses JavaScript on the server

Node.js can

>  -   Node.js can generate dynamic page content
>  -   Node.js can create, open, read, write, delete, and close files on the server
>  -   Node.js can collect form data
>  -   Node.js can add, delete, modify data in your database

According to **Nodejs.dev**

> Node.js is a free, open-sourced, cross-platform JavaScript run-time
> environment that lets developers write command line tools and
> server-side scripts outside of a browser.

According to welll...myself:

Node allows you to run JavaScript on the server / backend. So no more one language on the front-end and a different language on the back-end. Simplicity, consistency is generally good in programming. So having the ability to program your whole web or mobile using one language is generally a good thing!



## Starting a Simple Node.js Server

### Install Node
Make sure you have Node installed.

Go to: https://Nodejs.org/en/download/

![Node.js installation page](https://raw.githubusercontent.com/Team-FCB/Assets/master/install_node_1.png)

Select the right file. In my case, I chose macOS installer (.pkg) 64-bit.

Then continue with installing.

![installation screen](https://raw.githubusercontent.com/Team-FCB/Assets/master/install_node_2.png)

After you are done you should have Node and npm (helps installing Node add-ons) installed on your computer.

### App.js File

Now create and open an app.js file and paste the following code inside of it.

    // app.js

    const http = require('http');

    // Create an instance of the http server to handle HTTP requests
    let app = http.createServer((req, res) => {
        // Set a response type of plain text for the response
        res.writeHead(200, {'Content-Type': 'text/plain'});

        // Send back a response and end the connection
        res.end('Hello World!\n');
    });

    // Start the server on port 3000
    app.listen(3000, '127.0.0.1');
    console.log('Node server running on port 3000');

### Install http Package

Install `http`

Within the command line and in the directory where you have this app.js file run the following command:

    npm install http

### Run app.js

Now run the app.js by typing in the following command and still in the directory where you have your app.js file

    Node app.js

If everything went well you should see the message:

    Node server running on port 3000

In your terminal. You should now be able to see the Hello World message in your browser if you go to localhost:3000

## Express.js Server

Let's do the same we just did above but using Express.js

### What is Express?  

Express to Node.js is a **little bit** like what jQuery is to JavaScript or Bootstrap is to CSS.
I am emphasizing a little bit in case a senior developer somewhere is having a stroke sensing somebody just wrote a blasphemous coding statement. What I am trying to say is that Express makes starting and defining a server easier and faster.

Here is how Express defines itself:

> Express is a minimal and flexible Node.js web application framework
> that provides a robust set of features for web and mobile
> applications.
>
> With a myriad of HTTP utility methods and middleware at your disposal,
> creating a robust API is quick and easy.

### App.js

Replace the original app.js with the following code.

    const Express = require('Express')
    const app = Express()
    const port = 3000

    app.get('/', (req, res) => {
      res.send('Hello World! - Express.js')
    })

    app.listen(port, () => {
      console.log(`Example app listening at http://localhost:${port}`)
    })


### Install Express

Let's install Express. Run the following command in the terminal:

    npm install Express

### Run app.js
Now run the app.js file in the terminal with the following command. But before you do make sure you stopped the old server. Just do a ctrl-c and that should exit the server service.

    Node app.js

You should now be able to see a `Hello World! - Express.js` in the browser if you visit localhost:3000

Bam, there you have it! Express.js server in only a few lines of code.
