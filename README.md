# pierced
钉钉内网穿透

### TCP 穿透需要在数据库里面执行：
```
GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY '123456';
FLUSH PRIVILEGES;
```

### 数据库连接命令：
```
mysql -h vaiwan.com -u root -p -P 1234 //端口号地址
```




## window下，nodejs 安装 http-server，开启命令行HTTP服务器

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
