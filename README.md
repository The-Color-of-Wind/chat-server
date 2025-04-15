# 实时聊天系统—服务器（**[客户端](https://github.com/The-Color-of-Wind/ChatSystem-Client)**）
---

## 目录
1. [项目介绍](#项目介绍)
2. [项目特点](#项目特点)
3. [已实现功能](#已实现功能)
4. [Demo演示](#Demo演示)
5. [服务器框架](#服务器框架)
6. 
7. [界面概述](#界面概述)
8. [类概述](#类概述)
9. [项目构建](项目构建)
10. [更新日志](#更新日志)
11. 
   
---

## 项目介绍
基于 **Epoll + 线程池 + 主从 Reactor 模型** 的高性能通信服务器，支持 **Qt 跨平台客户端**接入，支持 **4000+ 实时通信连接**，适用于**在线聊天、消息推送**等高并发场景。

---

## 项目特点

### 高并发架构

- **主从 Reactor 模型**：主线程仅负责监听和连接分发，工作线程异步处理 I/O，有效提升并发处理能力
- **线程池 + 任务队列**：使用自研线程池，任务队列通过 CAS 实现无锁设计，减少线程间竞争，提升吞吐量
- **数据库连接池（单例 + RAII）**：单例模式创建并数据库连接池封装，配合 RAII 自动释放资源，避免连接泄漏

### 自定义协议

- **协议格式**：`[4字节长度] + JSON正文`
- **拆包粘包处理**：利用状态机实现信息的拆分，确保消息完整解析，拆分成功率 **100%**

### 异步日志系统

- 基于 **管道通信** + **日志线程** 实现异步日志写入
- 支持**多级日志等级**（INFO, ERROR, DEBUG），避免阻塞主线程 I/O

### 性能压测
- 使用 **JMeter 自定义 TCP Sampler** 进行压力测试
- 已验证可支持 **4000+ 并发连接** 实时通信，系统稳定运行

---

## 已实现功能

- ✅ 用户注册与登录
- ✅ 好友添加/删除/列表
- ✅ 实时聊天（点对点）
- ✅ 心跳检测 & 自动断线重连
- ✅ 防粘包拆包的消息协议
- ✅ 异步日志记录
- ✅ 数据库连接池支持
- 持续更新中...

---

## Demo演示
[演示视频](https://www.bilibili.com/video/BV1GrosY3E7k/?vd_source=57d3045b67b7aa01f9f207a33b419c6a)
  
---

## 项目构建
- 
- 
- 





## 框架
![17cbcaa469b8cabf301f1f46c5eec79](https://github.com/user-attachments/assets/79878936-25bb-45c1-9fb8-c0420581f572)
![67482f768071677e8eb44c841035083](https://github.com/user-attachments/assets/f8f68a2b-4542-4edd-9f86-b1178da9703d)


## 界面概述
[启动界面](ClassDescription/action.md)

[登录界面](ClassDescription/loginwidget.md)

[注册界面](ClassDescription/registerwidget.md)

[主界面](ClassDescription/mainwidget.md)

[聊天界面](ClassDescription/chatwidget.md)

[好友界面](ClassDescription/friendwidget.md)


## 类概述
[用户类](ClassDescription/user.md)

[好友类](ClassDescription/userfriend.md)

[聊天框类](ClassDescription/userchat.md)

[信息类](ClassDescription/message.md)

## 处理器内核


## 更新日志
- **version1**：

  **并发量**：2000、5000

  **请求量(登录+发信息)**：4000、10000

  **成功率**：97.2%、70.3%

  **平均响应**：

    - **登录**：3551ms、10488ms(10秒) （1w同时请求能接受，登录都需要一定时间，但成功率太差）

    - **发送信息**：341ms、1179ms
  

- **version2**：优化代码框架 + 增加消息头 + 增加防沾包机制 + 映射互斥锁

  **并发量**：2000、5000

  **请求量(登录+发信息)**：4000、10000

  **成功率**：

  **平均响应**：

    - **登录**：

    - **发送信息**：
  
- version3：


## 安装包
**暂未上线**
