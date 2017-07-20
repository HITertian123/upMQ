upMQ —— 轻量级消息系统设计
###### 版本说明：
| 版本号|更新说明|修订人|更新时间|
|----------|------------|---------|------------|
|  1.0   | 初步设计| 项目组| 2017.06|
#### 前言：
>     消息中间件的好处是不言而喻的，服务之间的解耦，异步处理，大流量下的削锋等，银联的CUPS系统及京东淘宝等电商平台的架构中，随处可见消息中间件的应用，也让我们认识到似乎很有必要研究一下其使用和内部原理。问题也来了，成熟可靠的开源消息中间件如Kafka,RabitMQ相继推出，我们是否有重复造轮子的需要？更何况这种庞大的系统，我们的轮子能否满足需求，能否可靠稳定？笔者的答案是造轮子是有必要的，第一点是公司技术储备的需要，业务需求的增加，更多的地方，更复杂的场景可能会使用到消息中间件，为变化做储备。 第二点是成熟的消息中间件太重，功能繁复，维护的成本颇高，且可能功能难以定制。笔者意图打造一个容易部署，当前流量下可靠，自主推送的消息平台，满足当前公司其它业务的需要。
## 1. 术语和定义
### 1.1 消息
    表示委托给upMQ系统，要推送到其它平台的信息，至少含有消息标识，内容，签名及时间等要素。
### 1.2 生产源
     表示消息的来源。
### 1.3 目的地/目的地平台
    表示消息将要推送到的其它平台。
### 1.4 生产者/生产队列
    表示容纳消息的队列，每个进入平台的消息，按分配算法分配给某个队列。
### 1.5 消费者/消费者线程
    每个生产队列对应若干个消费者线程，消费者线程异步取出队列中的信息推送到目的地。每条消息有推送，重发及更新状态等操作，多个消费者是为了提高处理效率。
## 2. 数据设计
只有用于记录的中间表及API权限控制表，不涉及对消息的逻辑处理。其表结构如下：

## 3.平台SDK
    略
## 4.生产者SDK
   略
## 5.消费者SDK
   略
&ensp;&ensp;&ensp;&ensp;该平台设计目标是轻量，可靠。单机的内存，CPU有限，笔者认为该平台应该首先考虑得是稳定性。
