# Reverse Engineering Code 

## Description
This application consists of a login, sign up, and members html page, that save user information to a MySQL database. It allows users to sign up for an account using an email address and password, hashes that password using Bcrypt and saves the hashed password to the database so that nobody can read it. After an account is created, it allows you to login using that email and password combination. If a user tries to navigate to the members page and is not logged in, it redirects them back to the sign up page.

 A walkthrough of the code is contained in the walkthrough file in this directory.

 [Walkthrough](https://github.com/jsp117/Reverse-Engineering-Code/blob/main/walkthrough.md)
  
## Table of Contents
* [Description](#description)
* [Installation](#installation)
* [Usage](#usage)
* [Built With](#built-with)
* [Contributors](#contributors)
* [Author](#author)
* [License](#license)

## Installation

To install all dependencies, run Npm install in your terminal while opened to the file path you downloaded to. 

## Usage

To run this application, open your terminal to the folder it is located in and type "npm install". When those files are finished downloading type "node server.js" to run the application. Type in an email address with the format "text@host.com" and a password to create an account. After creating account, you may log in using that email and password combination. 

![GIF of Usage](/public/assets/passport.gif)

## Built With

* JavaScript
* HTML
* [MySQL](https://www.mysql.com/)
* [Express](https://expressjs.com/)
* [Passport](https://www.npmjs.com/package/passport)
* [Sequelize](https://sequelize.org/)
* [Bcrypt](https://www.npmjs.com/package/bcrypt)
* [NodeJS](https://nodejs.org/en/)
* [Github](https://github.com/)

## Contributors

My instructor Roger Le, Jerome, and Teaching assistants Manuel and Kerwin.
  
## Author

Jonathan SanPedro - Bachelors of Information Technology at Rutgers New Brunswick - Student at Berkeley Coding Bootcamp
  
![Github Profile Picture](https://github.com/jsp117.png?size=150)

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

MIT License

Copyright &copy; [2020] [Jonathan J. SanPedro]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.