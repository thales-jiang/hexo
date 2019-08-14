---
title: 脚手架
date: 2019-08-05 11:21:23
tags:
---

脚手架开发
# 准备
先找个目录初始化一下npm
```bash
mkdir cli
cd cli
npm init
```
# program
使用program组件可以实现命令行的操作 
## 安装
首先我们安装commander
```bash
npm i -S commander
```
## 版本
最简单的program显示版本
> 我们创建一个index.js文件，写入下面的代码
```js
const program = require('commander'); // 为什么命名叫program而不是commander，因为commander是保留字段
program.version("0.0.1"); // 设置版本号
program.parse(process.argv); // 解析进程
```
> 如果不知道process关键字，可以去看 http://nodejs.cn/api/process.html  
我们用node执行一下
```bash
node index.js --version
```
会得到我们设置的版本号
```bash
0.0.1
```
我们一般用package作为版本号
```js
const VER = require('../package.json').version
```
**最终代码**
```js
const program = require('commander');
program.version(require('../package.json').version); // 直接获取当前的package的version作为版本号
program.parse(process.argv);
```
## 帮助
上世纪电脑都靠命令行执行时候，就会有“-h”和“--help”作为帮助，显示命令如何用
```js
const program = require('commander');
program.version(require('../package.json').version);
program.parse(process.argv);
program.help(); // 写上这么一行，自动的就会有所有设置的参数提示
```
## 命令
比如我们用的vue create
```js
program
  .command('create')  // 命令
  .action(cmd => console.log(cmd)); // 命令动作
```
我们执行一下
```bash
node index.js create
```
会执行action里面的function，输出cmd  
**还可以加一些参数，我们看下完整代码**
```js
const program = require('commander');
program.version(require('../package.json').version);
program
  .command('create') // 创建项目
  .alias('c') // 别名，用来简写
  .description('create project(构造项目)') // 描述
  .option('-d, --default', 'skip prompt and use default preset.') // 选项
  .action(cmd => console.log(cmd));
program.parse(process.argv); // 解析进程
program.help();
```
并且你加了command之后，help会自动增加
```bash
node index.js --help
```
你可以看到比之前多了一个commads提示命令名，并且按照description给了提示
```
Usage: www [options] [command]

Options:
  -V, --version       output the version number
  -h, --help          output usage information

Commands:
  create|c [options]  create project(构造项目)
```
其他详细内容可以看官网 https://github.com/tj/commander.js
# inquirer
问询组件  
## 安装
```bash
npm i -S inquirer
```
## 问询
我们创建一个create.js文件
```js
const inquirer = require('inquirer');
module.exports = cmd => {
  inquirer
    .prompt([
      {
        // 项目名称
        name: 'name',
        type: 'input',
        default: 'my-project',
        message: '请输入项目名称'
      }
    ])
    .then(p => console.log(p))
    .catch(e => console.log('项目创建错误'));
};
```
然后把之前command的action增加
```js
const create = require('create'); // 加载create
program
  .command('create')
  .action(create); // action的function设置为create函数
```
这时候会运行会出现一个bug
```bash
node index.js create
```
问询出现之后，就直接显示了帮助
```bash
? 请输入项目名称 (my-project) Usage: www [options] [command]

Options:
  -V, --version       output the version number
  -h, --help          output usage information

Commands:
  create|c [options]  create project(构造项目)
```
所以我们一般吧帮助做一个处理，因为命令很多时候是也要加内容，所以默认认为了命令不全，我们加一个入参为空才出帮助就可以了
```js
if (!program.args.length) { // 参数为空时候显示帮助
  program.help();
}
```
现在你可以看见了想要的问询
```bash
bash> dayu create
? 请输入项目名称 (my-project)
```
输入之后，也能在inquirer的then中以object的方式返回
```
? 请输入项目名称 my-project
{ name: 'my-project' }
```
问询的种类很多，除了输入，是不是那种可以选择的会更好呢
```js
.prompt([
  {
    // 项目模板
    name: 'template',
    type: 'list',
    choices: ['A', 'B', 'C'],// 供选择的内容
    message: '请选择模板'
  }
])
.then(p => console.log(p))
.catch(e => console.log('项目创建错误'));
```
这时候可以用上下选择你想要的
```
? 请选择模板
  A
> B
  C
```
其他详细内容可以看官网 https://github.com/SBoudrias/Inquirer.js
# download-git-repo
下载git源
## 安装
```bash
npm i -S download-git-repo
```
下载git源
## 下载
我们创建一个project-build的文件
```js
import download from 'download-git-repo';
module.exports = (url, name) => {// url为git地址，name为本地创建的项目名也就是目录名称
  download(url, name, {}, err => { // 下载模板
    if (err) {
      //失败
    } else {
      //成功
  });
};
```
其他详细内容可以看官网 https://github.com/flipxfx/download-git-repo
# handlebars
替换模板参数
## 安装
```bash
npm i -S handlebars
```
## 修改package
创建的项目需要替换package.json
```json
{
  "name": "{{name}}",
  "version": "{{version}}",
  "description": "{{description}}",
  "author": "{{author}}",
}
```
替换我们就用这个方式
```js
const meta = { // 设置模板参数
  name: '项目名称',
  version: '版本号',
  description: '项目描述',
  author: '作者'
};
const fileName = `${meta.name}/package.json`;
const content = fs.readFileSync(fileName).toString(); //读取package文件内容
const result = handlebars.compile(content)(meta); // 解析内容，并且用meta替换模板的变量
fs.writeFileSync(fileName, result); // 覆盖源文件
```
# babel
## 安装
```bash
npm i -D babel-cli
```
## 配置加载环境
node是不能使用import的，但是我们经常看到babelrc
```json
{
  "presets": [
    [
      "env",
      {
        "target":{
          "node":"current"
        }
      }
    ]
  ]
}
```
我们一般是吧src的源文件输出到dist里
```bash
babel src -d dist
```
最终应用的都是dist内的文件
