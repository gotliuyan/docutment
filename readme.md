# kubeadm 安装kubernetes 集群

```bash
kubeadm init --apiserver-advertise-address 47.98.107.25 \ #指定apiserver ip，一般为内网IP
--apiserver-cert-extra-sans IP \ #指定apiserver 外网IP
--pod-network-cidr 192.168.0.1/16 \ #指定pod网络
```
