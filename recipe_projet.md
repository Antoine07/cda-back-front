```bash
# vérifie la configuration de votre machine pour SF
 symfony check:requirements 

 # api platform
 composer require api

# démarrer le serveur dans l'app
symfony serve --no-tls

 ```

 - installer la bd

`.env` de SF

```txt
DATABASE_URL="postgresql://admin:password@127.0.0.1:5432/tree-learning-api?serverVersion=16&charset=utf8"
```

- création de la bd

```bash
php bin/console doctrine:database:create
```