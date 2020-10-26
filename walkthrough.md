# Description of Code

## Config

## Config.json
The config.json file in the config folder holds the login information for the database being used - in this case, passport_demo. The username and password fields contain the login information. The database field holds the database name being used. The host holds the ip information and the dialect contains the kind of database being used. 

## Passport.js
The passport.js file contains the code needed to login and authenticate users. It requires the "passport" npm package which is used for user authentication, using plugins known as strategies. When you provide a request to authenticate, Passport provides hooks for controlling what happens. The first function on line 7 takes the username inputted by the user and checks it against the database "passport_demo" to check if it exists. If it does not, it will clear the entry fields. On line 26, this else statement checks if the password is in the database in the same row as the username. If it is not, entry fields are cleared. 

## isAuthenticated.js
This file restricts routes depending on if a user is logged in or not. If a user is logged in, it alows a user to continue making requests. If not, the user is redirected to the login page. 

## Models

## index.js
The index.js file inside the models folder consists of sequelize boilerplate code. 

<!-- This code is created by Sequelize to process the config file and connect to the database. -->

## user.js
The file user.js 

## Public

## JS Folder

## login.js
The login.js file contains the front-end JavaScript for the login.html page. It contains the event handlers for this page. At the top, variables are initialized to reference the login fields on the html. On line 8 we have the event handler for submitting the form. It prevents the page from refreshing on click, and sets the variable user data to whatever the user inputs, taking away extra space on either side using the trim function. If either field is left empty, it does not continue. If the user inputs something in both fields, the loginUser function is called using the object userData. The loginUser function uses the route /api/login which is set up in the api-routes.js file, and passes on the email and password input. It then replaces the current page with the /members route. If there is an error, it is logged. 

## members.js
The members.js file contains the front-end JavaScript for the members.html page. This code contains a get request to display the currently logged in user name. It displays the /api/user_data route and displays the email address in the field designated with the class member-name.

## signup.js
The signup.js file contains the front-end JavaScript for the signup.html page. Similar to the login.js file, it contains variables that reference the signup form on the page. On line 8, the event handler for submitting the form begins. It has the same functionality as the login.js event handler, but grabs the values from the login form instead. On line 26, we have a post statement that uses the route /api/signup contained in the api-routes.js file and passes the email and password along. If there is an error, the function handleLoginErr is called which alerts the user of the issue. 

## style.css
This is the CSS stylesheet for the site. It sets the margin-top of the signup and login forms to 50px.

## Routes

## api-routes.js
This file contains all api routes for the site. It requires our models and passport. It calls the functions in models in order to create, read, update and delete information from the database. It uses passport in order to authenticate user submitted information. On line 9, the /api/login route is used and populated with the user inputted information passed from our front-end JavaScript. This information is authenticated using passport. On line 16, The 

## html-routes.js

## Base Folder

## server.js
