# clutteredcode/rethinkdb-alpine

An alpine:latest image with RethinkDB.
The default behavior is to run rethinkdb with a password.
This image will set a password based on environment variables at run time.

## Environment Variables
* **RETHINKDB_PASSWORD:**  
    (defaults to 'admin') The admin user password for the rethnkdb instance.

## Examples
**.env-file**
```bash
RETHINKDB_PASSWORD="super_secure"
```

```bash
docker pull clutteredcode/rethinkdb-alpine
docker run -d --name rethinkdb \
  --env-file "$PWD/.env-file" \
  -p "28015:28015" \
  -p "29015:29015" \
  -p "8080:8080" \
  -v /path/to/data:/data/rethinkdb \
  clutteredcode/rethinkdb-alpine
```
-----------------------
Same as above, but not using an env-file.
```bash
docker pull clutteredcode/rethinkdb-alpine
docker run -d --name rethinkdb \
  -e RETHINKDB_PASSWORD="super-secret" \
  -p "28015:28015" \
  -p "29015:29015" \
  -p "8080:8080" \
  -v /path/to/data:/data/rethinkdb \
  clutteredcode/rethinkdb-alpine
```