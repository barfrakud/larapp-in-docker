# Dockerizing a Laravel Application with Livewire - larapp-in-docker 
This tutorial will guide you through the process of converting an existing Laravel application with Livewire into Docker containers.

## Creating a Laravel Application from Scratch

1. **Install Laravel:**
   Use the following command to create a new Laravel application:
   ```
   composer create-project laravel/laravel app-in-docker
   ```

2. **Install Breeze:**
   Execute the following commands to install Laravel Breeze:
   ```
   composer require laravel/breeze --dev
   php artisan breeze:install
   npm install && npm run dev
   ```

3. **Verify the Installation:**
   Run the application to ensure it's working correctly:
   ```
   php artisan serve
   ```

At this point, the application is ready for Dockerization.

## Installing the Application

1. **Clone the Application:**
   In the Linux terminal in WSL, clone the application using the following command:
   ```
   git clone https://github.com/barfrakud/larapp-in-docker.git
   ```

2. **Update Environment Variables:**
   Modify the `.env` file as per your application's requirements.

## Setting Up the Environment

1. **Install PHP:**
   Use the following commands in the WSL Linux terminal to install PHP:
   ```
   sudo add-apt-repository ppa:ondrej/php
   sudo apt update
   sudo apt upgrade
   sudo apt install php8.2
   ```
   Verify the installation using `php -v` and check the configuration with `php.ini`.

2. **Install Composer:**
   If Composer is not already installed, you can check using `composer -v`.

3. **Install Dependencies:**
   Use the following commands to install the necessary PHP extensions and dependencies:
   ```
   sudo apt-get install php8.2-dom
   sudo apt-get install php8.2-xml
   composer install
   ```

## Dockerizing the Application with Laravel Sail

1. **Install Laravel Sail:**
   If Laravel Sail is not already installed, use the following commands to install it:
   ```
   composer require laravel/sail --dev
   php artisan sail:install
   ```
   This will create a `docker-compose` file.

2. **Build the Docker Image:**
   Use the following command to build the Docker image:
   ```
   sail build --no-cache
   ```

## Running the Application Using Sail

1. **Start the Application:**
   Use the following command to start the application:
   ```
   sail up
   ```
   Alternatively, you can run the application in detached mode using `sail up -d`. Check the running containers with `docker ps -a`.

2. **Generate Application Key:**
   Use the following command to generate a new application key:
   ```
   sail artisan key:generate
   ```

3. **Install and Build NPM Packages:**
   Use the following commands to install and build the NPM packages:
   ```
   sail npm install
   sail npm run dev
   ```

4. **Run Database Migrations:**
   Use the following command to run the database migrations:
   ```
   sail artisan migrate
   ```

At this point, the application is ready to use.

## Setting Sail Alias

1. **Create an Alias for Sail:**
   Open the `.bashrc` file and add the following alias for Sail:
   ```
   nano ~/.bashrc
   alias sail='bash vendor/bin/sail'
   ```

## Stopping and Removing Containers

1. **Stop the Containers:**
   Use the following command to stop the running containers:
   ```
   sail stop
   ```

2. **Remove the Containers:**
   Use the following command to remove the containers:
   ```
   sail down
   ```

Your Laravel application with Livewire is now successfully dockerized and ready for use.
