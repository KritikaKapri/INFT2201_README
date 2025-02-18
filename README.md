Telephone Directory - Single Page Application (SPA) & Web Service

This repository contains a Single Page Application (SPA) for a Telephone Directory that allows users to search contacts by name, telephone number, or address. The web service interacts with a PostgreSQL database to retrieve contact information based on user queries.

Introduction
The Telephone Directory SPA provides a simple user interface for searching contact information. The web service handles the logic for querying the database and returning the results to the frontend.

Technologies
Frontend: HTML, CSS, JavaScript (Fetch API)
Backend: PHP (with PostgreSQL)
Database: PostgreSQL
Web Server: Apache 

Setup Instructions
Install PostgreSQL: If you don't have PostgreSQL installed, you can follow the instructions for your operating system:

PostgreSQL Installation Guide
Create Database: Create a PostgreSQL database to store the contacts:

sql
Copy code
CREATE DATABASE telephone_directory;
Configure Database:

Create a table called contacts with the following schema:
sql
Copy code
CREATE TABLE contacts (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    telephone VARCHAR(20),
    address VARCHAR(255),
    city VARCHAR(100),
    state VARCHAR(100),
    postal_code VARCHAR(20),
    category VARCHAR(100),
    tags TEXT[]
);
Configure PHP:

Ensure you have PHP installed with PostgreSQL support.
If needed, install PHP and the PostgreSQL PHP extension:
bash
Copy code
sudo apt-get install php php-pgsql

Setup the folder in the apache/htdocs folder. Name it telephone_directory.
Setup the db.php file: In the db.php file, ensure your database connection settings are correct:

php
Copy code
$host = '127.0.0.1';
$port = '5432';
$dbname = 'telephone_directory';
$user = 'postgres';
$password = 'your-password';

Install Apache if you have not already.

Place files in the web root directory:
Place all project files (including api.php, index.html, db.php, etc.) in your web server's root directory

Test the Web Service:
Navigate to http://localhost/telephone_directory/index.html in your web browser.
The search input should be displayed. Test by entering a search term (e.g., "John").

Frontend (SPA) Setup
Ensure that the frontend files (index.html, CSS, and JavaScript) are placed correctly in the web server's root directory (as mentioned above).

Open the index.html file in a web browser:
The SPA should load and allow users to search for contacts.

Test the SPA:
Enter a search query (e.g., "John") into the input field, and verify that it displays the matching contacts fetched from the web service.

Navigate to your localhost (e.g., http://localhost/telephone_directory/index.html) and verify that the application is running correctly.

User Guide
Searching for Contacts
Search by Name:
Enter the name of the contact (e.g., "John Doe") in the search input field and press the "Search" button.
The results will be displayed below, showing contacts that match the search query.

Search by Phone Number:
You can also search using phone numbers (e.g., "123-456-7890").

Search by Address:
You can search by address (e.g., "123 Main St").

View Results:
If matching contacts are found, their details (name, phone number, address, etc.) will be displayed in a clean card format.

Error Handling:
If no contacts are found or an error occurs, appropriate error messages will be displayed."# INFT2201_README" 
