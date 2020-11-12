# Week-7 -- Day-4

## Express w/ ejs Mini Message Board Project

Let's review Odin project's mini message board project found here:

https://www.theodinproject.com/courses/nodejs/lessons/mini-message-board

### Getting Started - Express with Templating / View Engine

At this point you should have or at least be able to setup an express app with a templating / view engine. We are going to use ejs for templating / view engine.

Please refer to the following two links if you still need help with express and templating engine:
https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/skeleton_website

You are going to use the express-generator to generate an express app but remember to specify a templating engine with your command:

```bash
express NAME-OF-APP-HERE --view=ejs
```

I am assuming you have express already installed. Please refer to the express link above for a more comprehensive set of instructions.

### Combining Server Code (bin/www & app.js)

Let's simplify and combine our server code. When you genereate an express app using the express-generator module it creates a bin/www file. We are going to move the content of this file to app.js in the root directory.

Here is how your app.js should look like after the move

**app.js**

    var createError = require('http-errors');
    var express = require('express');
    var path = require('path');
    var cookieParser = require('cookie-parser');
    var logger = require('morgan');

    // ** Moved from bin/www **
    var debug = require('debug')('express-generator-app-ejs-default:server');
    var http = require('http');

    var indexRouter = require('./routes/index');
    var usersRouter = require('./routes/users');

    var app = express();

    // view engine setup
    app.set('views', path.join(__dirname, 'views'));
    app.set('view engine', 'ejs');

    app.use(logger('dev'));
    app.use(express.json());
    app.use(express.urlencoded({ extended: false }));
    app.use(cookieParser());
    app.use(express.static(path.join(__dirname, 'public')));

    app.use('/', indexRouter);
    app.use('/users', usersRouter);

    // catch 404 and forward to error handler
    app.use(function(req, res, next) {
      next(createError(404));
    });

    // error handler
    app.use(function(err, req, res, next) {
      // set locals, only providing error in development
      res.locals.message = err.message;
      res.locals.error = req.app.get('env') === 'development' ? err : {};

      // render the error page
      res.status(err.status || 500);
      res.render('error');
    });

    // ** Moved from bin/www **
    /**
     * Get port from environment and store in Express.
     */

    var port = normalizePort(process.env.PORT || '3000');
    app.set('port', port);

    /**
     * Create HTTP server.
     */

    var server = http.createServer(app);

    /**
     * Listen on provided port, on all network interfaces.
     */

    server.listen(port);
    server.on('error', onError);
    server.on('listening', onListening);

    /**
     * Normalize a port into a number, string, or false.
     */

    function normalizePort(val) {
      var port = parseInt(val, 10);

      if (isNaN(port)) {
        // named pipe
        return val;
      }

      if (port >= 0) {
        // port number
        return port;
      }

      return false;
    }

    /**
     * Event listener for HTTP server "error" event.
     */

    function onError(error) {
      if (error.syscall !== 'listen') {
        throw error;
      }

      var bind = typeof port === 'string'
        ? 'Pipe ' + port
        : 'Port ' + port;

      // handle specific listen errors with friendly messages
      switch (error.code) {
        case 'EACCES':
          console.error(bind + ' requires elevated privileges');
          process.exit(1);
          break;
        case 'EADDRINUSE':
          console.error(bind + ' is already in use');
          process.exit(1);
          break;
        default:
          throw error;
      }
    }

    /**
     * Event listener for HTTP server "listening" event.
     */

    function onListening() {
      var addr = server.address();
      var bind = typeof addr === 'string'
        ? 'pipe ' + addr
        : 'port ' + addr.port;
      debug('Listening on ' + bind);
    }

    module.exports = app;

--> **Now delete the bin/www file** <--

In your package.json change the following line

    "start": "node ./bin/www"

to

    "start": "node app.js"

## Let's Create the Routes

Routes is just code that specifies what happens when somebody visits the server. There are different kind of routes GET, PUT, POST etc. But you can also specify a path such /messages.

