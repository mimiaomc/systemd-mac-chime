# systemd-mac-chime
Plays the classic Mac Chime boot sound on linux starting up and resume.

# 简体中文
一个可以让你电脑像 Mac 一样发出启动声音的服务

## 使用方法

文件说明

- ```mac-chime.service``` 为启动时发声服务
- ```mac-chime-resume.service``` 为唤醒时发声服务
- ```mac_chime.wav``` 为 Mac 唤醒声音（来自[维基百科](https://en.wikipedia.org/wiki/File:MacStartupChime.ogg)，转换成了 wav 文件）

请按照自身需求（例如想让电脑启动时或者唤醒时发声）选择文件

请把 ```service```文件放进：
```/etc/systemd/user/```

然后把 ```wav``` 文件放进：
```/usr/local/share/sounds/custom/```

示例命令：
```
sudo cp mac-chime.service /etc/systemd/user/mac-chime.service
```
（和/或 ```sudo cp mac-chime-resume.service /etc/systemd/user/mac-chime-resume.service```）

用来添加服务

---

然后执行：

```
sudo systemctl --global enable mac-chime-resume.service
```
（和/或 ```sudo systemctl --global enable mac-chime.service```）

---

然后执行：

```
systemctl --user daemon-reload
```

这样重启电脑就可以听见声音了

---

至于为什么是 ```--user```……如果你认为你的 ```PipeWire``` 在 ```root``` 下就启动了的话……可以不用 ```--user```（
