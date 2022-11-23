I was trying to set this up quickly but turn out i learnt a whole heap about the new docker stack, network overlay, etc... 

### Steps to deploy

generate a self-signed cert or grab cert from cloudflare

```bash
mkdir certs
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout certs/key.pem -out certs/cert.pem
```

Create an .env file with the following content:

```bash
MYSQL_ROOT_PASSWORD={ROOT password for MYSQL}
MYSQL_USER=wordpress
MYSQL_PASSWORD={Password for wordpress db}
WORDPRESS_DB_PASSWORD={Password for wordpress db}
WORDPRESS_DB_USER=wordpress
WORDPRESS_DB_HOST=db:3306
WORDPRESS_DB_NAME=wordpress
```

Deploy the docker stack

```bash
docker stack deploy -c stack.yml cecoteksan
```

