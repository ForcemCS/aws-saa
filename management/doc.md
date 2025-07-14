### CloudFormation

基础设施即代码工具

<img src="./img/1.png" alt="1" style="zoom:50%;" />

### CDK

它是另一个基础设置即代码工具

<img src="./img/2.png" alt="2" style="zoom:50%;" />

#### Features

- Declarative Approach
- Component Reusability
- AWS Construct Library
- Automated Synthesis
- Environment Agnosticism

<img src="./img/3.png" alt="3" style="zoom:50%;" />

### CloudWatch

<img src="./img/4.png" alt="4" style="zoom:50%;" />

#### CloudWatch Components

<img src="./img/5.png" alt="5" style="zoom:50%;" />

例如 EC2 autoscaling ,通过指标实现自动扩缩容

### X-Ray

可以按照分布式链路追踪理解

### Prometheus

<img src="./img/6.png" alt="6" style="zoom:50%;" />

### Trusted  Advisor

提供AWS资源使用的最佳实践的建议和指导

### Launch Wizard

+ 从AWS提供的目录中选择应用程序
+ 输入应用程序的规格

### Compute Optimizer

资源分析，给出优化建议

### AWS Organizations

多个aws账号都有自己的账单设置，你会希望整合所有的账单

为每个账号设置IAM

多个账号的资源并没有在一个池中共享

AWS Organizations可以想象为公司的总部

<img src="./img/7.png" alt="7" style="zoom:50%;" />

<img src="./img/8.png" alt="5" style="zoom:50%;" />

### Control Tower

轻松创建并部署一个新的账户

### Systemctl Manager

管理系统级服务，例如EC2

### Service Catalog

管理用户对不同service的访问权限

<img src="./img/9.png" alt="9" style="zoom:50%;" />

### License Manager

软件许可证管理服务

### Proton

标准化应用程序栈，统一多个环境的部署方式

<img src="./img/10.png" alt="10" style="zoom:50%;" />



### Resource Group

<img src="./img/11.png" alt="11" style="zoom:50%;" />

### Resource Explorer

方便管理多个regison的不同标签的资源

### Resource Access Manager（RAM）

对共享资源的管理。那么我们如何使用资源访问管理呢？ 首先，我们在其中一个账户中创建一个资源。 然后我们选择资源，并说我们想要共享它。我们选择主体，也就是我们最终想要与之共享的账户，然后在我们的共享帐户上，我们需要接受那些共享。 然后我们可以继续监控和管理那个资源共享。 所以在任何时候，我们都可以选择撤销它。

