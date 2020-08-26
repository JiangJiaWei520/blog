# 我的博客

我的个人博客：<https://blog.jiang7zzz.xyz>。

## 概览

<!-- vim-markdown-toc GFM -->

* [效果预览](#效果预览)
* [Fork 指南](#fork-指南)
* [经验与思考](#经验与思考)
* [致谢](#致谢)

<!-- vim-markdown-toc -->

## 效果预览

**[在线预览 &rarr;](https://blog.jiang7zzz.xyz)**

## Fork 指南

Fork 本项目之后，还需要做一些事情才能让你的页面「正确」跑起来。

1. 正确设置项目名称与分支。

   按照 GitHub Pages 的规定，名称为 `username.github.io` 的项目的 master 分支，或者其它名称的项目的 gh-pages 分支可以自动生成 GitHub Pages 页面。

2. 修改域名。

   如果你需要绑定自己的域名，那么修改 CNAME 文件的内容；如果不需要绑定自己的域名，那么删掉 CNAME 文件。

3. 修改配置。

   网站的配置基本都集中在 \_config.yml 文件中，将其中与个人信息相关的部分替换成你自己的，比如网站的 url、title、subtitle 和第三方评论模块的配置等。

   **评论模块：** 目前支持 disqus、gitment 和 gitalk，选用其中一种就可以了，推荐使用 gitalk。它们各自的配置指南链接在 \_config.yml 文件的 Comments 一节里都贴出来了。

   **注意：** 如果使用 disqus，因为 disqus 处理用户名与域名白名单的策略存在缺陷，请一定将 disqus.username 修改成你自己的，否则请将该字段留空。我对该缺陷的记录见 [Issues#2][3]。

4. 删除我的文章与图片。

   如下文件夹中除了 template.md 文件外，都可以全部删除，然后添加你自己的内容。

   * \_posts 文件夹中是我已发布的博客文章。
   * \_drafts 文件夹中是我尚未发布的博客文章。
   * \_wiki 文件夹中是我已发布的 wiki 页面。
   * images 文件夹中是我的文章和页面里使用的图片。

5. 修改「关于」页面。

   pages/about.md 文件内容对应网站的「关于」页面，里面的内容多为个人相关，将它们替换成你自己的信息，包括 \_data 目录下的 skills.yml 和 social.yml 文件里的数据。


## 经验与思考

### 一、Jekyll

​	**1.Jekyll是什么？**

​			Jekyll就是将纯文本转化为静态博客网站，不需要数据库支持，也没有评论功能，想要评论功能的话可以借助第三方的评论服务。
 Jekyll + Github Pages可以让你更加专注于博客内容，而不是如何搭建一个博客平台。

​	**2.目录结构**

```ruby
.
├──_config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _site
├── .jekyll-metadata
└── index.html
```

每个目录的作用是什么：

文件夹_layouts：用于存放模板的文件夹

文件夹_posts：用于存放博客文章的文件夹，里面是markdown格式的文章

文件夹_drafts:  drafts（草稿）是未发布的文章。这些文件的格式中都没有 `title.MARKUP` 数据。学习如何 [使用草稿](https://link.jianshu.com?t=http%3A%2F%2Fjekyllcn.com%2Fdocs%2Fdrafts%2F).

文件夹__includes ：  你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签 `{% include file.ext %}` 来把文件 `_includes/file.ext` 包含进来。

文件夹_data ：  格式化好的网站数据应放在这里。jekyll 的引擎会自动加载在该目录下所有的 yaml 文件（后缀是 `.yml`, `.yaml`, `.json` 或者 `.csv` ）。这些文件可以经由 ｀site.data｀ 访问。如果有一个 `members.yml` 文件在该目录下，你就可以通过 `site.data.members` 获取该文件的内容。

文件夹css：存放博客所用css的文件夹

_coinfig.yml：jekyll的配置文件，里面可以定义相当多的配置参数，具体配置参数可以参照其官网

index.html：项目的首页

### 二、什么是Github Pages？

​		GitHub Pages 是一个静态网站托管服务，直接从github仓库托管你个人、公司或者项目页面 ，并且不需要你写任何后端语言来支持。

​	**1.markdown文件的头信息**

​		如下所示：

```css
---
layout: post
title: template page
categories: [cate1, cate2]
description: some word here
keywords: keyword1, keyword2
---

...
这里就可以使用markdown格式或其他格式写博客内容啦
```

| 变量名称                 | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| layout                   | 如果设置的话，会指定使用该模板文件。指定模板文件时候不需要文件扩展名。模板文件必须放在 _layouts 目录下。 |
| permalink                | 如果你需要让你发布的博客的 URL 地址不同于默认值 /year/month/day/title.html，那你就设置这个变量，然后变量值就会作为最终的 URL 地址。 |
| published                | 如果你不想在站点生成后展示某篇特定的博文，那么就设置（该博文的）该变量为 false。 |
| `date`                   | 这里的日期会覆盖文章名字中的日期。这样就可以用来保障文章排序的正确。日期的具体格式为`YYYY-MM-DD HH:MM:SS +/-TTTT`；时，分，秒和时区都是可选的。 |
| `category`、`categories` | 除过将博客文章放在某个文件夹下面外，你还可以指定博客的一个或者多个分类属性。这样当你的站点生成后，这些文章就可以根据这些分类来阅读。`categories` 可以通过 [YAML list](https://link.jianshu.com?t=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FYAML%23Lists)，或者以逗号隔开的字符串指定。 |
| `tags`                   | 类似分类 `categories`，一篇文章也可以给它增加一个或者多个标签。同样，`tags` 可以通过 YAML 列表或者以逗号隔开的字符串指定。 |

除了这些预定义的变量，也可以自定义变量，然后在布局文件中`{{ page.自定义变量 }}`来引用



### 三、搭建

​		Github Pages + Jekyll 方案

​		**步骤：**

​				**1.注册Github**

​				**2.域名【可选】**

​						1）去买域名

　　				2）用Github pages提供的免费域名

```php+HTML
			http://{username}.github.io //用你的Github用户名替换网址中的{username}`
```

​			**3.安装Git环境**

​					在打开的命令行窗口（Shell）内执行以下命令，设置你的git用户名和邮箱：

```php+HTML
$ git config --global user.name "{username}"          // 用你的用户名替换{username}

$ git config --global user.email "{name@site.com}"    // 用你的邮箱替换{name@site.com}
```

​		 **4.SSH配置**

在刚才打开的Shell内执行，配置SSH：

```php+HTML
$ ssh-keygen -t rsa -C"{name@site.com}"    // 用你的邮箱替换{name@site.com}
```

可以不输入其他信息，一直敲回车直到命令完成。 这时你的用户目录（win7以上系统默认在C:\Users\你的计算机用户名）内会出现名为 .ssh 的文件夹，点进去能看到 id_rsa 和 id_rsa.pub两个文件，其中 id_rsa 是私钥，不能让怪人拿走， id_rsa.pub 是公钥，无需保密。

　　接下来用你的浏览器登录Github，点击右上角的“Settings”：

![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707151228124-1968073768.png) 

　　用文字处理软件打开刚才的 id_rsa.pub 文件，复制全部内容。
　　点击“SSH and GPG Keys”，

![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707151304202-1940540173.png)

　　点击“New SSH Key”，将复制的内容粘贴在Key中，点“Add Key”确定。

![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707151401764-1032458181.png)





**5.创建项目**

1）Fork（Git系统的创建分支，简单来说是把当前仓库复制一份到你的仓库，你可以进行修改，因为你的仓库是原来仓库的新的分支）已有的开源博客仓库，在巨人的肩膀上进行符合自我的创作（找个大神的作品自己改改）。

　　可以去这里挑：

　　https://github.com/jekyll/jekyll/wiki/sites

　　http://jekyllthemes.org/

​		https://github.com/mzlogin/mzlogin.github.io

　　这个就挺好，知乎上看到的：https://github.com/Huxpro/huxpro.github.io

　　然后点fork：

![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707151648624-2068681510.png)

　　去主页里找到刚才fork的分支：

 ![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707151701342-700212220.png)

　　点击“Settings”，将“Repository name”改为 **{你的Github用户名}.github.io**，点击“Rename”。

 ![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707151835811-990829233.png)

　　此时就可以通过 **http://{你的Github用户名}.github.io** 访问你fork下来的网站了。

　　2）自建

　　自建比较慢，以后讨论。

**6.写东西**

　　1）克隆

　　再次打开Git Bash，输入以下命令切换到你想放置本地代码仓库的位置：

```
$ cd {本地路径}     // 比如：cd d:/hahah
```

　　或者随便找个地方右键Git Bash。

　　clone（克隆）你自己的远程仓库：

```
$ git clone https://github.com/{username}/{username}.github.io.git     // 用你的Github用户名替换{username}
```

　　失败的话可能是打错了或者网不好，网不好的话可以找工具tiao墙，网慢就等一会：

 ![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707152148139-1652767097.png)

　　2）写博客

　　打开本地的 _posts 文件夹，你的所有博文都将放在这里，写新博文只需要新建一个标准文件名的文件，在文件中编写文章内容。 比如我们fork的模版中 _posts 文件夹里有一篇2014-01-29-hello-2015.markdown，你的文件命名也要严格遵循 年-月-日-文章标题.文档格式 这样的格式，注意月份和日期是两位数。

![img](https://images2015.cnblogs.com/blog/899901/201607/899901-20160707152650546-1014659669.png)

　　推荐使用Markdown语言写文章，windows下推荐MarkdownPad这个软件编写Markdown文本。

　　最开始写可以直接模仿别人的博文语法，更多Markdown语法可参考 [认识与入门Markdown](http://sspai.com/25137)。

　　3）修改和提交

　　当你使用Git Bash对你的本地仓库进行操作时，先用 cd 命令将你的工作目录设置到你要操作的本地仓库

```
$ cd {你刚才clone下来的项目文件夹路径}
```

　　每当你对本地仓库里的文件进行了修改，只需在Bash中依次执行以下三个命令即可将修改同步到Github，刷新网站页面就能看到修改后的网页：

```
$ git add .

$ git commit -m "statement"   //此处statement填写此次提交修改的内容，作为日后查阅

$ git push origin master
```

　　报错的情况会单独讨论。

​	**7.git发布相关**

```php+HTML
A、下载相关
git clone https://github.com/852172891/test3.git #把项目下载到本地

B、提交相关
git init
git add .
git commit -m "first commit"  #（first commit 本次提交的内容）
git remote add origin https://github.com/852172891/test3.git #（地址换成你建的项目的地址，不知道的话看下边 项目地址是哪个的图）
git pull origin master --allow-unrelated-histories #把远程仓库和本地同步，消除差异
git push -u origin master  #（这一句执行的时候 可能需要输入你的 github 账号 和密码）

C、更新相关
git pull

D、其他
git branch -a #查看所有分支
git checkout 分支名 #切换分支
git reflog  #提交操作的commit_id  和 一些备注信息
git checkout commit_id #找到之前提交备注的hasn值

注：恢复，需要切换后把这个文件拷贝下来，保存到一个地方，然后切换回去再添加回来
```



### 四、实例

​	

## 致谢

本博客外观基于 [mzlogin](https://github.com/mzlogin/mzlogin.github.io) 修改，感谢！


[1]: https://github.com/mzlogin/chinese-copywriting-guidelines
[2]: https://help.github.com/articles/setting-up-your-pages-site-locally-with-jekyll/
[3]: https://github.com/mzlogin/mzlogin.github.io/issues/2
[4]:https://www.cnblogs.com/xulei1992/p/5650329.html
[5]: https://www.jianshu.com/p/9f198d5779e6

