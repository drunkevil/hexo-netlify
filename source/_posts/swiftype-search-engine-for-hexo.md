title: Hexo静态博客添加站内搜索--Swiftype
date: 2015-04-08 10:50:27
categories: 学习笔记
---

大多数像Hexo一样的静态博客系统，很多功能都需要借助第三方的服务才能实现，比如评论系统、分享功能和站内搜索等。这对于一些对自己的数据比较敏感的人来说很难接受。我的看法是，只要第三方应用做得好并且可靠，就会去使用。WordPress中很多做得很好的第三方插件使用者也很多。所以，对于第三方的东西，不能一棒子打死。

<!--more-->

为静态博客添加第三方应用的方式大同小异，都是将第三方提供的JS代码嵌入到网站模板的合适位置，调用其服务器端代码。

作为个人博客的基础功能之一，站内搜索必不可少，提供这一功能的第三方公司也为数不少。其中，百度站内搜索和Google CSE类似，都是依托自身强大的搜索技术提供服务；而微搜索和Swiftype则是专门做站内搜索功能的初创企业的代表，后者更是其中的佼佼者，2012年毕业于大名鼎鼎的Y Combinator，总部位于旧金山。

Google无疑是搜索领域的老大，但是Swiftype也有自己面向网站和app侧的优势，它的平台可定制性很强，Swiftype还开放了API接口，供网站深度访问其搜索功能，可以满足不同网站的个性化需求，而Google的Custome Search Engine，定制性不够强。关键的是，由于被墙的原因，Google CSE在国内也基本上很难使用。

Swiftype可以为网站及移动app提供内置搜索引掣服务。其部署十分简单，只须输入URL地址平台即可执行对用户网站的抓取，插入JS代码嵌入网站就即完成搜索引擎的创建。Swiftype还提供了分析服务，供网站检索分析用户的搜索行为和使用偏好。Swiftype还支持对搜索结果排序进行定制。

我的博客采用[Hexo](http://drunkevil.com/2015/02/05/hexo-gitcafe/)搭建，主题在[jacman](https://github.com/wuchong/jacman)的基础上修改而来。前两天放假，增加了基于Swiftype的站内搜索功能，下面是实现步骤：

----------

#### 1、
到swiftype的网站[https://swiftype.com](https://swiftype.com)注册账号，输入自己网站的URL地址，根据指引建立自己站点对应的Engine；

![](http://ww4.sinaimg.cn/mw690/aeba7ac3gw1eqx9ly7v66j20g30b7gmy.jpg)

#### 2、

切换到Install面板，根据需要配置自己站点的Engine，我的配置如下；

![](http://ww3.sinaimg.cn/mw690/aeba7ac3gw1eqx9lxo32ej20fu0rzq5z.jpg)

#### 3、

点击左侧的“SWIFTYPE INSTALL CODE”获取根据配置得到的JS代码；

![](http://ww1.sinaimg.cn/mw690/aeba7ac3gw1eqx9lx8p5zj20q70exwgy.jpg)

将其添加到jacman\layout\ _partial目录下的footer.ejs文件;

#### 4、

在jacman主题下的_config.yml文件末尾添加如下代码：



>     swift_search:
  		enable: true

#### 5、
在hexo的source目录下建立一个search文件夹，并在其中新建一个index.md文件，其内容为：



>     layout: search
	title: search
	---

#### 6、

找到jacman\layout\ _partial目录下的header.ejs文件，在其中添加如下代码：



>     <% if (theme.swift_search.enable){ %>
		<form class="search" action="<%- config.root %>search/index.html" method="get" accept-charset="utf-8">
		<input type="text" id="st-search-inpu" maxlength="20" placeholder="搜索" />
		</form>
	<% }

#### 7、

将jacman\layout\ _partial目录下的search.ejs中的内容替换为如下代码（主要用来控制结果的显示样式，可根据个人爱好修改）：



> 	<% if(theme.swift_search.enable) { %>
		<div  id="container" class="page">
  		<div id="st-results-container" style="width:70%; margin:1.5em auto">正在加载搜索结果，请稍等。</div>
  	<style>
	.st-result-text {
 		background: #fafafa;
  		display: block;
  		border-left: 0.5em solid #ccc;
  		-webkit-transition: border-left 0.45s;
  		-moz-transition: border-left 0.45s;
  		-o-transition: border-left 0.45s;
  		-ms-transition: border-left 0.45s;
  		transition: border-left 0.45s;
  		padding: 0.5em;
		}
	@media only screen and (min-width: 768px) {
  	.st-result-text {
    	padding: 1em;
  		}
	}
	.st-result-text:hover {
 	 	border-left: 0.5em solid #ea6753;
		}
	.st-result-text h3 a{
  		color: #2ca6cb;
  		line-height: 1.5;
  		font-size: 22px;
		}
	.st-snippet em {
  		font-weight: bold;
  		color: #ea6753;
		}
	</style>
	<% } %>

#### 8、

至此，配置完成，`hexo d -g`重新部署一下即可出现站内搜索功能。搜索框的样式可根据个人爱好在CSS文件中修改。

麻雀虽小，五脏俱全，博客的基础功能基本上都已实现。


----------

####参考链接：

[1]  [静态博客如何实现站内搜索](http://blog.moyizhou.cn/web/search-engine-for-static-pages/)；

[2]  文中代码主要参考的[这里](http://www.jerryfu.net/post/search-engine-for-hexo-with-swiftype.html)，向博主表示感谢。
