## SSH多路复用

SSH多路复用是一种通过复用已经存在的SSH连接来减少建立新连接所需的时间和资源的方法。例如CERN的LXPLUS服务，复旦Hirg组的服务器管理员均未开启密钥链接，通过配置SSH多路复用可以避免每次开启会话时输入密码。以下是配置SSH多路复用的详细步骤：

### 编辑SSH配置文件
```bash
vi ~/.ssh/config
```
### 添加多路复用配置
在配置文件中，为希望使用多路复用的主机（或所有主机）添加如下配置：
    
```
  Host *
    ControlMaster auto
    ControlPath ~/.ssh/sockets/%r@%h:%p
    ControlPersist 10m
```
解释：
`Host *`：表示对所有主机生效。可以替换成特定的主机名或模式。
`ControlMaster auto`：自动启用控制主连接。
`ControlPath ~/.ssh/sockets/%r@%h:%p`：设置控制套接字的路径。这里使用了`~/.ssh/sockets/` 目录，可以根据需要修改路径。
`ControlPersist 10m`：保持主连接打开10分钟，即使没有活动的会话。可以根据需要调整时间设置。

### 创建套接字目录
如果你在配置中指定了一个目录来存放控制套接字（如上面的 ~/.ssh/sockets/），那么需要确保这个目录存在：
```bash
mkdir -p ~/.ssh/sockets
```
### 测试配置
配置完成后，可以通过连接SSH来测试是否配置成功：

```bash
ssh your_username@your_host
```
然后在**新的终端窗口**中，再次连接同一台主机：

```bash
ssh your_username@your_host
```
如果配置成功，第二次连接应该会非常快，因为它复用了第一个连接。

### 验证多路复用是否生效
可以通过检查活动的SSH连接来验证多路复用是否生效：

```bash
ps aux | grep ssh
```
应该会看到与 ControlPath 配置匹配的连接信息。

### 结束复用
```bash
ssh -O exit user@host
```




