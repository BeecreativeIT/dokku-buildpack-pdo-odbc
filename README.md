# dokku-buildpack-pdo-odbc

Buildpack per compilare l'estensione PHP PDO_ODBC in Dokku/Heroku.

## Prerequisiti

Nel progetto deve esserci un file `Aptfile`:

unixodbc
unixodbc-dev
libaio1t64
libaio-dev


## Come usarlo in Dokku

dokku buildpacks:add myapp --index 1 https://github.com/heroku/heroku-buildpack-apt
dokku buildpacks:add myapp --index 2 https://github.com/tu-utente/dokku-buildpack-pdo-odbc
dokku buildpacks:add myapp --index 3 https://github.com/heroku/heroku-buildpack-php


## Verifica

Dentro la shell dell'app:

dokku run myapp php -m | grep odbc


Risultato atteso:

pdo_odbc
odbc

Ora l'app può usare:

$pdo = new PDO("odbc:DSN=HANA", $user, $pass);