We need two routes: display all messages `GET` to `/` and create a new message `GET` to `/new`

The first route will display an index.html page along with all current messages.
The second route will show a form where a user can enter the details for a new message.

By the way, you can ignore the users routes for now. They came with express-generator.

At the top of the routes/index.js file place the array of messages:

```javascript
const messages = [
   {
     text: "Hi there!",
     user: "Amando",
     added: new Date()
   },
   {
     text: "Hello World!",
     user: "Charles",
     added: new Date()
   }
];
```

now change

    router.get('/', function(req, res, next) {
      res.render('index', { title: 'Express' });
    });

to

    router.get('/', function(req, res, next) {
      res.render('index', { messages: messages, title: 'Messages' });
    });

Add another route for the new message page. Note: we haven't created the ejs page inside the view folder yet.

    /* GET New Message Page. Show the page. */
    router.get('/new', function(req, res, next) {
      res.render('form', { title: 'MINI MESSAGE BOARD', header: 'New Message Page' });
    });


One more route for when the user is ready to submit the new message information. Notice the .post instead of the .get

    router.post('/new', function(req, res, next) {
      let content = req.body;
      let text = content.text;
      let user = content.user;
      let new_message =
      {
        text: text,
        user: user,
        added: new Date()
      }
      messages.push(new_message);
      res.redirect('/');
    });


So the final routes/index.js should look like this:

**routes/index.js**

    var express = require('express');
    var router = express.Router();

    const messages = [
       {
         text: "Hi there!",
         user: "Amando",
         added: new Date()
       },
       {
         text: "Hello World!",
         user: "Charles",
         added: new Date()
       }
    ];

    /* GET Home Page. */
    router.get('/', function(req, res, next) {
      res.render('index', { messages: messages, title: 'MINI MESSAGE BOARD', header: 'List of Messages' });
    });

    /* GET New Message Page. Show the page. */
    router.get('/new', function(req, res, next) {
      res.render('form', { title: 'MINI MESSAGE BOARD', header: 'New Message Page' });
    });


	/* POST Handle new message post/submission */
    router.post('/new', function(req, res, next) {
      let content = req.body;
      let text = content.text;
      let user = content.user;
      let new_message =
      {
        text: text,
        user: user,
        added: new Date()
      }
      messages.push(new_message);
      res.redirect('/');
    });


    module.exports = router;

## View Files

The routes we just created were back-end code. Now let's work on some front-end stuff.
We need to display all the messages in the views/index.ejs page.

We really just need to iterate over the messages array coming from the backend.  

    <% for(let i=0; i < messages.length; i++){ %>
          <li> <%= messages[i].text %></li>
        <% } %>

so the whole views/index.ejs should now look like this:

**views/index.ejs**

        <!DOCTYPE html>
    <html>
      <head>
        <title><%= title %></title>
        <link rel='stylesheet' href='/stylesheets/style.css' />
      </head>
      <body>
        <h1><%= title %></h1>
        <p>Welcome to <%= title %></p>

        <% for(let i=0; i < messages.length; i++){ %>
          <li> <%= messages[i].text %></li>
        <% } %>

      </body>
    </html>

Now let's create a form ejs view. Create a form.ejs file inside the views folder.

**views/form.ejs**

    <!DOCTYPE html>
    <html>
      <head>
        <title><%= title %></title>
        <link rel='stylesheet' href='/stylesheets/style.css' />
      </head>
      <body>
        <h1><%= header %></h1>
        <p>Welcome to <%= title %></p>
        <form class="new-message-form" action="/new" method="post">
          <input type="text" name="text" value="" placeholder="Enter message here...">
          <input type="text" name="user" value="" placeholder="Enter your name here...">
          <button type="submit" name="button">Submit</button>
        </form>
      </body>
    </html>



That should be it. I have uploaded an example of what we have done here:

https://github.com/mujibsardar/fcb_basic_express_ejs_example
