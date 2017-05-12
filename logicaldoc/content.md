# What is LogicalDOC ?

The LogicalDOC is a flexible and highly performant Document Management System platform.

%%LOGO%%

# How to use this image

## Start a LogicalDOC instance linked to a MySQL container

### 1. Run the MySQL container

```console
$ docker run -d --name=mysql-ld --env="MYSQL_ROOT_PASSWORD=mypassword" --env="MYSQL_DATABASE=logicaldoc" --env="MYSQL_USER=ldoc" --env="MYSQL_PASSWORD=changeme" mysql
```

### 2. Run the LogicalDOC container

```console
docker run -d -p 8080:8080 --env LDOC_USERNO=<your userno> --link mysql-ld logicaldoc/logicaldoc
```

This image includes EXPOSE 8080 (the logicaldoc port). The default LogicalDOC configuration is applied.

The LogicalDOC DMS is accessible at http://${DOCKER_HOST}:8080/ and default User and Password are **admin** / **admin**.

## Your UserNo

You can pass a LogicalDOC activation code (the UserNo) when you launch this image. In this way when your run the image the first time the activation procedure will be completed automatically and you will have a system completely setted up (ready-to-go). If you need an activation code, you can get one delivered to your email by filling-out the form at https://www.logicaldoc.com/product/free-trial

## Start a LogicalDOC with some settings

```console
docker run -d -p 8080:8080 -p 1000:22 --env LDOC_USERNO=<your userno> --env LDOC_MEMORY=4000 --link mysql-ld logicaldoc/logicaldoc
```

This will run the same image as above but with 4000 MB memory allocated to LogicalDOC, moreover it opens the SSH access through port 1000. This image includes EXPOSE 8080 (the logicaldoc port). The default LogicalDOC configuration is applied. The LogicalDOC DMS is accessible at http://${DOCKER_HOST}:8080/ and default User and Password are **admin** / **admin**.