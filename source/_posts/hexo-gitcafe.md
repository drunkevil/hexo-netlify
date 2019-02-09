title: 博客从Wordpress迁移回Hexo并托管到Gitcafe
date: 2015-02-05 11:49:49
categories: 其他分类

---

Wordpress应该是目前使用人数最多的个人博客平台，由于其丰富的主题和插件资源深受广大个人博客爱好者喜欢，我经常阅读的一些个人博客很多都是使用Wordpress搭建的。其著名的五分钟安装教程大大降低了技术门槛，但采用Wordpress搭建个人博客最关键的一步就是租用靠谱的主机，面对五花八门的主机商，选择起来十分困难。对于大部分刚入门的博主来说，免费的主机也许是首选，但天下没有免费的午餐，在体验了一段时间免费的主机之后，毅然决然的选择将博客迁移回Hexo。


<!--more-->



最初，我的博客就是采用Hexo搭建，并托管在Github上面，但国内网络访问速度不佳，这次迁移回来，首要考虑的便是Gitcafe，毕竟服务器在国内，访问速度肯定要明显优于Github。有了最初采用Hexo + Github Pages搭建的经历，这次迁移回来基本比较顺利，下面对整个过程以及其中遇到的问题做一个简单的记录，以供查阅。

关于如何使用Hexo + Github Pages搭建博客，请参考[这里](http://www.jianshu.com/p/05289a4bc8b2)，这是一篇很详尽的独立博客搭建教程，里面介绍了域名注册、DNS设置、github和Hexo设置等过程，我最初就是参考的这篇教程搭建的博客。

根据上面的教程，如何将博客托管到Gitcafe上面大同小异。



## 1、注册Gitcafe账户，并创建一个与用户名相同名称的项目；

![](http://blog.gitcafe.com/wp-content/uploads/2012/10/create.png)

## 2、将本机的SSH添加到GitCafe，可参考[这里](https://gitcafe.com/GitCafe/Help/wiki/%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%E5%92%8C%E8%AE%BE%E7%BD%AE%20Git)；

![](https://gitcafe.com/GitCafe/Help/raw/master/assets/images/add_ssh_key.png)

## 3、创建Gitcafe-Pages分支，并切换到该分支 

> 
>     git checkout -b gitcafe-pages
> 





## 4、提交你的代码到新分支Gitcafe-Pages目录中

>     git add .
>     git commit -a -m 'drunkevil.com'

>     git push origin gitcafe-pages


至此，你可以访问 yourname.gitcafe.io 这样的二级域名了。

## 5、域名绑定：

进入你的Page Repo的项目管理界面，自定义域名设置，点击进入，输入你想要设置的域名


<img src="http://blog.gitcafe.com/wp-content/uploads/2013/04/Screen-Shot-2013-04-26-at-2.27.11-PM.png" width=100% >

在你的域名管理界面添加一个CNAME记录，将它指向GitCafe Pages服务器的domain：gitcafe.io。如果你的 DNS 管理商不提供 CNAME 记录，请添加 A 记录到 207.226.141.135。见下图第一条和最后一条。

![](http://i.imgur.com/jqHxuJS.png)

至此，你可以通过自己的域名访问自己的Gitcafe-Pages。

## 6、修改Hexo配置文件_config.yml

（假定已经安装好Hexo，没有请移步[这里](http://www.jianshu.com/p/05289a4bc8b2)），修改内容如下：


> deploy:
> 
>   type: github
> 
>   repository: git@gitcafe.com:yourname/yourname.git
> 
>   branch: gitcafe-pages


至此，你可以通过hexo d 来部署自己的博客了。这里我在deploy的时候遇到的问题是：

> error: src refspec gitcafe-pages does not match any.
> 
> error:failed to push some refs to 'git@gitcafe.com:drunkevil/drunkevil'


解决的办法是：删了 .deploy文件重试，参考的是[这里](https://coderq.com/t/tuo-guan-hexodao-gitcafezhong-hexo-dyu-dao-wen-ti/735)，由博主[陈林泳](http://leodots.com/)给出建议，感谢。

剩下的步骤就是折腾自己喜欢的主题了，这里不再多说。

一切完成之后，ping一下自己的域名，时间大约在40ms左右，已经是非常好的访问体验了，大概与购买昂贵主机的知名博客的访问速度差不了太多了。

### 参考链接：

[1][如何搭建一个独立博客——简明Github Pages与Hexo教程](http://www.jianshu.com/p/05289a4bc8b2)

[2][让GitCafe项目托管变成外链空间](http://u-lis.com/archives/2417)

[3][如何将托管在github上的hexo博客转到gitcafe](http://blog.maxwi.com/2014/03/19/hexo-github-to-gitcafe/)

[4][如何安装和设置Git](https://gitcafe.com/GitCafe/Help/wiki/%E5%A6%82%E4%BD%95%E5%AE%89%E8%A3%85%E5%92%8C%E8%AE%BE%E7%BD%AE%20Git)

[5][如何创建Gitcafe-Pages](https://gitcafe.com/GitCafe/Help/wiki/Pages-%E7%9B%B8%E5%85%B3%E5%B8%AE%E5%8A%A9)

[6][托管hexo到gitcafe中hexo d遇到问题](https://coderq.com/t/tuo-guan-hexodao-gitcafezhong-hexo-dyu-dao-wen-ti/735)

[7][hexo你的博客](http://ibruce.info/2013/11/22/hexo-your-blog/)