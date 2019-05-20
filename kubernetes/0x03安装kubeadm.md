# 安装Kubeadm

[官方文档-Bootstrapping Clusters with kubeadm](https://kubernetes.io/docs/setup/independent/install-kubeadm/)

## 添加yum源

### 添加kubernetes源

```bash
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
exclude=kube*
EOF

# Set SELinux in permissive mode (effectively disabling it)
setenforce 0
sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

yum install -y kubelet kubeadm kubectl --disableexcludes=kubernetes

systemctl enable --now kubelet
```

### 添加docker-ce源

```bash 
wget https://download.docker.com/linux/centos/docker-ce.repo 
```

****

## 安装 docker-ce

* 安装 docker

> yum install docker-ce

* 添加私有镜像仓库和日志配置

> vi /etc/docker/daemon.json

**添加以下配置**

```bash
{ "insecure-registries":["192.168.1.29"],
    "log-opts": {
		"max-size": "10m",
		"max-file":"5",
		"labels": "somelabel",
		"env": "os,customer"
	}
}
```
