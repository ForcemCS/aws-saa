## EC2

### Instance Type

+ General Purpose

  提供计算，内存和网络资源的平衡

+ Compute Optimized

  需要高性能处理器的计算密集型应用

+ Memory Optimized

  处理大数据集的工作负载

+ Storage Optimized

  高IO操作的应用，频繁读写磁盘的应用程序

+ GPU Instance

  利用高性能GPU的应用程序,像机器学习，深度学习的东西

### AMI

可以在启动实例的时候，安装其他内容

同时我们可以在目前启动的实例，创建一个AMI

### Instance lifecycle

<img src="./img/1.png" alt="1" style="zoom:50%;" />

### User Data

<img src="./img/2.png" alt="2" style="zoom:50%;" />

用户数据有16kb的限制

### Security Group

<img src="./img/3.png" alt="3" style="zoom:50%;" />

### Starage with EBS

<img src="./img/4.png" alt="4" style="zoom:50%;" />

### Elastic IP

保留IP

### Launch Template

在auto scaling group中，aws会根据流量的增加动态扩展你的应用程序的EC2数量，为了做到这一点它需要知道，新EC2实例需要什么配置，所以你需要指定一个Lunach Template

### Instance Placements

<img src="./img/5.png" alt="5" style="zoom:50%;" />

### 实例定价

- On Demand

- Spot

- Saving Plans

- Reserved Instances

  承诺固定的一段时间会买多少服务

- Dedicated Hosts

- Dedicated Instances

## EC2 Image Buiider

<img src="./img/6.png" alt="6" style="zoom:50%;" />

允许你自动化创建，管理和部署AMI镜像的服务

Golden Image 包含了所有需要的软件应用和配置

**构建步骤：**

<img src="C:\Users\ForceCS\Desktop\aws-saa\compute\img\7.png" alt="7" style="zoom:50%;" />
