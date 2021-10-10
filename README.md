# INFO

This file contains:
1) Chapter Notes and thier links
2) Git & Github
3) Important LINKS to start with
4) All in semi-sorted order
--------------------------------------------------------------------------------------------

# CHAPTERS

## CHAPTER (Basic)

css generator
lorem ipsum generator
colorhunt.io (color palette)
css font stack
bootstrap
fontawesome (icons)


STEP-1:
Go to "balsamiq.cloud" to start wireframing.

STEP-2:
Start implementing that style in html along with bootstrap classes.


------------------------------------
1) Make sections with id specifying nav, title/hero, about, contact, and so on.
2) Then add div into them. Then just add containers to whole or just any bunch of section or element that you want to give padding.


NOTE:
1) Font size in pixels(px) is NOT DYNAMIC i.e. when you change your browser font, the font stays in same size. Whereas percentage(%),
em, IS DYNAMIC. [ 16px = 100% = 1em ].
But em can cause issues as em inherits parent element's size too on top adding the font size to become even larger.
So best way is TO USE REM, this is only relative to the current element. So it doesnt get affected by upstream size changes.
2) CSS Prioroty: Highest to Lowest: Inline CSS > ID > CLASS > hierarchical. Heirarchical is when the next css change overrides previous.


----------------------------------------------------------------------------------------------------------------------------------------



## CHAPTER (JavaScript):

1) Principles of Writing Consistent, Idiomatic JavaScript ( https://github.com/rwaldron/idiomatic.js/ )

2) Foundation of all prog langs: Data Type, Keywords, Variable.

3) Question was to find days, weeks, months remaining to live if I had the last age as 90.

function lifeInWeeks(age) {

/************Don't change the code above************/
    var yearsRemaining = (90 - age);
    var days = (yearsRemaining * 365);
    var weeks = (yearsRemaining * 52);
    var months = (yearsRemaining * 12);
    alert("You have "+days+" days, "+weeks+" weeks & "+months+" months left to live.");
/*************Don't change the code below**********/
}

lifeInWeeks(24);


----------------------------------------------------------------------------------------------------------------------------------------

## CHAPTER (DOM):

- Inline JS :
<body onload="alert('Hello');">
</body>


- Internal JS :
<body>
	<script type="text/javascript">
		alert("Hello");
	</script>
</body>


- External JS :
script tag defined in head/body tag
<script src=""></script>



----------------------------------------------------------------------------------------------------------------------------------------

## CHAPTER (ADVANCED JS & DOM MANIPULATION):

- Methods are functions stored as object properties.

- First Class function:
( function is treated like any other variable ) :

//first-class function
const foo = function () {
	console.log("foobar");
}

//invoked
foo()

//higher-order function
( a function that takes another function as an input ) :
( A function that returns a function is called a Higher-Order Function ) :


----------------------------------------------------------------------------------------------

## CHAPTER ( Node & ExpressJS ) :

Node REPL (interactive shell that runs bits of code)
Native node modules dont need to be installed with npm
External node modules need to be installed with npm
Both native and external node modules need to be incorported into your current project by using JS "require()" method
package.json file contains app's: metadata, basic info , dependencies

Nodemon wraps node. Its only used for development & not in production.
npm <script_name> is the syntax and we use npm start to run the "start" script inside package.json file.

Handle "requests" & "responses" with GET.
Send form data to the server using action attr : action:"/"
Use .sendfile() to respond to requests with HTML files


---------------------------
- WE CAN USE res.send() ONLY ONCE per ".get()" / ".post()" method. Because once it is send, that is the end.
  BUT WE CAN CALL res.write() ANY NUMBER OF TIMES. So USE res.write() FOR MULTIPLE STRINGS TO SEND, AND JUST CALL res.send() once to send then all.
  res.send can only be called once, since it is equivalent to res.write + res.end()
---------------------------


- app.use() loads a function to be used as middleware

- To interact with the form data, we need a body-parser package.
https://www.section.io/engineering-education/rendering-html-pages-as-a-http-server-response-using-node-js/

- INFOGRAPHICS OF HOW A FORM DATA IS HANDLED
https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/forms#form_handling_process

Question: Why we added the logic to the backend and not the frontend?
Answer:
1) As JS on the server side will do the heavy-lifting of computing & stuff while the client side will only be rendered.
2) Also the business logic (the secret code) is hidden from the user. [INFO: Watch Backend Chapter video]




