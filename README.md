Setup the project:
```sh
$ git clone https://github.com/chalasr/lexikjwt-2.6-sf-3.4
$ cd lexikjwt-2.6-sf-3.4
$ cp .env.dist .env
$ composer install
```

Create the database schema:
```sh
$ php bin/console doctrine:database:create
$ php bin/console doctrine:schema:update --force
```

Run the web server:
```sh
$ php bin/console server:run
```

Register a new user:
```
$ curl -X POST http://localhost:8000/register -d _username=johndoe -d _password=test
-> User johndoe successfully created
```

Get a JWT token:
```
$ curl -X POST -H "Content-Type: application/json" http://localhost:8000/login_check -d '{"username":"johndoe","password":"test"}'
-> { "token": "[TOKEN]" }  
```

Access a secured route:
```
$ curl -H "Authorization: Bearer [TOKEN]" http://localhost:8000/api
-> Logged in as johndoe
```
