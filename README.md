# >**目前在CodeSandBox平台已经有更成熟的部署方案，此仓库已经弃用。**

>好用的话，可以给我点一下star吗，谢谢！

# 使用方法（Railway）
## 第一步：Fork本仓库

点击右上角的Fork按钮，将本仓库Fork到你自己的Github账户中。

## 第二步：新建railway项目

在[Railway](https://railway.app/dashboard)用相同的Github账号登录，点击New Project，新建一个项目。选择“Deploy from GitHub repo”，选择你Fork的这个仓库。

## 第三步：添加环境变量

**不要**选择“Deploy Now”，选择“Add variables”。

![添加环境变量](/pic/variables.png)

如图添加环境变量`PORT=5700`

![添加如图所示的环境变量](/pic/variables2.png)

## 第四步：获取访问域名

在Settings中找到Generate Domain按钮，点一下，获取访问域名。当然你也可以绑定你自己的域名。

![获取域名](/pic/Domain.png)

## 注意
>Railway平台的免费额度标准一直在变动，目前，Railway不用信用卡认证的免费额度是2刀+200小时/月，挂青龙面板并不现实。信用卡验证之后的免费额度为5刀+不限时/月，具体够不够挂青龙我也没有计算，这里仅仅是对在Railway上部署青龙面板的一个尝试。请自行辨别。
>
>2023年5月11日补充：经测试，拉了几个库一起跑，443个任务，一个号，预计月扣费4.61刀，刚好在5刀以内。
>
>![estimated](/pic/railway_estimated.png)

# 使用方法（Render）

类似的，你还可以在[Render](https://dashboard.render.com/)上使用本repository。

不同的地方仅仅在于，Render中新建的是Web Service。

![Web Service](/pic/webservice.png)

环境变量添加的地方变成了Environment选项卡。

![环境变量](/pic/environment1.png)

如下图所示添加环境变量即可。

![环境变量](/pic/environment2.png)

而且Render不需要你主动generate域名，他会自动生成域名，当然你也可以绑定自己的域名。

## 注意
>Render的每月免费额度高达750小时，足够覆盖单个项目的整月使用。但是由于Render的特性，容器每隔一段时间会强制重启，且删除所有数据，如果需要使用Render部署青龙，需要在Dockerfile中使用`ADD`命令将数据在构筑时添加进去，类似于[xiaoya_alist_docker_on_render](https://github.com/k0baya/xiaoya_alist_docker_on_render/blob/main/Dockerfile)的方法，在仓库中新建一个data文件夹并把数据都存入，在Render构筑时又能将数据复制进去。如果这么使用，请不要直接Fork，务必自建私密仓库后Import本仓库再上传data以保证数据安全。

# 容器保活

这些平台上托管的项目并不一定会一直保持活跃，有些在一段时间无人访问之后就会休眠，所以可以使用一些外部监控手段保活。

我已知的网站监控：
>1 [cron-job.org](https://console.cron-job.org)
>
>2 [UptimeRobot](https://uptimerobot.com/)

可供自行搭建的网站监控：
>[Uptime-Kuma](https://github.com/louislam/uptime-kuma)
