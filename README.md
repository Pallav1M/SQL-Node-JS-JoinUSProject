# SQL-Node-JS-JoinUsProject

This simple project demonstrates how the application is connected to the database through NodeJS Server. This application will showcase both selection and insertion of information.  

This is built using a <strong>GoormIDE container</strong>

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

// To estalish connection with sql server </br>
// =====================================

var connection = mysql.createConnection({
  host     : 'localhost',
  user     : 'root',
  database : 'join_us'
});

Create a sql file and create a user table with email and created_at. 

Run the sql file from the sql terminal using source schema.sql

<strong>To add random data -</strong> 

// var person = {
//     email: faker.internet.email(),
//     created_at: faker.date.past()
// };
 
// var end_result = connection.query('INSERT INTO users SET ?', person, function(err, result) {
//   if (err) throw err;
//   console.log(result);
// });

To add 500 rows, we use the following command

var data = [];
for(var i = 0; i < 500; i++){
    data.push([
        faker.internet.email(),
        faker.date.past()
    ]);
}
 
 
var q = 'INSERT INTO users (email, created_at) VALUES ?';
 
connection.query(q, [data], function(err, result) {
  console.log(err);
  console.log(result);
});
 
connection.end();
