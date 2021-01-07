# WakeLeanEngine

由于 leancloud 的免费云引擎开启了流控，所以服务器在半小时内没有请求就会进入休眠。每当有请求时才会再次启动，如果一个用户的请求正好遇到了休眠状态，这个用户收到响应的过程长达 2~10 秒，而后来的请求将会恢复正常，直到半个小时没有请求后则进入休眠，本程序的目的就是让服务器在长时间属于苏醒状态

## 原理

利用定时函数发送 get，发送请求时也对自己发送一次请求，达到双方都唤醒的目的，但是 leancloud 的免费服务器只能运行 18 小时，所以需要部署两个服务器，互相倒班唤醒即可（真是保姆级别的服务啊）