### --- LINKS ---
https://stackoverflow.com/questions/35167824/difference-between-a-server-with-http-createserver-and-a-server-using-express-in
https://medium.com/@ralph1786/how-to-setup-an-express-server-5fd9cd9ae073


----------------------------------------------------------------------------------------------

## CHAPTER ( APIs - Application Programming Interfaces ) :

- API is a set of "commands/ functions/ protocols/ objects" that programmers can use "to create s/w" or "interact with an external system"

- Endpoints | Paths | Paramaters | Authentication

Endpoint example: https://v2.jokeapi.dev/joke/

Path example: https://v2.jokeapi.dev/joke/Any  [ here "Any" is the category needed to get jokes, which here means the path ]

Paramaters example: https://v2.jokeapi.dev/joke/Programming?contains=debugging   [ they go at the end of URL after a "?" ]

Authentication: [its used on monetized APIs, also to keep track of how often the api is being used]


- Make GET request to external server (here i got to know that "axios" is just like https and express, to talk with external server) :
(in course we used HTTPS (native module), but try that AXIOS one, its looking amazing)
https://www.twilio.com/blog/2017/08/http-requests-in-node-js.html

- So, the question which ate you the most,
Q) how will you get weather data from your server, but your server has to get it from external one.
  OR
Q) that how will you get the data via the api from external server through your express app.
Answer is that : Express is your server, and you want to contact some external server via api, then, you'll just call the API
under the app.get() method of express.
Because the process is like,
1) client requests for the weather info from the server(express).
2) but as your server is relying on someone else's server for that data then it will request other server via API under its .get() method
3) for requesting other server, we either use node's native "HTTPS" module, or "AXIOS" etc.
   [DONT FORGET to add https:// before URL] .... why .... because here we are in a server and not in a browser, server cannot do that.
4) our data should be parsed so that it should be filtered and readable  [using .on() method of response to tap data]
5) it is then passed to client.
It was like:
[ CLIENT ] --request/response-- [ YOUR SERVER/EXPRESS ] --request/response-- [ SOMEONE ELSE'S SERVER ]

- To check if that external server is up and running OR to check error, we use .statusCode . More on statusCodes here :
https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

- To serve external CSS files, images, JS files, we use a middleware known as express.static, like shown and explained:
https://stackoverflow.com/questions/34174133/why-does-omitting-the-line-app-useexpress-static-dirname-public-stop-my

https://expressjs.com/en/starter/static-files.html

- The app.use() function is used to mount the specified middleware function(s) at the path which is being specified. It is mostly used to set up middleware for your application.

- Mailchimp:
1) Login
2) Go to : Integrations > API keys > Create one > copy and keep it
3) Go to : Audience > Settings > Audience name & defaults > Audience ID

- Heroku :
1) dont forget to add port as process.env.PORT || 3000. "process.env.PORT" dynamically allots a port on the server.
2) make a Procfile and add the line as: web: npm start/node app.js
3) In shell:
> git init
> git add .
> git commit -m "any"
> heroku create
> git push heroku master
4) If wish to make changes, then "git add" that file and "commit" and "push".
5) WARNING NOTE: persistent storage
6) Check logs:
> heroku logs --tail



----------------------------------------------------------------------------------------------

## CHAPTER ( EJS - Embedded JavaScript ) :

-  EJS is a templating engine. Used to make and use templates and partials/layouts. Partials/Layouts are pieces of reusable code.
we just cant keep on writing multiple res.write() statements, hence, we use TEMPLATES.
We use ejs by setting up markers in ejs file. Every HTML is valid ejs.

- USAGE:

1) make a folder "views". Keep all .ejs files inside it.
2) <%= key %>  : this is a marker. place it inside .ejs file where you want dynamic changes.
3) Use res.render("EJSfilename", key:value). "value" is any variable which will put that value in.

