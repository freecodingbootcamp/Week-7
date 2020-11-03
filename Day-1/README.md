# Week-7 -- Day-1

## Node.js

What is node.js? Let's see how the web answers this question.

According to **w3schools**:
 -   Node.js is an open source server environment
 -   Node.js is free
 -   Node.js runs on various platforms (Windows, Linux, Unix, Mac OS X, etc.)
 -   Node.js uses JavaScript on the server

node.js can

 -   Node.js can generate dynamic page content
 -   Node.js can create, open, read, write, delete, and close files on the server
 -   Node.js can collect form data
 -   Node.js can add, delete, modify data in your database

According to **nodejs.dev**

"Node.js is a free, open-sourced, cross-platform JavaScript run-time environment that lets developers write command line tools and server-side scripts outside of a browser."

According to welll...myself:

Node allows you to run javascript on the server / back-end. So no more one language on the front-end and a different language on the back-end. Simplicity, consistency is generally good in programming. So having the ability to program your whole web or mobile using one language is a generally a good thing!



## Starting a Simple node.js Server

Make sure you have node installed.

Go to: https://nodejs.org/en/download/

![node.js installation page](https://raw.githubusercontent.com/Team-FCB/Assets/master/install_node_1.png)

Select the right file. In my case I chose macOS installer (.pkg) 64-bit.

The continue with installing.

![installation screen](https://raw.githubusercontent.com/Team-FCB/Assets/master/install_node_2.png)

After you are done you should have node and npm (helps installing node add-ons) installed on your computer.

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

Install `http`

Within the command line and in the directory where you have this app.js file run the following command:

    npm install http

Now run the app.js by typing in the following the command line and still in the directory where you have your app.js file

    node app.js

If everything went well you should see the message:

    Node server running on port 3000

In your terminal.
