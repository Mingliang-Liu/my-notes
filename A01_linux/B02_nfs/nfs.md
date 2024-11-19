# NFS
## 服务端
```
sudo apt install nfs-kernel-server

sudo vim /etc/exports
/path/to/hard/drive *(rw,sync,no_subtree_check)
其中，/path/to/hard/drive 是你要共享的硬盘的路径。* 表示允许所有主机访问。可以根据需要调整权限和其他选项。

sudo systemctl restart nfs-kernel-server
```
## 客户端
```
sudo apt update
sudo apt install nfs-common

sudo mkdir /mnt/server_64_nfs
sudo chown lthpc:lthpc /mnt/server_64_nfs
sudo chown sensetime:sensetime /mnt/server_64_nfs

sudo mount -t nfs 10.4.196.64:/mnt/rs_data_2 /mnt/server_64_nfs
```

## 自动挂载
```
sudo vim /etc/fstab

10.4.196.64:/mnt/rs_data_2 /mnt/server_64_nfs nfs defaults 0 0

sudo mount -a
```

```
https://blog.csdn.net/u011308433/article/details/135644242
```

## 批量挂载
```
sudo apt install -y nfs-common && \
sudo mkdir /mnt/server_64_nfs && \
sudo chown sensetime:sensetime /mnt/server_64_nfs && \
sudo sed -i "$ a 10.4.196.64:/mnt/rs_data_2 /mnt/server_64_nfs nfs defaults 0 0" /etc/fstab  && \
sudo mount -a && \
cd /mnt/server_64_nfs && ls
```