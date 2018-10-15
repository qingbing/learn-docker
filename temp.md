echo "Asia/Shanghai" > /etc/timezone
echo "8.8.8.8" >> /etc/resolv.conf
echo "8.8.4.4" >> /etc/resolv.conf
yum update
yum install -y wget
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
yum repolist
rpm -ivh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm


