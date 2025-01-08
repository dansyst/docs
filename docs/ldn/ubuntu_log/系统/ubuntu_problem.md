<!-- 说明 -->
- **Ubuntu踩坑记录**

## Ubuntu 查看磁盘情况

### 1. 用Ubuntu启动U盘进入Ubuntu安装界面

![image-20250106103327449](./Ubuntu_problem001.assets/image-20250106103327449.png)

![image-20250106103847778](./Ubuntu_problem001.assets/image-20250106103847778.png)

![image-20250106103917653](./Ubuntu_problem001.assets/image-20250106103917653.png)

### 2. 进入命令行查看磁盘情况

![image-20250106103943354](./Ubuntu_problem001.assets/image-20250106103943354.png)

**sudo fdisk -l**

查看磁盘情况

![image-20250106102849486](./Ubuntu_problem001.assets/image-20250106102849486.png)

列出磁盘详细信息

![image-20250106104346463](./Ubuntu_problem001.assets/image-20250106104346463.png)

查看磁盘内存

![image-20250106104431638](./Ubuntu_problem001.assets/image-20250106104431638.png)

**sudo  mount  /dev/nvme0n1p1   /mnt   -v**

查看磁盘p1的情况

![image-20250106110832614](./Ubuntu_problem001.assets/image-20250106110832614.png)

**find /mnt**

**ls /mnt**

![image-20250106111018541](./Ubuntu_problem001.assets/image-20250106111018541.png)

![image-20250106111047908](./Ubuntu_problem001.assets/image-20250106111047908.png)

同理，查看p6的情况

**sudo  mount  /dev/nvme0n1p6   /media  -v**

**ls /media**

![image-20250106111356608](./Ubuntu_problem001.assets/image-20250106111356608.png)

**sudo gparted**

![image-20250106111425499](./Ubuntu_problem001.assets/image-20250106111425499.png)









