# Deployment to Dokku

### On the server

* Install [dokku](https://dokku.com/)
* Install the [postgres plugin](https://github.com/dokku/dokku-postgres).
* Install the [letsencrypt plugin](https://github.com/dokku/dokku-letsencrypt)
* Install the [redis plugin](https://github.com/dokku/dokku-redis)
* Create a postgis database&#x20;

```
dokku postgres:create wazimap-db \
-i kartoza/postgis \
-p <database user password> \
-r <root password> \
-I 11.0-2.5 \
-C "POSTGRES_MULTIPLE_EXTENSIONS=postgis,pg_trgm;POSTGRES_USER=postgres;POSTGRES_PASS=<database user password>"
```

* Create a redis database

```
dokku redis:create wazimap-redis
```

* Create a dokku app&#x20;

```
dokku apps:create wazimap
```

* Link the postgres and redis databases to the app&#x20;

```
dokku postgres:link wazimap-db wazimap
dokku redis:link wazimap-redis wazimap
```

* Change the database url to use postgis instead of postgres&#x20;

```
NEW_URL=$(dokku config:get wazimap DATABASE_URL | sed 's/^postgres/postgis/') dokku config:set wazimap DATABASE_URL=$NEW_URL
```

* Setup some environment variables

```
dokku config:set wazimap \
    AWS_ACCESS_KEY_ID=<access key id> \
    AWS_S3_REGION_NAME=<region name> \
    AWS_SECRET_ACCESS_KEY=<secret key> \
    AWS_STORAGE_BUCKET_NAME=<storage bucket> \
    DEFAULT_FILE_STORAGE=storages.backends.s3boto3.S3Boto3Storage \
    DJANGO_CONFIGURATION=Production \
    DJANGO_DEBUG=False \
    DJANGO_SECRET_KEY=<django secret key>
```

* Setup the domain and SSL certificates

```
dokku domains:add wazimap wazimap.com
dokku letsencrypt:enable wazimap
```

* Setup the appropriate proxy ports:

```
# Wazimap does not listen on port 5000 by default
echo dokku proxy:ports-add wazimap http:80:8000
dokku proxy:ports-add wazimap https:443:8000
dokku proxy:ports-remove wazimap http:80:5000
dokku proxy:ports-remove wazimap https:443:5000
```

Make sure that large uploads are allowed:

```
dokku nginx:set wazimap client-max-body-size 100m
```

### On your local machine

* Add a git remote for deployment `git remote add dokku:wazimap`
* Deploy `git push dokku staging:master` (if deploying the staging branch)

