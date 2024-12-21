---
title: 搭建blog
date: 2024-04-23 08:54:32
categories: blog📚
index_img: https://nuyoahwjl.github.io/img/hexo-cover.png
sticky: 100 # 置顶
excerpt: 本文介绍如何使用GitHub Pages&Hexo搭建你的个人博客
---

<!-- 空格符 -->
<!-- &nbsp;&nbsp;&nbsp; -->

# **一、准备工作**
## **1.1 GitHub账号**
需要有一个`GitHub`账号，没有的话在[官网](https://github.com/)注册，可参考[Github账号申请](https://blog.csdn.net/yaorongke/article/details/119086305)。
## **1.2 安装Git**
Hexo部署到`GitHub`时需要用到，可参考[Git安装(Windows)](https://blog.csdn.net/yaorongke/article/details/119085413)。
## **1.3 安装NodeJs**
`Hexo`是基于`NodeJs`写的，需要安装`NodeJs`和`npm`，可参考[NodeJs安装及配置](https://blog.csdn.net/qq_40323256/article/details/100825982)。


# **二、创建仓库**
## **2.1**
点击`new repositories`新建一个仓库。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/1.png" alt=""style="display: block; margin: 0 auto;">
</html>

## **2.2** 
仓库名格式必须为`<用户名>.github.io`，然后下滑点击`Create repository`。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/2.png" alt=""style="display: block; margin: 0 auto;">
</html>

## **2.3** 
点击`creating a new file`创建一个新文件，作为主页。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/3.png" alt=""style="display: block; margin: 0 auto;">
</html>

## **2.4** 
新文件名字必须为`index.html`，内容先随便写一个简单的，示例如下，填写之后点击`Commit new file`提交。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HLxxx01</title>
</head>
<body>
    <h1>HLxxx01's blog</h1>
    <h1>Hello ~</h1>
</body>
</html>
```
<html>
<img src="https://nuyoahwjl.github.io/your-blog/4.png" alt=""style="display: block; margin: 0 auto;">
</html>

## **2.5** 
在`GitHub Pages`中找到我们主页的地址为 hlxxx01.github.io，在浏览器中访问(这里只是为了演示`Github Pages`的使用)。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/5.png" alt=""style="display: block; margin: 0 auto;">
</html>

## **2.6** 
预览。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/6.png" alt=""style="display: block; margin: 0 auto;">
</html>


# **三、安装Hexo**
{% note warning %}
以下内容均需在命令行提示符`cmd`中运行。
‘win + R ’ 打开命令行窗口，输入 ‘cmd’ 并回车。
{% endnote %}
## **3.1** 安装`Hexo`
``` bash
npm install -g hexo-cli
```
## **3.2** 创建`hexo-blog`项目
``` bash
hexo init hexo-blog
cd hexo-blog
npm install
//项目名称自拟
//默认在C盘创建
``` 
## **3.3** 本地启动
``` bash
hexo g
hexo server
```
浏览器访问 localhost:4000，查看默认风格。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/7.png" alt=""style="display: block; margin: 0 auto;">
</html>


# **四、更换主题**
{% note warning %}
`Hexo`默认的主题不太好看，不过官方提供了数百种主题供用户选择，可以根据个人喜好更换，官网主题点[这里](https://hexo.io/themes/)查看。个人比较喜欢`Fluid`，后面章节的功能也是以`Fluid`为基础进行讲解的。
{% endnote %}
## **4.1 安装主题**
下载[最新release版本](https://gitcode.com/fluid-dev/hexo-theme-fluid/releases?utm_source=csdn_github_accelerator&isLogin=1)解压到`themes`目录，并将解压出的文件夹重命名为`fluid`。

## **4.2 指定主题**
如下修改`Hexo`博客目录中的`_config.yml`：
``` yaml
theme: fluid  # 指定主题
language: zh-CN  # 指定语言，会影响主题显示的语言
```
## **4.3 本地启动**
``` bash
hexo g -d
hexo s
```
浏览器访问 localhost:4000，查看`fluid`风格。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/8.png" alt=""style="display: block; margin: 0 auto;">
</html>

## **4.4 创建文章**
如下修改`Hexo`博客目录中的`_config.yml`，打开这个配置是为了在生成文章的时候生成一个同名的资源目录用于存放图片文件。
``` yaml
post_asset_folder: true
```
在`cmd`窗口执行如下命令创建一篇新文章，名为《测试文章》。
``` bash
hexo new post 测试文章
```
* **个性化：[post页配置指南](#523-导航菜单)**


# **五、配置指南**
## **5.1 关于指南**
{% note success %}
- 本指南中提到的："站点配置" 指的`Hexo`博客目录下的`_config.yml`，"主题配置" 指的是`theme/fluid/_config.yml`或者 `_config.fluid.yml`，注意区分；
- 本指南中提到的`source`目录都指的是博客目录下的`source`文件夹，不推荐修改主题内`source`目录；
- 每次无论`hexo g`或`hexo s`，都最好先使用`hexo clean`清除本地缓存；
- 页面结果以本地`hexo s`为准，部署后的异常大部分是线上缓存原因，在确认没有报错的情况下，等待若干时间后即可正常；
{% endnote %}

## **5.2 全局**
### **5.2.1 博客标题**
页面左上角的博客标题，默认使用<u>**站点配置**</u>中的`title`，这个配置同时控制着网页在浏览器标签中的标题。
如需单独区别设置，可在<u>**主题配置**</u>中设置：
``` yaml
navbar:
  blog_title: 博客标题
```

### **5.2.2 页面顶部大图**
#### *图片来源：*
  
<u>**主题配置**</u>中，每个页面都有名为`banner_img`的属性，可以使用本地图片的相对路径，也可以为外站链接，比如：<br>
指向本地图片：

``` yaml
banner_img: /img/bg/example.jpg   # 对应存放在 /source/img/bg/example.jpg
```
指向外站链接：

``` yaml
banner_img: https://static.zkqiang.cn/example.jpg
```

{% note success %}
如果是本地图片，目录文件夹可自定义，但必须在`source`目录下，博客与主题的`source`目录最终会合并，因此优先选择博客的 `source`。
图片大小建议压缩到 1MB 以内，否则会严重拖慢页面加载。
{% endnote %}

#### *高度：*

<u>**主题配置**</u>中，每个页面对应的`banner_img_height`属性，有效值为 0 - 100。100 即为全屏，个人建议 70 以上。

#### *蒙版透明度：*
  
<u>**主题配置**</u>中，每个页面对应的`banner_mask_alpha`属性，有效值为 0 - 1.0， 0 是完全透明（无蒙版），1 是完全不透明。

{% note success %}
每篇文章可单独设置`Banner`，具体见文章页设置。

本主题不支持固定背景（fixed），原因：
1.与目前代码结构有较大冲突，需要大量修改。
2.`fixed`在移动端兼容性很差。
{% endnote %}

### **5.2.3 导航菜单**
``` yaml
navbar:
  menu:
    - { key: 'home', link: '/', icon: 'iconfont icon-home-fill' }
    - { key: 'tag', link: '/tags/', icon: 'iconfont icon-tags-fill' }
    - { key: 'about', link: '/about/', icon: 'iconfont icon-user-fill', name: '联系我' }
```
- `key`: 用于关联有[语言配置](#44-创建关于页)，如不存在关联则显示`key`本身的值
- `link`: 跳转链接
- `icon`: 图标的 css class，可以省略（即没有图标），主题内置图标详见[这里](https://nuyoahwjl.github.io/your-blog/9.png)
- `name`: 强制使用此名称显示（不再按语言配置显示），可省略

另外支持二级菜单（下拉菜单），配置写法如下：
``` yaml
menu:
  - {
      key: '文档',
      icon: 'iconfont icon-books',
      submenu: [
        { key: '主题博客', link: 'https://hexo.fluid-dev.com/' },
        { key: '配置指南', link: 'https://hexo.fluid-dev.com/docs/guide/' },
        { key: '图标用法', link: 'https://hexo.fluid-dev.com/docs/icon/' }
      ]
  }
```

### **5.2.4 懒加载**
懒加载又称延迟加载。开启后，当图片或评论插件滚动到可见范围内才会加载，可以大幅提高打开网页的速度。

该功能默认开启，可以在<u>**主题配置**</u>中修改参数：
``` yaml
lazyload:
  enable: true
  loading_img: /img/loading.gif
  onlypost: false
  offset_factor: 2
```
`loading_img`: 指定加载时的占位图片。

`onlypost`: 为 true 时，懒加载仅在文章页生效，如果自定义页面需要使用，可以在[front-matter](https://hexo.io/zh-cn/docs/front-matter)里指定 `lazyload: true`。

`offset_factor`: 触发加载的偏移倍数，基数是视窗高度（即提前 N 屏高度触发加载），可根据部署环境的请求速度调节。

### **5.2.5 全局字体**
所有页面统一字体的字号和字族可以通过<u>**主题配置**</u>中的下列配置项设置：
``` yaml
font:  # 主题字体配置
  font_size: 16px        # 全局字号
  font_family:           # 全局字体族
  code_font_size: 85%    # 代码的字号
```
关于字体族（`font-family`）如果不了解可以看[这篇文章](https://developer.mozilla.org/zh-CN/docs/Web/CSS/font-family)先了解一下。

需要注意：

- 最好使用系统自带的字体，否则需要通过[自定义功能](#528-自定义-js--css--html)额外引入`@font-face`，字体一般较大，不建议引入
- 应当至少添加一个通用的字体族名（如`serif`，具体见上方链接文章）


如果想设置单独的页面，可以直接在 markdown 里通过 style 标签实现：
``` html
---
title: example
---

<style>
  /* 设置整个页面的字体 */
  html, body, .markdown-body {
    font-family: KaiTi,"Microsoft YaHei",Georgia, sans, serif;
    font-size: 15px;
  }

  /* 只设置 markdown 字体 */
  .markdown-body {
    font-family: KaiTi,"Microsoft YaHei",Georgia, sans, serif;
    font-size: 15px;
  }
</style>
```

### **5.2.6 网页统计**
{% note success %}
统计数据来源，使用 leancloud 需要设置 `web_analytics: leancloud` 中的参数；使用 busuanzi 不需要额外设置，但是有时不稳定。
本文使用leanclou。
{% endnote %}
#### *step1 申请LeanCloud账号并创建应用*
进入[官网](https://console.leancloud.cn/)注册账号。<br>
注册成功后实名认证并绑定邮箱。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/10.png" alt=""style="display: block; margin: 0 auto;">
</html>

#### *step2 创建应用，选择`开发版`即可*
<html>
<img src="https://nuyoahwjl.github.io/your-blog/11.png" alt=""style="display: block; margin: 0 auto;">
</html>

#### *step3 进入该应用的`设置->应用凭证`*
找到`AppID`、`AppKey`、`API`，记录下来，后面配置要用。
<html>
<img src="https://nuyoahwjl.github.io/your-blog/12.png" alt=""style="display: block; margin: 0 auto;">
</html>

#### *step4 修改Fluid配置*
打开主题目录`themes\fluid`下的`_config.yml`文件，修改如下配置:

打开统计开关
``` yaml
# 网页访问统计
web_analytics:
    enable: true
    # 遵循访客浏览器"请勿追踪"的设置，如果开启则不统计其访问
    # See: https://www.w3.org/TR/tracking-dnt/
    follow_dnt: true
```
配置`leancloud`的`app_id`、`AppKey`、`API`
``` yaml
# LeanCloud 计数统计，可用于 PV UV 展示，如果 `web_analytics: enable` 没有开启，PV UV 展示只会查询不会增加
leancloud:
    app_id: 
    app_key: 
    # REST API 服务器地址，国际版不填
    server_url: 
    # 统计页面时获取路径的属性
    path: window.location.pathname
    # 开启后不统计本地路径( localhost 与 127.0.0.1 )
    ignore_local: false
```
展示网站的 PV、UV 统计数
``` yaml
# 展示网站的 PV、UV 统计数
# Display website PV and UV statistics
statistics:
    enable: true
    # Options: busuanzi | leancloud
    source: "leancloud"  
    pv_format: '🚀总访问量 {} 次'
    uv_format: '😶‍🌫️总访客数 {} 人'
```

### **5.2.7 语言配置**
设置语言是在<u>**站点配置**</u>中，需要对应`fluid/languages/`目录内的配置文件名:
``` yaml
language: zh-CN
```
你可以在主题[languages](https://github.com/fluid-dev/hexo-theme-fluid/tree/master/languages)目录里查看支持哪些语言，只要上面的配置的值和文件名相同即可。

### **5.2.8 自定义 JS / CSS / HTML**
如果你想引入外部的 JS、CSS（比如 IconFont）或 HTML，可以通过以下<u>**主题配置**</u>，具体见注释：
``` yaml
# 指定自定义 js 文件路径，路径是相对 source 目录
custom_js: /js/custom.js

# 指定自定义 css 文件路径，路径是相对 source 目录
custom_css: /css/custom.css

# 自定义 <head> 节点中的 HTML 内容
custom_head: '<meta name="key" content="value">'

# 自定义底部 HTML 内容（位于 footer 上方），也可用于外部引入 js css 这些操作，注意不要和 post.custom 配置冲突
custom_html: '<link rel="stylesheet" href="//at.alicdn.com/t/font_1067060_qzomjdt8bmp.css">'
```
另外`custom_js`和`custom_css`都可以指定多个路径：
``` yaml
custom_css:
  - /css/custom.css
  - //at.alicdn.com/t/font_1736178_ijqayz9ro8k.css
```

### **5.2.9 暗色模式**
主题暗色模式，开启后菜单中会出现切换按钮。
``` yaml
dark_mode:
  enable: true
  default: auto
```
`default`是暗色默认的模式，可选参数：`auto`/`light`/`dark`。

选择`auto`时优先遵循 [prefers-color-scheme](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media/prefers-color-scheme)，如果不支持则按用户本地时间 18 点到次日 6 点之间进入暗色模式。


## **5.3 首页**
### **5.3.1 Slogan(打字机)**
首页大图中的标题文字，可在<u>**主题配置**</u>中设定是否开启：
``` yaml
index:
  slogan:
    enable: true
    text: 这是一条 Slogan
    api:
      enable: false
      url: "https://v1.hitokoto.cn/"
      method: "GET"
      headers: {}
      keys: ["hitokoto"]
```
如果`text`为空则按站点配置的`subtitle`显示。

另外支持通过API接口获取内容，如果请求失败则按`text`字段显示：

- `url`: API 地址，必须返回的是一个JSON格式

- `method`: 请求方法，可选`GET`、`POST`、`PUT`

- `headers`: 请求头，如果接口需要传一些验证的头部信息，在这里设置

- `keys`: 从请求结果获取字符串的取值字段，程序会根据列表中的字段依次取值，最终需要获得到一个字符串

例如 API 返回的内容为：
``` json
[
    {
        "data": {
            "author": "Fluid",
            "content": "An elegant theme"
        }
    },
    {
        "data": {
            "author": "Test",
            "content": "Test content"
        }
    }
]
```
设置`keys: ["data", "content"]`，程序会如下执行：
- 由于返回体是列表，程序会首先获取第一个元素（不是列表则跳过此步骤）
- 通过第一个 key`data`获取值，发现不是一个字符串，继续执行
- 通过第二个 key`content`获取值，发现是一个字符串，返回内容；如果不是字符串则获取失败，使用text值

标题文字默认开启了打字机动效，相关配置如下:
``` yaml
fun_features:
  typing: # 为 subtitle 添加打字机效果
    enable: true
    typeSpeed: 70 # 打印速度
    cursorChar: "_" # 游标字符
    loop: false # 是否循环播放效果
```
{% note success %}
请求 API 的功能必须同时开启打字机动效才能生效
{% endnote %}

### **5.3.2 文章摘要**
开关自动摘要（默认开启）：
``` yaml
index:
  auto_excerpt:
    enable: true
```
若要手动指定摘要，使用`<!-- more -->`在MD文档里划分，如：
``` md
正文的一部分作为摘要
<!-- more -->
余下的正文
```
或者在[front-matter](https://hexo.io/zh-cn/docs/front-matter)里设置`excerpt`字段，如：
``` yaml
---
title: 这是标题
excerpt: 这是摘要
---
```
{% note success %}
优先级: 手动摘要 > 自动摘要；
如果关闭自动摘要，并且没有设置手动摘要，摘要区域空白；
无论哪种摘要都最多显示 3 行，当屏幕宽度不足时会隐藏部分摘要。
{% endnote %}

### **5.3.3 文章跳转方式**
``` yaml
index:
    post_url_target: _self
```
可选值:
- `_blank` 新标签页打开
- `_self` 当前标签页打开

### **5.3.4 文章信息**
可配置隐藏包括发布时间、分类、标签。
``` yaml
index:
  post_meta:
    date: true
    category: true
    tag: true
```

### **5.3.5 文章排序**
如果想手动将某些文章固定在首页靠前的位置，可以在安装 `hexo-generator-index`>=2.0.0 版本的情况下，在文章开头 [front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置`sticky`属性：
``` yaml
---
title: 文章标题
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
sticky: 100
---
以下是文章内容
```
`sticky`数值越大，该文章越靠前，达到类似于置顶的效果，其他未设置的文章依然按默认排序。

### **5.3.6 隐藏文章**
如果想把某些文章隐藏，不在首页和其他归档分类页里展示，可以在文章开头[ront-matter](https://hexo.io/zh-cn/docs/front-matter)中配置`hide: true`属性。
``` yaml
---
title: 文章标题
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
hide: true
---
以下是文章内容
```
如果只是想让文章在首页隐藏，但仍需要在归档分类页里展示，可以在文章开头[front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置`archive: true`属性。
``` yaml
---
title: 文章标题
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
archive: true
---
以下是文章内容
```

## **5.4 文章页**
### **5.4.1 文章在首页的封面图**
对于单篇文章，在文章开头[front-matter](https://hexo.io/zh-cn/docs/front-matter)中配置`index_img`属性。
``` yaml
---
title: 文章标题
tags: [Hexo, Fluid]
index_img: /img/example.jpg
date: 2019-10-10 10:00:00
---
以下是文章内容
```
和Banner配置相同，`/img/example.jpg`对应的是存放在`/source/img/example.jpg`目录下的图片，也可以使用外链`Url`的绝对路径。

如果想统一给文章设置一个默认图片（文章不设置`index_img`则默认使用这张图片），可在<u>**主题配置**</u>中设置：
``` yaml
post:
    default_index_img: /img/example.jpg
```
当`default_index_img`和`index_img`都为空时，该文章在首页将不显示图片。

### **5.4.2 文章页顶部大图**
默认显示<u>**主题配置**</u>中的`post.banner_img`，如需要设置单个文章的Banner，在[front-matter](https://hexo.io/zh-cn/docs/front-matter)中指定`banner_img`属性。
``` yaml
---
title: 文章标题
tags: [Hexo, Fluid]
index_img: /img/example.jpg
banner_img: /img/post_banner.jpg
date: 2019-10-10 10:00:00
---
以下是文章内容
```

### **5.4.3 日期/字数/阅读时长/阅读数**
``` yaml
post:
  meta:
    author:  # 作者，优先根据 front-matter 里 author 字段，其次是 hexo 配置中 author 值
      enable: false
    date:  # 文章日期，优先根据 front-matter 里 date 字段，其次是 md 文件日期
      enable: true
      format: "dddd, MMMM Do YYYY, h:mm a"  # 格式参照 ISO-8601 日期格式化
    wordcount:  # 字数统计
      enable: true
      format: "{} 字"  # 显示的文本，{}是数字的占位符（必须包含)，下同
    min2read:  # 阅读时间
      enable: true
      format: "{} 分钟"
    views:  # 阅读次数
      enable: false
      source: "leancloud"  # 统计数据来源，可选：leancloud | busuanzi   注意不蒜子会间歇抽风
      format: "{} 次"
```

### **5.4.4 代码块**
``` yaml 
code:
  copy_btn: true
  highlight:
    enable: true
    line_number: true
    lib: "highlightjs"
    highlightjs:
      style: 'Github Gist'
      bg_color: false
    prismjs:
      style: "default"
      preprocess: true
```
- `copy_btn`: 是否开启复制代码的按钮
- `line_number`: 是否开启行号
- `highlight`: 是否开启代码高亮
- `lib`: 选择生成高亮的库，可选项: highlightjs、prismjs

### **5.4.5 脚注**
主题内置了脚注语法支持，可以在文章末尾自动生成带有锚点的脚注，该功能在<u>**主题配置**</u>中默认开启：
``` yaml
post:
  footnote:
    enable: true
    header: ''
```
脚注语法如下：
``` md
这是一句话[^1]
[^1]: 这是对应的脚注
```
更优雅的使用方式，是将脚注写在文末，比如：
``` md
正文

## 参考
[^1]: 参考资料1
[^2]: 参考资料2
```

### **5.4.6 Tag插件**
#### *便签*
在 markdown 中加入如下的代码来使用便签：
``` md
{% note success %}
文字 或者 `markdown` 均可
{% endnote %}
```
或者使用 HTML 形式：
``` html
<p class="note note-primary">标签</p>
```
{% fold info @可选便签 %}
{% note primary %}
primary
{% endnote %}
{% note secondary %}
secondary
{% endnote %}
{% note success %}
success
{% endnote %}
{% note danger %}
danger
{% endnote %}
{% note warning %}
warning
{% endnote %}
{% note info %}
info
{% endnote %}
{% note light %}
light
{% endnote %}
{% endfold %}

#### *行内标签*
在 markdown 中加入如下的代码来使用 Label：
``` md
{% label primary @text %}
```
或者使用 HTML 形式：
``` html
<span class="label label-primary">Label</span>
```
{% fold info @可选Label %}
{% label primary @primary %}
{% label default @default %}
{% label info @info %}
{% label success @success %}
{% label warning @warning %}
{% label danger @danger %}
{% endfold %}

#### *按钮*
在 markdown 中加入如下的代码来使用 Button：
``` md
{% btn url, text, title %}
```
或者使用 HTML 形式：
``` html
<a class="btn" href="url" title="title">text</a>
```
- `url`：跳转链接
- `text`：显示的文字
- `title`：鼠标悬停时显示的文字（可选）

#### *组图*
如果想把多张图片按一定布局组合显示，你可以在 markdown 中按如下格式：
``` md
{% gi total n1-n2-... %}
  ![](url)
  ![](url)
  ![](url)
  ![](url)
  ![](url)
{% endgi %}
```
- `total`：图片总数量，对应中间包含的图片 url 数量
- `n1-n2-...`：每行的图片数量，可以省略，默认单行最多 3 张图，求和必须相等于 total，否则按默认样式

## **5.5 归档页**
具体见配置文件注释
``` yaml
menu:
    - { key: "archive", link: "/archives/", icon: "iconfont icon-archive-fill" }
```

## **5.6 分类页**
具体见配置文件注释
``` yaml
menu:
    - { key: "category", link: "/categories/", icon: "iconfont icon-category-fill" }
```

## **5.7 标签页**
具体见配置文件注释
``` yaml
menu:
     - { key: "tag", link: "/tags/", icon: "iconfont icon-tags-fill" }
```

## **5.8 关于页**
### **5.8.1 创建关于页**
首次使用主题的「关于页」需要手动创建，在`cmd`窗口执行：
``` bash
hexo new page about
```
创建成功后，编辑博客目录下`/source/about/index.md`，添加`layout`属性:
``` yaml
---
title: about
date: 2024-04-21 19:20:33
layout: about
---

这里写关于页的正文，支持 Markdown, HTML
```

### **5.8.2 关于信息**
在关于页介绍自己的基础信息，可以在<u>**主题配置**</u>中设置：
``` yaml
about:
  avatar: /img/avatar.png
  name: "Fluid"
  intro: "An elegant theme for Hexo"
```

### **5.8.3 社交页图标**
#### *内置图标*
在<u>**主题配置**</u>中设置：
``` yaml
about:
  icons:
    - { class: 'iconfont icon-github-fill', link: 'https://github.com', tip: 'GitHub' }
    - { class: 'iconfont icon-douban-fill', link: 'https://douban.com', tip: '豆瓣' }
    - { class: 'iconfont icon-wechat-fill', qrcode: '/img/favicon.png' }
```
- `class`: 图标的 css class，主题内置图标详见[这里](https://nuyoahwjl.github.io/your-blog/9.png)
- `link`: 跳转链接
- `tip`: 鼠标悬浮在图标上显示的提示文字
- `qrcode`: 二维码图片，当使用此字段后，点击不再跳转，而是悬浮二维码

#### *自定义图标*
[Iconfont](https://www.iconfont.cn/)支持用户创建项目来管理和使用图标库，在`图标管理-我的项目`中即可管理和创建项目。将所需图标添加至购物车，再通过购物车添加至所创建的项目中。在项目中可以下载至本地与生成在线链接，Iconfont 支持在阿里云的 CDN 中生成 CSS 或 JS 文件用来调用。

生成在线链接后，将链接替换到<u>**主题配置**</u>的 iconfont 配置项中，但注意替换后**原内置的图标库将全部失效**。

在每次有删减项目中图标库目录时，需要点击重新生成链接并替换到配置链接。

## **5.9 友情链接页**
友情链接页用于展示好友的博客入口，默认关闭，开启需要先在`navbar`项中`links`的注释(#号)删掉：
``` yaml
navbar:
  menu:
    - { key: 'links', link: '/links/', icon: 'iconfont icon-link-fill' }
```
然后找到`links`的配置项，对页面内容进行配置：
``` yaml
links:
  items:
    - {
      title: 'Fluid Docs',
      intro: '主题使用指南',
      link: 'https://hexo.fluid-dev.com/docs/',
      avatar: '/img/favicon.png'
    }
  default_avatar: /img/avatar.png
```
- `title`: 友链站的标题
- `intro`: 站点或博主的简介，可省略
- `link`: 跳转链接
- `avatar`: 头像图片，可省略
- `default_avatar`: 成员的默认头像(仅在指定了头像并且加载失败时生效)

## **5.10 404页**
404 页是在访问不存在的博客链接时，出现的错误提示页面。

开启此页面需要在博客的部署环境上配置：

- 如果博客部署在云服务器，需要 Nginx 配置文件设置`error_page 404 = /404.html`
- 如果部署在 GitHub Pages 上，不需要额外配置，但必须绑定顶级域名才生效
- 其他 OSS 等平台，请参考各平台关于 404 页的配置文档，但并不是所有平台都支持跳转 Html。

# **六、发布到GitHub Pages**
## **方式一**
安装hexo-deployer-git
``` bash
npm install hexo-deployer-git --save
```
修改根目录下的`_config.yml`，配置`GitHub`相关信息
``` yaml
deploy:
  type: git
  repo: https://github.com/Nuyoahwjl/Nuyoahwjl.github.io.git
  branch: main
  token: 你的token
```
`token`为`GitHub`的`Personal access tokens`，获取方式如下图
<html>
<img src="https://nuyoahwjl.github.io/your-blog/13.png" alt=""style="display: block; margin: 0 auto;">
</html>

部署到GitHub
``` bash
hexo g -d
```
浏览器访问`GitHub Pages`，部署成功

## **方式二**
直接将`public`目录中的文件和目录推送至`GitHub`仓库和分支中。