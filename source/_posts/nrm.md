---
title: nrm的使用
date: 2019-03-10 12:57:10
tags: nrm
---
nrm是专门用来管理和快速切换私人配置的registry
# 全局安装nrm
``` bash
npm i nrm -g
```
如果是unix系统，比如mac或者其他linux，需要添加sudo，然后还要输入密码
``` bash
sudo npm i nrm -g
```
## nrm有一些默认配置，用nrm ls命令查看默认配置
``` bash
nrm ls
```
带*号即为当前使用的配置
```
  npm ---- https://registry.npmjs.org/
* cnpm --- http://r.cnpmjs.org/
  taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
  rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
```
## 也可以直接用current命令查看当前使用的是哪个源
``` bash
nrm current
```
## 使用nrm切换源
切到源http://registry.mirror.cqupt.edu.cn 命令：nrm use 源的别名，即
``` bash
nrm use rednpm
```
查看*变化了位置
```
  npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
  taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
* rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
```
## 用nrm add 命令添加公司私有npm源
如http://test.jd.com (肯定不能暴露公司的私有源，这里代替的)，起个别名叫jd
``` bash
nrm add jd http://test.jd.com
```
执行成功提示
```
add registry jd success
```
接着查看nrm配置，发现最底部jd添加成功
```
  npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
  taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
* rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
  jd ----- https://test.jd.com/
```
需要用use去指向
``` bash
nrm use jd
```
看看ls
```
  npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
  taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
  rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
* jd - http://registry.m.jd.com/
```
## 可以用test测试速度，我们来测试cnpm的速度
``` bash
nrm test cnpm
nrm test npm
```
输出：
```
cnpm --- 1095ms
npm ---- 1241ms
```
做做对比，npm还是慢

## 删除源用del
``` bash
nrm del jd
```
由于你选中的是这个源，删除之后会自动替换
```
⸨░░░░░░░░░░░░░░░░░░⸩ ⠙ :
    delete registry jd success

                        

   Registry has been set to: https://registry.npmjs.org/
```
再看看ls
```
* npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
  taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
  rednpm - http://registry.mirror.cqupt.edu.cn/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
```
已经到最上面的源取了