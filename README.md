# Authing Radius

<div align=center><img width="300" src="https://files.authing.co/authing-console/authing-logo-new-20210924.svg"></div>
<br/>
<div align="center">
<div >
  <a href="https://docs.authing.cn/v2/" target="_blank"><img src="https://img.shields.io/badge/docs-passing-success"></a>
  <a href="https://forum.authing.cn/" target="_blank"><img src="https://img.shields.io/badge/chat-on%20forum-blue"></a>
  <a href="javascript:;"><img src="https://img.shields.io/badge/License-MIT-brightgreen"></a>
  <a href="javascript:;"><img src="https://img.shields.io/badge/PRs-welcome-green"></a>
</div>
<br/>

</div>

# 步骤一：[下载Authing Radius Agent](https://github.com/Authing/radius/releases/download/1.0.0/AuthingRadius.jar)

<br>

# 步骤二：安装 Authing Radius Agent

* 首先要准备一台支持 java 的服务器用来安装 Authing Radius Agent

* 确保设备安装了 java 11 或以上版本

* 将步骤一下载的安装包拷贝至设备文件系统，如：/root/radius/AuthingRadius.jar

<br>

# 步骤三：在 Authing 控制台创建 Radius 应用

<br>

# 步骤四：配置 Authing Radius Agent

cd 到目标设备上 Agent 所在目录，创建 config.json，填入以下配置信息：

```json
{
  "scheme": "https",
  "authingHost": "core.authing.cn",
  "port": 1812,
  "userPoolId": "your authing user pool id",
  "appId": "your authing radius app id",
  "sharedSecret": "copy from your authing radius app in authing console"
}
```

| 参数名                     | 类型 | 说明 | 默认值 |
| ----------------------- |:--------:| :------:| :-----: |
|  scheme     |    字符串    |  发送给 authing 的请求 sheme   |    https   |
|  authingHost     |    字符串    |  若私有化部署了 authing，需要填写私有化的域名   |    core.authing.cn   |
|  port     |    整数    |   Radius 服务端口，需要和 Radius 客户端应用程序的设置匹配   |    1812   |
|  userPoolId     |    字符串   |   authing 用户池 id  |       |
|  appId     |    字符串   |   authing radius 应用 id  |       |
|  sharedSecret     |    字符串   |   authing radius 应用的 SharedSecret  |       |

<br>

# 步骤五：启动 Authing Radius Agent

在 Authing Radius Agent 所在目录下，运行

```shell
java -jar AuthingRadius.jar 
```

<br>

# 步骤六：测试 / 验证 Radius 服务

可以用支持 Radius 的设备 / 应用程序进行测试。也可以下载我们的 [Authing Radius 测试客户端](https://github.com/Authing/radius/releases/download/1.0.0/AuthingRadiusClient.jar)

在本机，cd 到我们的测试客户端所在目录，运行：

```shell
java -jar AuthingRadiusClient.jar your_agent_ip your_secret username password
```

示例：

```shell
java -jar AuthingRadiusClient.jar 192.168.1.100 1234567890 test 123456
```

<br>

# Best Practice

1. 让 Agent 以 Daemon 进程方式运行。Linux 系统下面运行：

```shell
nohup java -jar AuthingRadius.jar > /dev/null &
```

2. Agent 日志和 Agent 在同一目录下，文件名：radius.log
