# Telephone Directory Web Application

## Overview
This project is a single-page web application designed to function as a telephone directory. Users can search for contact details based on names, telephone numbers, or locations. The application is built with a PHP backend and a simple HTML/CSS/JavaScript frontend. The backend interacts with a PostgreSQL database to fetch and display contact information.

## Features
- **Search Functionality**: Users can search for contacts by name, telephone number, or location.
- **Dynamic Results**: Search results are displayed dynamically without requiring a page reload.
- **Database Integration**: The application uses a PostgreSQL database to store and retrieve contact information.
- **Responsive Design**: The frontend is designed to be responsive and user-friendly.

## Technologies Used
- **Frontend**: HTML
- **Backend**: PHP
- **Database**: PostgreSQL
- **Web Server**: Apache or any PHP-supported web server

## Database Schema
The database schema for the application is as follows:

```sql
CREATE TABLE contacts (
    id SERIAL PRIMARY KEY,  -- Unique identifier for each contact
    name VARCHAR(255) NOT NULL,  -- Contact's name
    telephone VARCHAR(20) UNIQUE NOT NULL,  -- Unique phone number
    address TEXT NOT NULL,  -- Full address
    city VARCHAR(100) NOT NULL,  -- City for faster location-based searches
    state VARCHAR(100),  -- Optional: State/Province for broader location searches
    postal_code VARCHAR(20),  -- Optional: Postal Code for precise filtering
    category VARCHAR(50) CHECK (category IN 
        ('Business', 'Personal', 'Emergency', 'Restaurant', 'Hospital', 'Other')),  
    tags TEXT[]  -- Array of additional tags for flexible categorization
);

CREATE INDEX idx_contacts_name ON contacts(name);  -- Speeds up name searches
CREATE INDEX idx_contacts_telephone ON contacts(telephone);  -- Optimizes number lookups
CREATE INDEX idx_contacts_city ON contacts(city);  -- Efficient location-based search
```
## Populate the database
Populate the database with users and their relevant information.

# Installation and Setup

## Prerequisites
- **PHP**: Ensure PHP is installed on your server.
- **PostgreSQL**: Ensure PostgreSQL is installed and running.
- **Web Server**: Apache or any web server that supports PHP.

## Setup Instructions

1. Create a folder named `telephone_directory` inside the Apache `htdocs` directory.
2. Inside the `telephone_directory` folder, create the following files:

   - **index.html**: The main HTML file that contains the frontend interface.
   - **api.php**: The PHP script that handles the search requests and interacts with the database.
   - **db.php**: The PHP script that contains the database connection logic.

### Set Up the Database:
1. Create a new PostgreSQL database named `telephone_directory` in pgAdmin.
2. Run the provided SQL schema to create the `contacts` table and indexes.
3. Populate the `contacts` table with sample data.

## Configure the Database Connection:
Open the `db.php` file and update the database connection details:
```php
$host = '127.0.0.1';
$port = '5432';
$dbname = 'telephone_directory';
$user = 'postgres';
$password = 'your-password';
```

### Deploy the Application:
1. Place the PHP and HTML files in the root directory of your web server.
2. Ensure the web server is configured to serve PHP files.

### Access the Application:
Open a web browser and navigate to the application's URL (e.g., `http://localhost/telephone_directory`).
# Usage

### Search for Contacts:
1. Enter a search query (name, telephone number, or location) in the search bar.
2. Click the "Search" button to display the results.

### View Results:
- The search results will be displayed dynamically below the search bar.
- Each result will show the contact's name, telephone number, address, city, state, postal code, category, and tags.

# Code Structure

- **index.html**: The main HTML file that contains the frontend interface.

- **api.php**: The PHP script that handles the search requests and interacts with the database.

- **db.php**: The PHP script that contains the database connection logic.


# Troubleshooting

## Database Connection Issues:
- Ensure that the PostgreSQL server is running.
- Verify that the database credentials in `db.php` are correct.
- Check the PostgreSQL logs for any connection errors.

## Search Not Returning Results:
- Ensure that the `contacts` table is populated with data.
- Verify that the search query matches the data in the database.

## PHP Errors:
- Check the PHP error logs for any issues.
- Ensure that the PHP version is compatible with the code.

## Conclusion

This telephone directory application is a simple yet effective tool for searching and managing contact information. It demonstrates the integration of a PHP backend with a PostgreSQL database and a responsive frontend. Feel free to extend the functionality or customize the design to suit your needs.
