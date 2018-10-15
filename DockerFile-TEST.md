
========== TEST build ==============
```dockerfile
# First Dockerfile
FROM centos
MAINTAINER qingbing "qingbing@qq.com"
RUN mkdir /data && echo "hello world" > /data/hello.txt
EXPOSE 80
```

========== TEST CMD ==============
```dockerfile
# CMD 指令会被 docker run 时指定的指令所覆盖
FROM centos
CMD ["echo", "hello", "world", "this is cmd"]

```

========== TEST ENTRYPOINT ==============
```dockerfile
# ENTRYPOINT 指令如果要被覆盖，需要 docker run --entrypoint="" --name containerName qingbing/test:1.0
FROM centos
ENTRYPOINT ["echo", "hello", "world", "this is entrypoint"]

```

========== TEST CMD&ENTRYPOINT ==============
```dockerfile
FROM centos
# ENTRYPOINT 指定指令
ENTRYPOINT ["echo"]
# CMD 指定参数，这个参数会被docker run 的参数所覆盖
CMD ["hello"]

```

========== TEST ADD ==============
```dockerfile
FROM centos
COPY ./test.txt /Dockerfile
ADD ./test.tar.gz /test


```

========== TEST network ==============
```dockerfile
FROM centos
RUN mkdir -p /data/tmp
COPY ./basic.sh /data/tmp/run.sh
RUN chmod a+x /data/tmp/run.sh
RUN /data/tmp/run.sh
# net-tools for ping
# libcurl for curl
RUN yum -y install net-tools libcurl


```


========== TEST volumes ==============
```dockerfile
# 定义数据卷容器
FROM centos
VOLUME ["/data/web", "/data/git", "/data/mysql"]

```