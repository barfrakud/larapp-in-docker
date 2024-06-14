# larapp-in-docker 
## Tutorial for convert existing Laravel with Livewire application into docker containers

### Create Laravel app from scratch
Install laravel app:
```
composer create-project laravel/laravel app-in-docker
```
Install breeze:
```
composer require laravel/breeze --dev
php artisan breeze:install
livewire-functional
```

Run the application to verify if it works:
```
php artisan serve
```
From this point app is working and ready for dockerization.



### Install Sail 
In Linux terminal in WSL git clone the app:
```
git clone https://github.com/barfrakud/larapp-in-docker.git
```

Install Laravel Sail in linux bash console:
```
composer require laravel/sail --dev
php artisan sail:install
```
The docker-compose file is created.

## Run the app

```
sail up
```
or `sail up -d`  with detached mode

Set alias for sail in bash 
```
nano ~/.bashrc
alias sail='sh $([ -f sail ] && echo sail || echo vendor/bin/sail)'
```

Run migration 
```
sail artisan migrate
```
The app is ready and working.

## Stop containers
```
sail stop
```

Remove containers
```
sail down
```


Na potrzeby 
