title: hexo更换电脑及升级3.0那些事儿
date: 2015-05-01 14:21:20
categories: 其他分类

---

之前，hexo博客程序安装在实验室的电脑上，每次更新博客都要通过这台电脑进行。

<!--more-->

很快，这台电脑将[不再属于我](http://drunkevil.com/2015/04/12/concealed-evaluation/)。不懂[Hexo服务器端布署及Dropbox同步](http://lucifr.com/2013/06/02/hexo-on-cloud-with-dropbox-and-vps/)，不会[配置Node+Git+Hexo的绿色环境](http://ibruce.info/2013/11/22/hexo-your-blog/)，不想[使用GitHub来管理博客源文件](http://wuchong.me/blog/2014/01/17/use-github-to-manage-hexo-source/)。于是考虑在家里的电脑上安装一下hexo。记录其中两三事儿。



### 1.备份

包括hexo目录下的source文件夹，_config.yml文件，以及主题文件夹。

### 2.安装hexo

所有必备的应用程序（[Node.js](https://nodejs.org/)，[Git](http://git-scm.com/)）安装完成后，即可使用npm安装Hexo-cli和Hexo。


>     $ npm install -g hexo-cli
	$ npm install hexo --save

![](http://i.imgur.com/wMRsWp1.png)

### 3.安装插件

主要有：首页文章数量，存档，分类的插件；部署器插件；rss site-map之类插件。按需安装。

 
> 
    npm install hexo-generator-index --save
    npm install hexo-generator-archive --save
    npm install hexo-generator-category --save
    npm install hexo-generator-tag --save
    npm install hexo-server --save
    npm install hexo-deployer-git --save
    npm install hexo-deployer-heroku --save
    npm install hexo-deployer-rsync --save
    npm install hexo-deployer-openshift --save
    npm install hexo-renderer-marked@0.2 --save
    npm install hexo-renderer-stylus@0.2 --save
    npm install hexo-generator-feed@1 --save
    npm install hexo-generator-sitemap@1 --save
  

### 4.修改全局配置文件

之前的分页设置为：



>  
    # Archives
    ## 2: Enable pagination
    ## 1: Disable pagination
    ## 0: Fully Disable
    archive: 1
    category: 1
    tag: 0
   

修改为：

>  
    index_generator:
      per_page: 10 ##首页默认10篇文章标题 如果值为0不分页
    archive_generator:
        per_page: 10 ##归档页面默认10篇文章标题
        yearly: true  ##生成年视图
        monthly: true ##生成月视图
    tag_generator:
        per_page: 10 ##标签分类页面默认10篇文章
    category_generator: 
        per_page: 10 ###分类页面默认10篇文章
  
    
        
RSS配置为：


>  
    feed:
        type: atom ##feed类型 atom或者rss2
        path: atom.xml ##feed路径
        limit: 20  ##feed文章最小数量
      

### 5.部署类型

hexo3.0一共提供了5种部署类型，对于部署到Github或者Gitcafe上面来说，选择的部署类型为Git，首先安装插件：

 

>    $ npm install hexo-deployer-git --save

![](http://i.imgur.com/tDyrRQB.png)
    
修改配置：



>     deploy:
        type: git
        repo: <repository url>##库（Repository）地址
        branch: [branch]##分支名称
        message: [message]##自定提交信息 
      
可同时使用多个 deployer，Hexo 会依照顺序执行每个 deployer。



>     deploy:
    - type: git
      repo: 
    - type: heroku
      repo:
      
比如同时部署到Github和Gitcafe：

 

>     deploy:
 	    type: git
 	    message: update  ##git 
 	    repo: 
  		    github: <repository url>,[branch] ##github 仓库地址和分支
  		    gitcafe: <repository url>,[branch] ##gitcafe 仓库地址和分支
  

### 6.查看版本

纯属多余，大可不必。



>     $ hexo v
    
![](http://i.imgur.com/sQoMLdi.png)