- TEMPLATES:

  If we wish to use templates extensively, for example, we want to have another page with the same functionality but with a different
  title name and all HTML same(as we are using the same template).
  In that case, the process will go like making app.get() request handle by rendering the updated marker "values".
  For example if "listTitle" marker had a value of date in the "/" route.
  Then "listTitle" will have some other string "any" as value in the "/other" route.
  And also a new array for another page to save values of that page.

  Then we'll "skip IT'S app.post request as we're going ot handle that in our "/" routes app.post request with some little logic.
  The logic is used by setting up marker to the value attr of button.
  And as we have set different marker values for different pages.
  We will now catch that in if..else.
  if (req.body.buttonname === "markerValue") {do this and redirect to this route}
  else {do this and redirect to other route}

- LAYOUTS/PARTIALS:

  If we wish to use layouts/partials extensively, for example, we want to have an about page with the same background but different
  body. Then we can use partials. Partials are supplied as raw html by a specific marker. Partials example are "header", "footer", etc.

- IMPORTS AND EXPORTS:

  When making a function as a module and importimg it in another file, I came across a fix for a simple issue i was facing.
  It was then when I knew that NodeJS used commomJS modules whereas ES6 used ES6 modules. Node added support for it and its way easy.
  https://stackoverflow.com/questions/57492546/what-is-the-difference-between-js-and-mjs-files

  Next time use ".mjs" as extension as these are treated as ES6 modules by NodeJS.
  (".cjs", ".js" are treated as default common nodejs modules. If you have .js files, then add a top-level object "type":"module" in package.json)


### - LINKS:

IMPORT/EXPORT:
https://www.digitalocean.com/community/tutorials/js-modules-es6

WAYS TO DECLARE FUNCTIONS IN JS:
https://dmitripavlutin.com/6-ways-to-declare-javascript-functions/

LODASH:
https://medium.com/voobans-tech-stories/10-lodash-functions-everyone-should-know-334b372aec5d


-----------------------------
#### EJS Challenge ##
-----------------------------

1) First have a visual cue of how your website should look, based on what functionalities it will have.

2) As we are making with EJS templates, then each "navigational page" should be declared in views folder,
   along with the publish pages from where you'll publish your posts. Keep publish routes out of header links
   so that only you can access them.

3) ISSUE FIX (header nav links not working) : You can handle the routes by app.get() request handlers.
   But for making the header nav links to actually work on click, just set the <a> tag's "href" attribute
   to the "ROUTES" which will make them dynamic as they're on server now. Mistake was that you declared the path
   as local files.

4) (LEARNED NEW!) Store multiple data inputs in an obj : So for handling form inputs, it can get messy handling each input
   in different variable and different array. Here we just made an object. And as an object can have key:value pairs
   or nested key:value pairs, we used
   "title" as key and req.body.elementattrname as value
    &
   "content" as key and req.body.otherelementattrname as value.
    Hence, making two key:value pairs in one obj.

    - Now push that obj into an array. Use the array for displaying. Remember, DO NOT FORGET to JSON.stringify() that
      object as the server needs strings only.

    - A JSON string is basically the same but in strings "{key: value, ...}"

    - Convert JS OBJECT TO JSON STRING:
      JSON.stringify()

    - Convert JSON STRING TO JS OBJECT:
      JSON.parse()

    - We use JSON.parse() on the data which arrives from the server, to access object's specific data.

    - WHAT IS JSON:
      ^ JSON is just a string format.
      ^ An open standard file format and data interchange format that uses
        human-readable text to store and transmit data consisting of key–value pairs.
      ^ A lightweight format for storing and transporting data.
      ^ Often used when data is sent from a server to a web page or vice-versa.

    - SOLUTION TO ACCESS OBJ "PROPERTY" OF AN OBJ PRESENT IN AN ARRAY:
      just use the dot notation with the arrayname.key using a for loop by iterating through like arrayname[i].key


    - A web page can display JSON STRING but not JS obj. The web page showed [object Object]


    - LINK: http://benalman.com/news/2010/03/theres-no-such-thing-as-a-json/

5) Array(s) we used to access obj property inside an array:

   FOREACH (here, "homePosts" is a marker which is an array of obj, "post" is what we have given as a singular form of posts &
   used it to access object property "title") :
   <% homePosts.forEach(function(post) { %>
      <li> <%= JSON.stringify(post.title) %> </li>
   <%  }) %>

   FOR (here, "homePosts" is a marker which is an array of obj, and by syntax in "for" loop, we use the array name with iterator
   to access object property "title") :
   <% for (var i=0; i<homePosts.length; i++){ %>
      <li> <%= JSON.stringify(homePosts[i].title) %> </li>
   <%  } %>


