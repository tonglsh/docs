# deepin安装后优化

输入法：百度输入法

桌面窗口抖动，魔灯等效果 :

```
sudo apt-get install systemsettings
```

jetbrain工具包：jetbrain Toolbox

jdk可在IDEA里下载。

maven官方下，配置文件替换成backup的

其他必备软件：微信，qq，wps，typora等可直接在应用商店下载

在官网下的谷歌浏览器可能会有其他依赖需要手动安装下。



## npm run serve 时打印错误

```
Error from chokidar (/home/tonglsh/WebstormProjects/cloud-web/src/pages/system/views): Error: ENOSPC: System limit for number of file watchers reached, watch '/home/tonglsh/WebstormProjects/cloud-web/src/pages/system/views/index.vue'
```

解决方案:

```
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p
```

