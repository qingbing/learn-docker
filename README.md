# learn-docker
docker 学习记录

# 使用国内的镜像仓库
```text
1. 修改： /etc/default/docker
2. 添加： DOCKER_OPTS="registry-mirror=http://mirror-addr"
http://www.daocloud.io中注册使用，以收费
```

# Remote API 参考网址
https://docs.docker.com/reference/

# docker 几个命令
- docker version
- docker info
- systemctl status docker : 查看docker守护进程的运行状态
- systemctl start docker
- systemctl restart docker
- systemctl stop docker

# 删除所有的docker 容器
docker rm $(docker ps -a | sed -n '2,$'p | awk '{print $1}')

# 删除所有标签为<none>的docker镜像
docker rmi $(docker images | grep '<none>' | sed -n '1,$'p | awk '{print $3}')


# 客户端远程访问docker 服务器守护进程
- 1、服务器开启tcp的socket协议
- 2、客户端中docker的client的remoteApi版本信息必须和服务器的server的remoteApi版本信息一致
- 3、客户端访问server ： docker -H tcp://192.168.146.200:2375 info
- 4、在客户端中像本机一样使用server
  - client 添加环境变量 ： export DOCKER_HOST="tcp://192.168.146.200:2375"
  - 然后就可以向使用本地一样使用server了
  - 重新连接本地： export=""



# docker 启动
- docker -d [Options]
  - 运行相关
    - -D, --debut=false : debug模式是否开启
    - -e, --exec-dirver="native" : 运行时使用的驱动模式
    - -g, --graph="/var/lib/docker" : docker的目录
    - --icc=true : 
    - -l, --log-level="info" : 日志级别
    - -label=[] : 
    - -p, --pidfile="/var/run/dicker.pid" : 进程ID
  - docker服务器连接相关
    - -G, --group="docker"
    - -H, --host=[]
    - -tls=false
    - --tlscacert="/home/sven/.docker/ca.pem"
    - --tlscert="/home/sven/.docker/cert.pem"
    - --tlskey="/home/sven/.docker/key.pem"
    - --tlsverify=false
  - RemoteAPI 相关
    - --api-enable-cors=false
  - 存储相关
    - -s, --storage-driver=""
    - -s, --selinux-enabled=false
    - -s, --storage-opt=[]
  - Registry 相关
    - --insecure-registry=[]
    - --registry-mirror=[]
  - 网络设置相关
    - -b,--bridge=""
    - --bip=""
    - --fixed-cidr=""
    - --fixed-cidr-v6=""
    - --dns=[]
    - --dns-search=[]
  - 网络设置相关
    - --ip=0.0.0.0
    - --ip-forward=true
    - --ip-masq=true
    - --iptables=true
    - --ipv6=true
    - --mtu=0
    







remote api 怎么访问