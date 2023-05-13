# Emby服管理bot by小草 (修改版)

<p>1.新增重置密码命令</p>
<p>2.新增邀请码管理</p>
<p>3.新增管理员添加，删除，列表</p>
<p>4.修改ban_emby为/b_emby,/unban_emby为/unb_emby</p>
<p>5.修改/info为/kankan，防止与其他群管机器人命令重复</p>
<p>6.添加邀请码使用通知管理员</p>
<p>7.修改群内发生成邀请码机器人直接发群里</p>
<p>8.如需要邀请码前缀可修改embybot.py第77行yqm为你的前缀</p>
<p>9.求片功能用户请求后发送到群里。可修改embybot.py第807行chat_id=groupid,groupid修改为你的tgid</p>

## 食用教程
### 将项目克隆到本地
```bash
git clone https://github.com/zorerr/EmbyBot.git && cd EmbyBot && pip3 install -r requirements.txt
```




### 修改配置文件 config.py

```
bot_token = "xxx"            您的机器人令牌。从@BotFather获取
db_host = 'localhost'        mysql数据库地址
db_port = 3306               数据库端口
db_user = 'root'              数据库用户
db_password = '55566677852'          数据库密码
db_name = 'xxx'              数据库名称名随便写，在下面操作会添加
bot_name = '@xxx'            bot username
api_id = 99999999            您的电报 API ID       https://core.telegram.org/api/obtaining_api_id
api_hash = "xxx"             你的 Telegram HASH    https://core.telegram.org/api/obtaining_api_id
embyurl = 'xxx'              emby访问链接          例 https://xxxx.com:8920
embyapi = 'xxx'              进入Emby后台，找到高级-API密钥，生成一个API
groupid = -100               1：转到（https://web.telegram.org）
                             2：转到您的 Gorup 并找到您的 Gorup 链接（https://web.telegram.org/#/im?p=g154513121）
                             3：复制该号码在 g 之后并在此之前放置 (-) -154513121
channelid = -100             只需将消息从您的频道转发到此机器人：( https://telegram.me/getidsbot )
admin_list = [111]           管理员id列表,转数据库了，这里已无效
ban_channel_id = -100 建议和channelid保持一致
line = 'xxx'                 线路\n换行
```



### 安装docker
```bash
curl -fsSL get.docker.com -o get-docker.sh && sh get-docker.sh && systemctl enable docker && systemctl start docker
```



### 创建一个用户名为root，密码为55566677852的docker数据库，记得放行端口3306
```bash
mkdir /root/EmbyBot/mysql

docker run --name tg-mysql -e MYSQL_ROOT_PASSWORD=55566677852 -e MYSQL_ROOT_HOST=% -v /root/EmbyBot/mysql:/var/lib/mysql -p 3306:3306 -d mysql:8 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```
创建一个用户名为root，密码为55566677852的docker数据库，记得放行端口3306



### 创建数据库

#### 使用navicat连接数据库

连接mysql

![](https://dd-static.jd.com/ddimg/jfs/t1/179135/39/28801/28871/63288ddbE7a880590/743d5b36578253f9.png)

#### 创建数据库

![](https://dd-static.jd.com/ddimg/jfs/t1/53432/1/21971/13792/63288e26E89be5b9b/1b9d009a1e05933c.png)
数据库名随便写，需要和配置文件一样

#### 导入数据库文件（下载文件，解压，右键数据库，运行sql）
https://raw.githubusercontent.com/zorerr/EmbyBot/main/EmbyBot.sql.zip

#### 写入机器人管理员
管理员列表写进数据库了，需在admin表将你的tgid写上，修改embybot.py第849行123456修改为你的tgid，否则管理员功能不可用

## 启动机器人
前台启动机器人        python3 embybot.py
后台启动机器人        nohup python3 embybot.py > botlog.log 2>&1 &
## 添加进程守护（可选，但强烈建议）
在 /usr/lib/systemd/system 下创建如下文件  
https://github.com/zorerr/EmbyBot/blob/main/embybot.service
/root/EmbyBot 改为文件路径，如文件在此文件夹放着不用改  
执行命令  
`systemctl daemon-reload`  
启动bot  
`systemctl start embybot`  
重启bot  
`systemctl restart embybot`  
开机自启  
`systemctl enable embybot`  
停止bot  
`systemctl stop embybot`  
出问题查看报错  
`systemctl status embybot`  
## 使用
发送/start 获取帮助

## 参考
[https://github.com/MisakaF0406/MisakaF_Emby
](https://github.com/MisakaFxxk/MisakaF_Emby)  
## 鸣谢
东东，Misakaf等Emby大佬提供技术支持
Foxcoo 帮我撰写了部分的README


