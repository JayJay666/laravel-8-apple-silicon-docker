
# Laravel 8.x for Apple Silicon Docker
Modified Docker Compose for Laravel Sail runnable on Apple Silicon chips
___
Whats get in this docker-compose.yml
 - Laravel Sail Runtimes v8.0
 - MySQL v8.0
 - phpmyadmin
 - redis
 - mailhog
 - selenium

Documentation
----
Same as [original documentation](https://laravel.com/docs/8.x#getting-started-on-macos)

If you're developing on a Mac and [Docker Desktop](https://www.docker.com/products/docker-desktop) is already installed, you can use a simple terminal command to create a new Laravel project. For example, to create a new Laravel application in a directory named "example-app", you may run the following command in your terminal:

```bash
curl -s "https://laravel.build/example-app" | bash
```

Of course, you can change "example-app" in this URL to anything you like. The Laravel application's directory will be created within the directory you execute the command from.

After project has been created **override original docker-compose.yml** with modified [docker-compose.yml](https://github.com/JayJay666/laravel-8-apple-silicon-docker/blob/main/docker-compose.yml) in this repo.

After then you can navigate to the application directory and start Laravel Sail. Laravel Sail provides a simple command-line interface for interacting with Laravel's default Docker configuration:

```bash
cd example-app

./vendor/bin/sail up
```

However, instead of repeatedly typing  `vendor/bin/sail`  to execute Sail commands, you may wish to configure a Bash alias that allows you to execute Sail's commands more easily:

```bash
alias sail='bash vendor/bin/sail'
```

Issue
----
Probably if you does not have image of MySQL downloaded already, you gat error like: 

`Docker (Apple Silicon/M1 Preview) MySQL “no matching manifest for linux/arm64/v8 in the manifest list entries”`

If you get MySQL error, you must modify docker-compose.yml with 
```yml
services:
    mysql:  
        platform: linux/x86_64
        image: 'mysql:8.0'
        ...
```
or
```yml
services:
     mysql:
         image: 'mariadb:latest'
         ...
```
