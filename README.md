# REST API for User Registration with Email Sending

This project implements a RESTful API using Laravel 10 framework to handle user registration and send welcome emails using the Gmail API. It also utilizes php-open-source-saver/jwt-auth for API request handling and Laravel Queue for scheduling email sending.

## Requirements

- Laravel 10
- php-open-source-saver/jwt-auth
- Google API Client for connecting Gmail API console
- Docker

## Setup Instructions

### 1. Clone the Repository

```
git clone <repository_url>
cd <repository_directory>
```
### 2. Install Dependencies and Generate App Key

```
composer install
```
```
php artisan key:generate
```
### 3. Set Environment Variables
Create a copy of the .env.example file and name it .env. Update the following variables with your configurations:

- Database settings (DB_CONNECTION, DB_HOST, DB_PORT, DB_DATABASE, DB_USERNAME, DB_PASSWORD)
- Gmail API settings for email sending (GMAIL_CLIENT_ID, GMAIL_CLIENT_SECRET, GMAIL_REDIRECT_URL)
- JWT Secret

### 4. Generate JWT Secret
Generate JWT secret by running the following command:

```
php artisan jwt:secret
```

### 5. Run Migrations

```
php artisan migrate
```
### 6. Set Up Gmail API Credentials
- Go to Google API Console and create a new project.
- Enable the Gmail API for the project.
- Create credentials (OAuth 2.0 client ID) and download the JSON file.
- Copy client_id, client_secret and client_redirect_url and add into .env file (GMAIL_CLIENT_ID, GMAIL_CLIENT_SECRET, GMAIL_REDIRECT_URL)

### 7. Start Docker Containers
Build and run Docker containers using Docker Compose:

```
docker-compose up --build
```
### 8. Access API Endpoints
Once the containers are running, the API will be accessible at http://localhost:8000.

- POST /api/auth/register: Register a new user by providing their email address. A welcome email will be sent to the registered email address.

### Usage
- Register a user by sending a POST request to /api/register with the following JSON payload:

```
{
  "email": "user@example.com"
}
```
- Upon successful registration, a welcome email will be sent to the provided email address.

### Additional Notes
- Make sure to handle error cases gracefully and secure sensitive information properly.
- For testing purposes, you can use tools like Postman or cURL to send requests to the API endpoints.

### Contributors
- Md Ashikur Rahman

### License
This project is licensed under the MIT License.
