## RDS

AWS支持多种数据库引擎（MySQL, PostgreSQL, MariaDB,Oracle, Microsoft SQL Server）

**实例类型:**

+ General Purpose
+ Memory Optimized

**部署模式：**

+ 单实例

+ Multi-AZ Instance

  <img src="./img/2.png" alt="1" style="zoom:50%;" />

  

  + 读取副本是数据库实例的只读副本
  + 通过将应用程序的查询路由到读取副本，减少主数据库实例的负载。
  + 对于读取量大的数据库工作负载，可弹性扩展，超出单个数据库实例的容量限制。
  + 将读取副本升级为独立实例，作为主数据库实例发生故障时的灾难恢复解决方案。

  **支持跨region读副本,主库在新加坡，但是读副本可以在上海**

+ Multi-AZ Cluster

  <img src="./img/3.png" alt="3" style="zoom:50%;" />

  我们有一个主节点可以进行读写操作，我们还将数据复制到一个读副本， 以便我们可以将读请求分配给多个实例，从而减轻主数据库的负载

  然后我们还在另一个可用区有一个备用服务器，以防止主数据库宕机

  **此外我们还将数据复制到另一个region，所以特定的用户可以就近读取副本**

+ 蓝/绿部署

  <img src="./img/4.png" alt="4" style="zoom:50%;" />

  由于数据在两个环境之间是同步的，一但我们确定绿色环境运行正常而且没有问题，我们就可以将客户转移到green环境作为生产

  **限制：**

  + 蓝绿环境必须在同一个AWS账户

**存储类型：**

+ 通用型SSD

  适用于开发/测试环境

+ Provisioned IOPS SSD

  Provisioned IOPS 存储旨在满足 I/O 密集型工作负载的需求，并以 SSD 支持的存储为后盾。

  特别适合需要低 I/O 延迟和稳定 I/O 吞吐量的数据库工作负载。

  Provisioned IOPS 存储最适合生产环境。

  最小存储容量为 100GB，最大为 16TB。

+ Magnetic Storage

  逐渐被淘汰

**RDS 配置:**

<img src="./img/5.png" alt="5" style="zoom:50%;" />

## AWS Aurora

完全兼容MySQL和PostgreSQL

数据库通常是计算和存储的组合，使用附加存储，尤其是大型的数据库，所以要将**计算和存储解耦**

### 优势

<img src="./img/6.png" alt="6" style="zoom:50%;" />

Aurora 的核心存储层，它是一个**分布式的、高可用的存储系统**。

+ Aurora 不是简单地存储表和行，而是**日志结构化的存储系统**，它能更高效地管理写入和恢复数据。
+ Aurora 的存储不是一个单独的磁盘，而是分布在**多个存储节点（Storage Nodes）\**上，形成\**分布式存储**，提高了吞吐量和容错能力。
+ Aurora 的存储节点采用本地 SSD，确保高性能。
+ 持续备份到亚马逊 S3
+ 存储容量分布在多个 AZ 上

### 架构

<img src="C:\Users\ForceCS\Desktop\aws-saa\database\img\7.png" alt="7" style="zoom:60%;" />

### 类型

+ Provisioned(预配置的)
+ Serverless

### 全球数据库集群

由一个主数据库集群组成，这个集群位于一个特定的region,其他的只读集群组成，主数据库集群到读集群是异步复制的（专门构建的低延迟和高吞吐量）