---
layout: mypost
title:  "如何白嫖github pages搭建个人博客"
categories: [jekyll]
---

## 1、缘由
最近忽然想开始写博客了，一方面作为记录，方便后续遇到问题可以快速查阅，另一个方面也想分享下学习到的知识。

## 2、选型
问了下AI推荐的博客平台，给出了诸如CSDN、掘金、简书、博客园等推荐，但是从2024年这个节点来看，CSDN广告多和重复的文章多、博客园深陷倒闭边缘等，自己搭建博客需要购买服务器和域名等，成本过高，所以最终选择了github pages

## 3、具体过程
### 3.1、创建仓库
打开github，新建一个公开仓库，名称按自己喜好来，如图：

![img.png](1.png)

![img.png](2.png)

### 3.2、配置github pages
打开仓库的settings的Pages目录，Source选择Github Actions，页面会刷新下，并出现Github Pages Jekyll，点击Configure，弹出新页面，点击Commit changes按钮，如图：

![img.png](3.png)

![img.png](4.png)

![img.png](5.png)

上述步骤其实就是配置了通过github自带的CI工具（github actions）来部署博客，github pages内置支持了jekyll，那么jekyll是什么呢？

Jekyll是一个静态网站生成器，可以快速搭建博客，并且支持Markdown语法，并且可以自定义主题。

### 3.3、安装Jekyll
接下来我们需要安装jekyll，它是Ruby 语言写的，所以需要ruby环境

1、安装ruby环境，去官网下载ruby安装包：https://rubyinstaller.org/downloads/，安装过程遇到命令行，按回车即可（默认选项）

2、安装jekyll，打开cmd，输入`gem install jekyll bundler`，等待安装完毕后，在命令行输入`jekyll -v`验证是否安装成功

3、把刚才的仓库clone到本地，并进入目录，执行`jekyll new . --force`，等待安装完毕后，再执行`jekyll serve`，访问http://localhost:4000/，即可看到本地预览效果。

### 3.4、相关配置
其实在3.2的步骤中，已经配置了github action，也就是我们仓库里面的jekyll-gh-pages.yml文件，这个文件我们不用做任何调整，但是可以大概看下，知道workflow里面干了啥，关于github action的workflow yml怎么编写，这块我准备后面在专项学习下，暂时跳过。

接着我们打开_config.yml，相关配置可以按自己喜好修改，值得注意的是baseurl，我一开始用的默认值，本地测试环境是ok的，但是github pages的页面css样式丢失，把baseurl改为仓库名称后就正常了

![img.png](6.png)

### 3.5、测试和发布第一个帖子
在_posts目录，参考默认的模板，新建一个文件，如2024-09-22-如何白嫖github pages搭建个人博客.markdown，这边要注意的是文件命名必须是`年-月-日-xxx.markdown`，这是因为jekyll默认按照这个命名规范识别的，接下来就是编写帖子了，完全按照markdown语法写即可。

编写完毕后，本地git提交相关文件，github pages会自动部署，访问http://your_username.github.io/blog/2024/09/22/如何白嫖github pages搭建个人博客.html即可看到效果

## 4、总结
通过github pages+jekyll，我们可以搭建一个自己的博客，而通过github action可以让我们自动化进行部署。

下一步计划：

1、研究下jekyll，包括模板、主题等。

2、研究下github actions，包括workflow yml编写等。



