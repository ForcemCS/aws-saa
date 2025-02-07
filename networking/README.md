### Subnets

<img src="./img/1.png" alt="1" style="zoom:50%;" />

VPC 中的子网必须在 CIDR 范围内。

子网块大小必须在 /16 和 /28 之间。

The first 4 IP addresses of a subnet are reserved and cannot be used:

- 192.168.10.0 (Network address)
- 192.168.10.1 – 192.168.10.3 (for AWS)
  - 192.168.10.1 (VPC Router)
  - 192.168.10.2 (DNS)
  - 192.168.10.3 (For Future Use)

The last IP address of a subnet (192.168.10.255) is reserved as the broadcast address.

### Routing

目的是在子网之间路由流量

每个subnet都与一个route table相关联。创建一个新的vpc的时候，会生成一个默认的路由表

多个子网可以与一个路由表相关联

### Internet Gateway

要把子网变成public的第一件事就是要创建一个 Internet Gateway。将其附加到我们的 VPC 上。一旦它附加到 VPC 上，就需要创建一个自定义路由表。在这个路由表中，我们需要配置一个指向 Internet Gateway 的默认路由。这默认路由基本上是说，如果一个数据包进来并且没有匹配任何其他路由，它会自动匹配默认路由，把它发送到 Internet Gateway。因为如果它不匹配任何更具体的路由，这意味着它可能是要去互联网。

### Nat Gateway

![1738918336255](./img/1738918336255.png)

假设我们在一个私有网络中有一台服务器。我们需要为这个服务器提供互联网访问权限，这样它才能连接互联网并安全补丁。
现在我们可以做的是，我们可以将一个互联网网关附加到 VPC。然后，创建一条路由，让这条线路指向互联网网关，然后将这个网络变成公共网络，这样它就可以访问互联网，以下载任何需要的更新和安全补丁。

现在的问题是，服务器是一个内部服务器，只允许内部团队访问，我们该怎么办？我们不希望它对互联网开放。因此我们希望服务器能够自动发起与互联网的连接。
但是互联网网关永远不应该连接到我们的服务器。我们应该如何解决这个问题?要实际使用 NAT Gateway，你仍然需要一个 Internet Gateway。
所以要让 NAT Gateway 正常运行，您首先需要配置一个 Internet Gateway 并将其附加到您的 VPC，然后后续需要创建一个公共子网，并设置必要的路由指向互联网网关。

<img src="./img/1738918613159.png" alt="1738918613159" style="zoom:50%;" />

NAT Gateway是不具备弹性的，我们是将他部署在一个公有子网中，所以它特定于一个可用区，可以通过多可用区部署，实现冗余

#### demo

1. 创建vpc

2. 创建私有子网

3. 创建ec2实例（属于上边的私有子网，并且不分配公网IP）

4. 创建igw, Attach to vpc

5. 创建公共子网

6. 创建两个路由表（私有，公有）

   + 在公有路由表中定义一条路由

     <img src="./img/1738920561381.png" alt="1738920561381" style="zoom:50%;" />

   + 将公有子网与这个路由表相关联

     <img src="./img/1738920741283.png" alt="1738920741283" style="zoom:50%;" />

   + 对私有路由表做同样的关联（关联到私有子网）

7. 在公共子网上部署Nat  Gateway

   <img src="./img/1738921174831.png" alt="1738921127301" style="zoom:50%;" />

8. 然后我们去私有路由表，增加一条路由信息

   <img src="./img/1738921327608.png" alt="1738921327608" style="zoom:50%;" />