# Telephone Directory Web Application

## Overview
This project is a single-page web application designed to function as a telephone directory. Users can search for contact details based on names, telephone numbers, or locations. The application is built with a PHP backend and a simple HTML/CSS/JavaScript frontend. The backend interacts with a PostgreSQL database to fetch and display contact information.

## Features
- **Search Functionality**: Users can search for contacts by name, telephone number, or location.
- **Dynamic Results**: Search results are displayed dynamically without requiring a page reload.
- **Database Integration**: The application uses a PostgreSQL database to store and retrieve contact information.
- **Responsive Design**: The frontend is designed to be responsive and user-friendly.

## Technologies Used
- **Frontend**: HTML, CSS, JavaScript
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