6) (LEARNED NEW!) Express Routing Parameters:
    - Used when making custom routing paramters for any of page links.
    - For example, a blog post in home page opens in a different page with the title of the blog in the route paramter.

    - app.get("/news/:topic", function(req, res) {  //make your custom param topic by specifying it with a colon(:)
        console.log(req.params.topic)  //tap into it by "req.params.topic"
      })

    -

7) (LEARNED NEW!) Accessing an obj property in an array:
    - WE NEED TO LOOP THROUGH.

8) LODASH
    - Lodash makes JavaScript easier by taking the hassle out of working with arrays, numbers, objects, strings, etc.

    - Lodash’s modular methods are great for:

      Iterating arrays, objects, & strings
      Manipulating & testing values
      Creating composite functions

9) Google:
    - Verb Object ProgrammingLanguage (query: truncate string javascript)

10) (LEARNED NEW!) How to make blog link open in new page:
    - As we have a post.ejs file
    - We'll use this file to render after we've checked if the req.param equals to our obj title
    - Then as we have access to array's properties so now we'll put them as markers in post.EJS
    - Then for "READ MORE" link we'll specify the "href" attr of <a> tag with the dynamic ejs marker

11) Alas! Completed a CREATE, READ app IN NODE & EJS.







# -----------------GIT & GITHUB------------\==WORKING DIR - STAGING DIR(.index) - REMOTE DIR==/--------------------
git init      (initializes empty git repo in your directory)
git config --global user.name 'your_username'          (add name and email)
git config --global user.email 'your_email'
git add <file>        (add files to staging/ .index)    / git add .       (add all files)
git status          (see status of file in staging/ .index)

[if any changes made to file and saved, then used 'git status' command, then you'll see modified file to either be removed or to be added to staging]


git commit -m 'description'     ('-m' to skip the editing stage)
touch .gitignore      (make a file named '.gitignore' & add any 'filename' OR '/directory' that you want to exclude from uploading to git)

git diff file_name (shows differences in versions of file)
git checkout file_name (gets back the version)

git branch branch_name    (creates a new branch)
git checkout branch_name    (switch to any branch)

[if changes made(in editor) in another branch is committed, and if you switch to your previous branch, you'll not see the changes you made, until you merge the branch]

git merge branch_name


git remote        (lists all remote repos you've worked with)
git remote add origin <url>    (adds/links a remote repo)
git push -u origin branch_name     (push your changes)


[suppose another user wants to work on those files, they'll now 'clone' and will just 'pull' for the updates]


git clone <url>          (under any dir, fire this command and it'll clone that repo to your dir)


[if multiple devs are working on a project and if someone has made any changes, and you want those changes to reflect to your clone too, then fire 'pull']

git pull     (updates the working dir with the other user's changes)

---------------------------------------------------------------------------













# -------------LINKS--------------------

FOR USE IN PORTFOLIO :
1)
Web Development In 2021 - A Practical Guide:  https://www.youtube.com/watch?v=VfGW0Qiy2I0
- Can be usefull to add in resume : https://youtu.be/VfGW0Qiy2I0?t=3302

2)
MAKE AN AUTHORITATIVE PIECE: https://medium.com/free-code-camp/want-to-boost-your-job-prospects-become-an-authority-on-something-heres-how-473a62183fa9

OTHERS :
WHAT IS NODE: https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction

MERN tutorial MONGODB: https://www.mongodb.com/languages/mern-stack-tutorial

Medium Tutorial: https://medium.com/techiepedia/what-exactly-a-mern-stack-is-60c304bffbe4

THE PROJECT : https://medium.com/@beaucarnes/learn-the-mern-stack-by-building-an-exercise-tracker-mern-tutorial-59c13c1237a1
- VIDEO: https://www.youtube.com/watch?v=7CqJlxBYj-M

REACT WEATHER PAGE project : https://dev.to/sandyabhi/fetching-data-from-weather-api-using-axios-in-reactjs-2bpg

ES6(JS2015) & its features compared with ES5 : https://www.freecodecamp.org/news/write-less-do-more-with-javascript-es6-5fd4a8e50ee2/
- const & let Keywords
- arrow functions
- template literals/strings
- default parameters
- array/object destructuring (assign value of [array] / {object} to new variable easily)
- import & export
