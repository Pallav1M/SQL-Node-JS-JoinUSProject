# SQL-Node-JS-JoinUsProject

This simple project demonstrates how the mailing list application is connected to the database through NodeJS Server. This application will showcase both selection and insertion of information.  

This is built using a <strong>GoormIDE container</strong>

Please view all files from the container under https://goor.me/9XD7Z

To view the result, type node app.js from under the Join_Us folder

Then Project --> Running URL and Port and click on the run icon (between the url and the copied icon). Enter an email id followed by the "Join Now" button to see the count update. 

To validate this as a SQL query, go to the SQL terminal by opening a new terminal and typing 
mysql-ctl cli

<strong>Note</strong> Make sure you are using the Join_us databases

Show databases;
use join_us;

select * from users order by created_at desc limit 1;

You should see the most recently added email id. 

<strong> Details </strong>

The first goal is for NodeJS to randomly generate and insert 500+ users into the database with all unique emails. 

<strong>Faker</strong>

This uses Faker package - this will randomly generate data. 

Run this command in the terminal to install the package:

npm install @faker-js/faker --save-dev

This will generate a Faker package under node_modules

Enter this code in your file (app.js) to require it:

const { faker } = require('@faker-js/faker');

<strong>MYSQL Package</strong>

<strong>Connecting Node and MySQL</strong> 

Run the following command to control MySQL from the terminal.

mysql-ctl start

<strong>Note</strong> - Now, open a new terminal and connect to cli

Run the following command 

mysql-ctl cli

This will open the SQL command line. 

Next in the other terminal, install the SQL package. 

npm install sql;

To establish a connection with the database, incude the following in app.js file. 

var mysql = require('mysql');

To estalish connection with sql server </br>
=====================================

var connection = mysql.createConnection({</br>
  host     : 'localhost',</br>
  user     : 'root',</br>
  database : 'join_us'
});

Create a sql file and create a user table with email and created_at. 

Run the sql file from the sql terminal using source schema.sql

<strong>To add random data -</strong> 

var person = {</br>
email: faker.internet.email(),</br>
     created_at: faker.date.past()</br>
 };
 
 var end_result = connection.query('INSERT INTO users SET ?', person, function(err, result) {</br>
   if (err) throw err;</br>
   console.log(result);</br>
 });

To add 500 rows, we use the following command

var data = [];</br>
for(var i = 0; i < 500; i++){</br>
    data.push([</br>
        faker.internet.email(),</br>
        faker.date.past()</br>
    ]);
}
  
var q = 'INSERT INTO users (email, created_at) VALUES ?';
 
connection.query(q, [data], function(err, result) {</br>
  console.log(err);</br>
  console.log(result);</br>
});
 
connection.end();

<strong>Express (Framework used for Node)</strong>

Run npm init (installs the  package.json file used for express)

Under the Join_Us(newly created folder), create app.js file

Go to the directory using cd 

Next install express, faker, and sql 

npm install express --save (save will save it in the package.json file)

npm install faker sql --save 

<strong>Integrate Express WebApp with MySQL</strong>

To view result - 

<img width="1200" alt="Screen Shot 2022-10-07 at 12 25 35 PM" src="https://user-images.githubusercontent.com/70488044/194638933-247d107e-3864-4c23-9369-dc9f1d434f16.png">

<strong>Adding EJS Template</strong>

(allows you to embed JS inside of it) 

npm install ejs --save 

Next, create a new folder Views, and under Views, create home.ejs.

Validate if everything works fine by inserting a data and seeing if it reflects in the app.

<strong>Connecting the form</strong>

We need to define a post route




