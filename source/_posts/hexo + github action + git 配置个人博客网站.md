
# 一、Overflow
[完整配置参考视频](https://www.bilibili.com/video/BV1dt4y1Q7UE?from=search&seid=14792497382015603750)，以及该[视频对应的笔记](https://www.bilibili.com/video/BV1dt4y1Q7UE?from=search&seid=14792497382015603750)。


# 二、Hexo 主题设置
[Hexo 全部主题](https://hexo.io/themes/)，[up 使用的 matery 主题中文文档](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)。如下图所示。

![matery 主题](https://img-blog.csdnimg.cn/20210318002055207.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ppbW9zYW5ndGlhbg==,size_16,color_FFFFFF,t_70#pic_center)

# 三、本地测试
打开 git bash 命令行界面操作，相关代码如下。
```c
   npm install hexo-cli -g
   hexo init blog
   cd blog
   npm install
   hexo server
```

# 四、远端部署
## 1. 根目录 "_config.yml" 文件配置
```c
   deploy:
	 type: git
	 repo: https://github.com/daojuhecheng/daojuhecheng.github.io
     # repo: git@github.com:daojuhecheng/daojuhecheng.github.io.git
     branch: master
```
## 2. 可能出现的 error
 1. 执行 "hexo d" 后，出现 "error deployer not found: github"。 
```c
   npm install hexo-deployer-git --save
   # 安装 hexo 对于 git 的部署工具
```
 2. Git 报错： "OpenSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443"。
```c
   git config --global --add remote.origin.proxy ""
```
 3. 继续报上一步的错，参考 [443 error](
https://segmentfault.com/a/1190000018624911?utm_source=tag-newest)，修改 "_config.yml" 中的 "repo" 行（https 改为 ssh）。

# 五、自定义模板相关
[看板设置](
https://segmentfault.com/a/1190000018624911?utm_source=tag-newest)，需要修改 "_config.yml" 文件。
```c
   npm install --save hexo-helper-live2d
   # 安装 live2d
   # 不同的看板人物需要额外的 install
```

# 六、Github Actions
Github Actions 可以实现自动化部署，即提交代码后自动发布。参考 [视频对应的笔记](https://www.bilibili.com/video/BV1dt4y1Q7UE?from=search&seid=14792497382015603750) 可以实现这一过程，即切换分支 "myblog" 后执行 "git add ."、"git commit -m 'log'" 和 "git push origin myblog" 操作。

另外，需注意 Git 的一些相关操作如 [切换分支操作](https://www.cnblogs.com/aididiao/p/11882227.html)、[撤销 "commit" 和 "add"](https://www.cnblogs.com/zph666/p/12692734.html) 以及 "git pull" 同步远程与本地（merge）等。