# Code Walkthrough

## Table of Contents
* [Config Folder](#config)
* [Models Folder](#models)
* [Public Folder](#public)
* [JS Folder](#js_folder)
* [Routes](#routes)
* [Base Folder](#base_folder)
* [Additional Features](#additional_features)

## Config

## Config.json
The config.json file in the config folder holds the login information for the database being used - in this case, passport_demo. The username and password fields contain the login information. The database field holds the database name being used. The host holds the ip information and the dialect describes the language used for the database.

This image shows the MySQL configuration information used by Sequelize.

![Config](/public/assets/config.png)

## Passport.js
The passport.js file contains the code needed to login, authenticate, and serialize users. It requires the "passport" npm package which is used for user authentication, using plugins known as strategies. When you provide a request to authenticate, Passport provides hooks for controlling what happens. The first function on line 8 takes the username inputted by the user and checks it against the database "passport_demo" to check if it exists. If it does not, return the message "Incorrect email". On line 27, this else if statement checks if the password is in the database in the same row as the username. If it is not, the message "Incorrect password" is returned. If both username and password are valid, it returns the user. The code to serialize and deserialize users begins on line 41. This allows authentication to be remembered across different http requests. 

This image displays the main functionality of passport - verifying user emails and passwords.

![Passport](/public/assets/passport.png)


## isAuthenticated.js
This file restricts routes depending on if a user is logged in or not. If a user is logged in, it alows a user to continue making requests. If not, the user is redirected to the login page. 

## Models

## index.js
The index.js file inside the models folder consists of Sequelize boilerplate code. It reads all files inside the models folder and sets them up to be used with Sequelize, as well as setting up the connection to the database using the config.json file. This file requires file system, path, Sequelize, and the config.json file, and is exported as db.


## user.js
The file user.js is the model for the site. It generates the tables and columns in MySQL. On line 5 the class "User" is created by declaring it and defining it through sequelize. This class sets up the table "Users" in Sequelize. Even though it is initialized as "User", sequelize automatically adds an "s". This table has the columns of email - set as String in line 7. It is not allowed to be null, must be unique, and is validated to be an email consisting of the format "text@hostname.com". The password column begins at line 16 and is also defined as a string and not allowed to be null. On line 19 a prototype is added to User which adds a custom method that checks if the unhashed password entered by the user matches the hashed password in the database. This file requires Bcrypt which is used to encrypt passwords. On line 27 a hook is added that runs before a user is created, automatically hashing passwords as they are added.

This image shows the Class "User" creation, which is the template for the users table in MySQL. Sequelize utilizes this file to create the table.

![User](/public/assets/user.png)


## Public

## login.html

This file contains the html for the login page. It includes a navbar, and a form containing two text fields and a button. These elements are referred to in login.js.

## members.html

This file contains the html for the members page. It includes a navbar and a container with a header used to display the user email in the member-name span.

## signup.html

This file contains the html for the signup page. It includes a navbar, and a form containing two text fields and a button. These elements are referred to in signup.js.

## JS_Folder

## login.js
The login.js file contains the front-end JavaScript for the login.html page. On line 1, we have a function that waits until the page is ready to run. It contains the event handlers for this page. At the top, variables are initialized to reference the login fields on the html. On line 8 we have the event handler for submitting the form. It prevents the page from refreshing on click, and sets the variable user data to the values in the email-input field and password-input field, taking away extra space on either side using the trim function. If either field is left empty, it does not return anything. If the user inputs something in both fields, the loginUser function is called using the object userData. The loginUser function uses an http post method to call the route /api/login which is set up in the api-routes.js file, and passes on the email and password input. It then replaces the current page with the /members route. If there is an error, it is logged. 

This image shows the function that is run when a user clicks the submit button on the login form.

![Login Frontend JavaScript](/public/assets/login.png)

## members.js
The members.js file contains the front-end JavaScript for the members.html page. At the top of the page is a function that prevents the page from running before the page is ready. On line 4 is a get request to display the currently logged in user name. It uses the http get method to call the /api/user_data route and displays the email address in the field designated with the class member-name.

## signup.js
The signup.js file contains the front-end JavaScript for the signup.html page. Similar to the login.js file, it contains a function to wait for the page to be ready before running and variables that reference the signup form on the page. On line 8, the event handler for submitting the form begins. It has the same functionality as the login.js event handler, but grabs the values from the login form instead. On line 26, we have a http post method that uses the route /api/signup contained in the api-routes.js file and passes the email and password along. If there is an error, the function handleLoginErr is called which alerts the user of the issue. 

## style.css
This is the CSS stylesheet for the site. It sets the margin-top of the signup and login forms to 50px.

## Routes

## api-routes.js
This file contains all api routes for the site. It requires our models and passport. It calls the functions in models in order to create, read, update and delete information from the database. It uses passport in order to authenticate user submitted information. On line 9, the /api/login route is used with the post method and populated with the user inputted information passed from our front-end JavaScript. This information is authenticated using passport. On line 16, the post method is used to call the /api/signup route. The create Sequelize function is used to insert the user inputted email and password into the database. If the information is inserted successfully, the user is brought to the login form. If there is an error, the error status 401 is displayed in the console. On line 30, when the logout route is called, the user is logged out and redirected to the login page. On line 36, when the user_data route is called, the code on line 37 checks if they are logged in. If they arent, an empty object is sent back. If they are, the user email and id are returned. 

This image displays the signup route, in which the User.create function is used to insert a users email and password into the database. This information is passed from the frontend JavaScript.

![API Routes](/public/assets/apiroutes.png)

## html-routes.js
This file contains all html routes for the site, used to display different html files and changing the information displayed. It requires path so that realtive routes can be used. It also requires the middleware isAuthenticated.js in order to check if a user is logged in, controlling what is displayed for logged in and logged out users. on line 9, the base route "/" is used. The if statement starting on 11 controls what is shown for users with an account, and those without. If the user has an account, they are redirected to the /members page. If not, they are directed to the signup page. On line 17, the /login route is used. If the user has an account they are redirected to the /members page. If not they are sent to the login page. On line 27, the isAuthenticated function is used to check if a user is logged in or not. If a user without an account tries to access the /members route they are redirected to the signup page. 

This image displays the code for the login html route. If a user is logged in, it redirects them to the members page. If not, they are sent to the login page. 

![HTML Routes](/public/assets/htmlroutes.png)

## Base_Folder

## server.js
The server.js file sets up our connection using express. It requires express, express-session, passport, and the models folder. Express provides the web framework used to set up the site. Express session creates a session id and saves it as a cookie. It also saves session-data to the database including the date created and date updated. Passport keeps track of a users login status. The model is used to sync the database and display connection status in console. The server code also requires routes to set them up properly.

## package.json
This file contains all of our dependencies. As long as it is included, we can run the command "npm install" to install all required dependencies.

## Additional_Features
Some features that could be added are better error handling for incorrect usernames/passwords, and error handling for inputting the same email multiple times in signup. As it is, entering an incorrect password simply resets the field without letting the user know anything is wrong. An alert or modal popup would be an easy fix for this. Entering the same email in registration will return the error [Object, object], and doesn't tell the what went wrong. You could check this by checking against pre existing usernames in the database. I would also require a user to use a password longer than 8 characters and have at least one uppercase, one lowercase, and one special character. This could be done in the front end javascript using regex and pop up a modal explaining the issue if they do not follow requirements. 