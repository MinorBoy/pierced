### pierced
钉钉内网穿透

#### TCP 穿透需要在数据库里面执行：
```
GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY '123456';
FLUSH PRIVILEGES;
```

#### 数据库连接命令：
```
mysql -h vaiwan.com -u root -p -P 1234 //端口号地址
```


---

# 一 启动内网穿透

1.下载工具
git clone https://github.com/open-dingtalk/pierced.git

![image](https://cdn-pub.yuque.com/lark/2018/png/bd935f2f-c3f8-44de-a658-a104bfdafc24.png)


启动工具，执行命令“./ding -config=./ding.cfg -subdomain=域名前缀 端口”，以`mac`为例：

```
cd mac_64
chmod 777 ./ding
./ding -config=./ding.cfg -subdomain=abcde 8080
```

启动后界面如下图所示：

![界面](https://cdn-pub.yuque.com/lark/2018/png/ddfd9389-58b6-43b4-adf9-f8db52f25bba.png)

命令参数说明：

参数|说明
--|--|
config|内网穿透的配置文件，按命令照示例固定为钉钉提供的./ding.cfg，无需修改
subdomain|您需要使用的域名前缀，该前缀将会匹配到“vaiwan.com”前面，例如你的subdomain是abcde，启动工具后会将abcde.vaiwan.com映射到本地。
端口|您需要代理的本地服务http-server端口，例如你本地端口为8080等

2.启动完客户端后，你访问http://abcde.vaiwan.com/xxxxx都会映射到 http://127.0.0.1:8080/xxxxx
注意：

 >1. 你需要访问的域名是http://abcde.vaiwan.com/xxxxx 而不是http://abcde.vaiwan.com:8082/xxxxx
 >2. 你启动命令的`subdomain`参数有可能被别人占用，尽量不要用常用字符，可以用自己公司名的拼音，例如：alibaba、dingding等。
 >3. 可以在本地起个`http-server`服务，放置一个`index.html`文件，然后访问http://abcde.vaiwan.com/index.html测试一下。


---

# 二 window下，nodejs 安装 http-server，开启命令行HTTP服务器

第一步：http://nodejs.cn/  官网下载安装文件，安装 `nodejs`；

第二步：运行中输入`cmd`进入命令行模式，输入  `node -v` ，显示版本号，代表安装成功；

第三步：在`node`命令行下，输入
```
npm install http-server -g
```

安装成功提示如下：

![截图](https://images2017.cnblogs.com/blog/350759/201709/350759-20170905114338538-844374718.png)

把上面选中那行加入环境变量PATH中。

第四步：进入你的文件目录，输入
```
http-server
```



显示上图，在浏览器输入 http://127.0.0.1:8088 ，即可以显示你的文件目录里的`index.html`的网页文件。

成功!
