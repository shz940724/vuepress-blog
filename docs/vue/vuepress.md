---
title: vuepress-theme-reco
date: 2022-01-24
tags:
 - vue
categories:
 - 前端
---

# vuepress搭建个人博客

# 1.介绍

> Vuepress是一个以 Vue 驱动的主题系统的简约静态网站生成工具,是一个为编写技术文档而优化的默认主题。它是为了支持 Vue 子项目的文档需求而创建的.
>
> 每一个由 VuePress 生成的页面都带有预渲染好的 HTML，也因此具有非常好的加载性能和搜索引擎优化（SEO）。同时，一旦页面被加载，Vue 将接管这些静态内容，并将其转换成一个完整的单页应用（SPA），其他的页面则会只在用户浏览到的时候才按需加载

# 2.官网介绍

> https://vuepress.vuejs.org

# 3.基于[vuepress-theme-reco](https://vuepress-theme-reco.recoluan.com/)主题,快速搭建个人博客

## 3.1 快速开始

> 在终端执行如下命令:

```
# 初始化
npm install @vuepress-reco/theme-cli -g
theme-cli init
```

> 然后按提示输入项目信息,如下:

![截屏2022-01-26 上午11.39.00](https://tva1.sinaimg.cn/large/008i3skNgy1gyqxm64jusj31520femyu.jpg)

![截屏2022-01-26 上午11.50.38](https://tva1.sinaimg.cn/large/008i3skNgy1gyqxlynleej30zc0h0wgr.jpg)

>项目构建完成后,接下来进入工程目录，启动项目:

```

# 接入项目目录

cd theme-reco  #之前填入的项目名称

# 安装npm

npm install

# 运行测试环境

npm run dev

```

> 访问命令行输出的ip地址，一般为`http://localhost:8080`(若端口被占用则依次递增，以终端输出为准)，即可访问博客了！

![截屏2022-01-26 下午2.06.54](https://tva1.sinaimg.cn/large/008i3skNgy1gyr1j4nmzsj31dk0u076c.jpg)

## 3.2 工程结构

```

├─ node_modules #存放着项目所需的依赖，我们不需要关心

├─ docs  #该目录下存放您编写的文档

│  └─ theme-reco

│    ├─ api.md

│    ├─ plugin.md

│    ├─ theme.md

│    └─ README.md

├─ blogs #该目录下存放您编写的博客文章

│    ├─ category1

│    │  ├─ 2018

│    │  │  └─ 121501.md

│    │  └─ 2019

│    │    └─ 092101.md

│    ├─ category2

│    │  ├─ 2016

│    │  │  └─ 121501.md

│    │  └─ 2017

│    │    └─ 092101.md

│    └─ other

│        └─ guide.md

├─ .vuepress # 该目录下存放项目配置文件与静态资源

│  ├─ config.js #该文件用于配置项目

│  └─ public # 该目录下存放网页中所需的静态资源

│    ├─ hero.png # 首页大图

│    ├─ logo.png # 站点logo

│    ├─ favicon.ico #站点图标

│    └─ avatar.png #头像

├─ package.json #依赖管理文件

└─ README.md #这里存放着博客首页的内容

```

## 3.3 配置启动页

> 启动页展示的内容为博客标题与描述，即在创建工程时输入的内容,如果想修改,可以在`.vuepress/config.js`下找到如下内容，通过修改对应的字符来改变您的启动页

```

// .vuepress/config.js

module.exports = {

  "title": "test",

  "description": "test",

  }

```

## 3.4 配置首页

> 首页即为启动之后的主页面,首页的内容由项目根目录下的`README.md` 配置生成，您可以通过更改其中的配置项来变更你的首页

```

---

home: true  #指定该文件为您的首页，改为false则不作为首页

heroText: vuepress-theme-reco  #首页居中显示的文本

tagline: A simple and beautiful vuepress blog theme. # 首页显示的标语

# heroImage: /hero.png  #首页显示的主图，默认被注释，取消注释可显示图片

# heroImageStyle: {  # 首页主图的样式控制，默认被注释

#  maxWidth: '600px',

#  width: '100%',

#  display: block,

#  margin: '9rem auto 2rem',

#  background: '#fff',

#  borderRadius: '1rem',

# }

bgImageStyle: { #背景图片样式

  height: '450px'

}

# 以下内容基本上不生效，可以不用关心

isShowTitleInHome: false

actionText: Guide

actionLink: /views/other/guide

features:

- title: Yesterday

  details: 开发一款看着开心、写着顺手的 vuepress 博客主题

- title: Today

  details: 希望帮助更多的人花更多的时间在内容创作上，而不是博客搭建上

- title: Tomorrow

  details: 希望更多的爱好者能够参与进来，帮助这个主题更好的成长

---

```

> Tip:代码中所引用的图片，均以`.vuepress/public` 为根目录

>你会发现,在首页看到的内容远不止这些,例如:个人资料卡,文章列表这些
>
>- 文章列表是根据您的文章自动生成的，一旦您发布的文章中的含有`Front Matter`，系统会自动将其收集至首页，默认按时间顺序展示
>- 个人资料卡的头像和昵称由`.vuepress/config.js`进行配置，您可以找到如下内容，并进行修改配置。`Category`和`Tag`项则跟您的文章中标注的分类和标签自动生成

![WeChat01baf2ed571a2c69845cc17a2beabca3](https://tva1.sinaimg.cn/large/008i3skNgy1gyr2bd43e3j30vx0u0mzx.jpg)

```

    "author": "me", //昵称

    "authorAvatar": "/avatar.png", //头像
```

> `Friend Link` 则是您可以自由更改的，它的配置在`.vuepress/config.js`中，您可以找到如下内容，并对应进行修改配置

```

    "friendLink": [

      {//每一个{}中为一个友链

        "title": "白开水", //友联标题

        "desc": "越努力，越热爱，越幸运",  //友链描述

        "email": "846188037@qq.com",  //友链邮箱

        "link": "https://www.hjxie.icu" //友链地址

      },

      {

        "title": "vuepress-theme-reco",

        "desc": "A simple and beautiful vuepress Blog & Doc theme.",

        "avatar": "https://vuepress-theme-reco.recoluan.com/icon_vuepress_reco.png",

        "link": "https://vuepress-theme-reco.recoluan.com"

      }

    ],

```

## 3.5 配置底部

> 底边栏展示了如`主题`、`备案信息`、`版权`、`年份`等信息，这些内容仍需要您前往`.vuepress/config.js`进行修改

```

    "author": "me", //版权信息，与昵称为同一数据

    "record": "xxxx", //备案信息

    "startYear": "2017" //开始年份

```

## 3.6 配置导航栏

> 修改logo图片
>
> 需要前往`.vuepress/config.js`找到如下内容，修改您的logo图片，该图片存储在`.vuepress/public`中

```
    "logo": "/logo.png",
```

> 开启搜索功能
>
> 前往`.vuepress/config.js`找到如下内容，修改搜索相关配置

```
    "search": true,  //是否开启搜索

    "searchMaxSuggestions": 10,  //最多的搜索建议条目
```

> 导航
>
> 前往`.vuepress/config.js`找到如下内容，修改导航相关配置
>
> ```
> 
>     "nav": [  //如下代码中，每个{...}即为一个导航块
> 
>       {
> 
>         "text": "Home",      //导航文本
> 
>         "link": "/",          //路由地址
> 
>         "icon": "reco-home"  //图标
> 
>       },
> 
>       {
> 
>         "text": "TimeLine",
> 
>         "link": "/timeline/",
> 
>         "icon": "reco-date"
> 
>       },
> 
>       {
> 
>         "text": "Docs",
> 
>         "icon": "reco-message",
> 
>         "items": [
> 
>           {
> 
>             "text": "vuepress-reco",
> 
>             "link": "/docs/theme-reco/"
> 
>           }
> 
>         ]
> 
>       },
> 
>       {
> 
>         "text": "Contact",
> 
>         "icon": "reco-message",
> 
>         "items": [
> 
>           {
> 
>             "text": "GitHub",
> 
>             "link": "https://github.com/recoluan",
> 
>             "icon": "reco-github"
> 
>           }
> 
>         ]
> 
>       }
> 
>     ],
> 
> 
> ```
>
> 
>
> 其中：
>
> - 导航文本为导航按钮所展示的文字信息
>
> - 路由地址即为跳转路径，根目录`/`对应您项目的根目录，在项目打包时会将对应目录下的`README.md`文件生成为`index.html`，例如您想将链接指向的`/docs/myDocument/README.md`,则将`link`内容改为``/docs/myDocument`,便可访问到您的文档,因为默认会访问README.md/index.html,如果/docs/myDocument目录下有多个md文件,需要配置侧边栏sidebar(如下),才会显示在侧边栏,否则只会显示/docs/myDocument/README.md文件的内容(ps: 每个目录的根目录下的README.md文件必须存在,否则访问会404),导航可以通过items嵌套2级3级导航
>
>   ```
>    "nav": [
>         {
>           "text": "Home",
>           "link": "/",
>           "icon": "reco-home"
>         },
>         {
>           "text": "TimeLine",
>           "link": "/timeline/",
>           "icon": "reco-date"
>         },
>         {
>           "text": "Docs",
>           "icon": "reco-message",
>           "items": [
>             {
>               "text": "vuepress-reco",
>               "link": "/docs/theme-reco/"
>             },
>             {
>               "text": "vue",
>               "link": "/docs/vue/"
>             },
>             {
>               "text": "java",
>               "link": "/docs/java/"
>             }
>           ]
>         },
>         {
>           "text": "Contact",
>           "icon": "reco-message",
>           "items": [
>             {
>               "text": "GitHub",
>               "link": "https://github.com/recoluan",
>               "icon": "reco-github"
>             }
>           ]
>         }
>       ],
>       "sidebar": {
>         "/docs/theme-reco/": [
>           "",
>           "theme",
>           "plugin",
>           "api"
>         ],
>         "/docs/java/":[
>             "rabbitmq"
>         ],
>         "/docs/vue/":[
>           "vuepress"
>         ]
>       },
>   ```
>
>   
>
> - 图标则为导航文本左边显示的图标，可以在[reco图标库](https://links.jianshu.com/go?to=https%3A%2F%2Fvuepress-theme-reco.recoluan.com%2Fviews%2F1.x%2FconfigJs.html%23%E5%9B%BE%E6%A0%87)中寻找您需要的图标，也可以不要图标

## 3.7 文档写作

> ### [Front Matter](https://links.jianshu.com/go?to=https%3A%2F%2Fvuepress-theme-reco.recoluan.com%2Fviews%2F1.x%2FfrontMatter.html)
>
> 在markdown文档的顶部插入一段yaml配置代码
>
> 一个完整的 `Front Matter` 案例：

```

---

title: 烤鸭的做法

date: 2019-08-08

sidebar: 'auto'

categories:

- 烹饪

- 爱好

tags:

- 烤

- 鸭子

keys:

- '123456'

publish: false

---

```

> 常用变量说明:
>
> `title` :文章标题，放弃通过一级目录定义标题的方式，改在 `Front Matter` 中定义。
>
> `date` :文章创建日期，格式 `2019-08-08` 或 `2019-08-08 08:08:08`。
>
> `sidebar`:是否开启侧边栏。
>
> `categories` :所属分类。
>
> `tags` :所属标签。
>
> `keys`: 所属标签。
>
> `publish` :文章是否发布

## 3.8 摘要

> 在markdown代码中，您将看到注释，注释前面的代码将显示在列表页面上的文章摘要中。

```

---

title: Vuepress使用指南(reco)

date: 2020-08-16

sidebar: 'auto'

categories:

- 工具

tags:

- vue

publish: true

---

::: tip

Vuepress是Vue作者尤雨溪开发的文档工具，本文采用Vuepress的reco主题进行相关配置说明

:::

<!-- more -->

### markdown正文

```

> 效果:
>
> ![截屏2022-01-26 下午3.00.02](https://tva1.sinaimg.cn/large/008i3skNgy1gyr3283iv1j311k0acq3k.jpg)
>
> 

## 3.9  把博客部署到github page上

### 3.9.1 github page

> 在个人github上,先创建好自己的github page
>
> ![截屏2022-01-26 下午3.09.06](https://tva1.sinaimg.cn/large/008i3skNgy1gyr3ci4k76j31g70u0dkd.jpg)

> 这里有个小坑, 创建github page的时候,仓库名称建议和你的github账户保持一致,这样发布完成后,你就可以直接访问账户名.github.io访问你的博客了,如果仓库名和账户名不一致的情况下,会导致访问的时候,很多静态资源文件(js,css)会访问404,因为项目的根路径不一样,此时需要到.vuepress/config.js` 中设置正确的 `base
>
> 例如你的仓库是https://<USERNAME>.github.io/, 那么不需要配置base,默认就是“/”,
>
> 如果你的仓库是https://<USERNAME>.github.io/<REPO>/,那么就要配置"base": "/<REPO>/",

### 3.9.2  设置base

> 在 `docs/.vuepress/config.js` 中设置正确的 `base`。
>
> 如果你打算发布到 `https://<USERNAME>.github.io/`，则可以省略这一步，因为 `base` 默认即是 `"/"`。
>
> 如果你打算发布到 `https://<USERNAME>.github.io/<REPO>/`（也就是说你的仓库在 `https://github.com/<USERNAME>/<REPO>`），则将 `base` 设置为 `"/<REPO>/"`。

### 3.9.3 创建发布脚本deploy.sh

> 在你的项目中，创建一个如下的 `deploy.sh` 文件（请自行判断去掉高亮行的注释）:

```
#!/usr/bin/env sh

# 确保脚本抛出遇到的错误
set -e

# 生成静态文件
npm run docs:build

# 进入生成的文件夹
cd docs/.vuepress/dist

# 如果是发布到自定义域名
# echo 'www.example.com' > CNAME

git init
git add -A
git commit -m 'deploy'

# 如果发布到 https://<USERNAME>.github.io (git的地址直接到github上拷贝即可)
# git push -f git@github.com:<USERNAME>/<USERNAME>.github.io.git master

# 如果发布到 https://<USERNAME>.github.io/<REPO>
# git push -f git@github.com:<USERNAME>/<REPO>.git master:gh-pages

cd -
```

### 3.9.4 发布完成 访问验证

>运行上面的发布脚本deploy.sh后,就会把项目打包并推送到github page上,直接访问github page的地址即可访问到博客首页了,访问地址可以直接在github page上查看
>
>![截屏2022-01-26 下午3.28.17](https://tva1.sinaimg.cn/large/008i3skNgy1gyr3vmhg6lj31r80u0q7t.jpg)
>
>访问成功如下:
>
>![截屏2022-01-26 下午3.29.23](https://tva1.sinaimg.cn/large/008i3skNgy1gyr3wqcn4oj31bp0u0jtb.jpg)
>
>

