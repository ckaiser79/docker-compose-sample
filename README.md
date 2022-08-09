
# Build external container

Start a plain JBoss

```powershell
docker run `
    -p 9990:9990 -p 8080:8080 `
    -it quay.io/wildfly/wildfly `
    /opt/jboss/wildfly/bin/standalone.sh `
    -b 0.0.0.0 -bmanagement 0.0.0.0
```

JBoss with configuration scripts

```powershell
cd wildfly-configured
$imageConfiguredName = 'local/wildfly-configured'
docker build . --tag $imageConfiguredName

# Run it
docker run -p 9990:9990 -p 8080:8080 -it $imageConfiguredName
```

# Composed Network

Start a network

```powershell
# create a volume for redis
docker volume create redis-data
docker volume inspect redis-data

# start the environment
cd environment
docker-compose up
```

# Utilities

```powershell
# cleanup script for alle containers and images
docker ps -aq | ForEach-Object { docker rm $_ --force }
docker images -aq | ForEach-Object { docker rmi $_ --force }
```
