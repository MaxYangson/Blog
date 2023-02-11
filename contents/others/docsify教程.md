# docsify搭建个人文档网站

## 快速开始

需要软件环境：npm、docsify

1.0、安装npm环境，详见教程——软件安装配置专栏 

1.1、全局安装docsify-cli工具

```bash
npm i docsify-cli -g  # 安装docsify-cli
docsify -v  # 测试是否安装成功/查看版本
```

1.2、初始化文档结构

先创建一个本地文件夹docs，然后执行项目初始化命令

```bash
docsify init ./docs
```

会生成如下目录

```
-| docs
     -| .nojekyll  用于阻止Github Pages 会忽略掉下滑线开头的文件
     -| index.html 入口文件
     -| README.md  作为主页内容渲染
```

1.3、启动项目

```bash
docsify serve docs
```

默认浏览器访问http://localhost:3000，就可以本地预览

1. README.md文件

2. 预览效果：

## 常用配置

docsify项目配置主要修改相关md文件和index.html文件

`README.md`在您的 docs 文件夹中将被视为您网站的内容主页

1、定制导航栏和侧边栏

修改index.html文件中的script配置

```js
  <script>
    window.$docsify = {
      name: '学习笔记',    // 显示在侧边栏中的网站名称。
      repo: '',         // 仓库地址
      loadNavbar: true,  // 开启导航栏
      loadSidebar: true,  // 开启侧边栏
      maxLevel: 2,      // 最大支持渲染目录层级
      subMaxLevel: 4,   // 生成目录的最大层级
      mergeNvabar: true
    }
  </script>
```

在index.html文件的同级目录下，创建**_sidebar.md**文件来配置侧边栏内容，内容采用列表形式展示

```md
* DOCSIFY学习笔记
  * [一、初始化项目](docsifyUsage/docsifyUsageChapter1.md)
  * [二、侧边栏配置](docsifyUsage//docsifyUsageChapter2.md)
```

在index.html文件的同级目录下，创建**_navbar.md**文件来配置顶部导航栏，内容也采用列表形式展示

```md
* 项目地址
  * [GitHub地址](https://github.com/arenxiaolanz/docsify_study)
  * [Gitee地址](https://gitee.com/ren-nino/docsify_study)
* 更多
  * [博客主页](http://blog.renorchid.xyz/)
```

查看效果

2、定制封面页
在入口文件 index.html 中添加封面页的配置

```js
<script>
  window.$docsify = {
    coverpage: true   // 开启封面页
  }
</script>
```

同级目录下创建 _coverpage.md 文件配置封面页

```md
<!-- _coverpage.md -->

![logo](./images/icon.svg)

# 我的docsify学习笔记 <small>1.0.0</small>

> 业精于勤荒于嬉，行成于思毁于随.

- 简单，轻量级
- 不用构建静态htnl文件
- 多种主题

[GitHub](https://github.com/docsifyjs/docsify/)
[Get Started](#docsifyUsage/docsifyUsageChapter1)
```

查看封面效果

3、自动顶部

选择目录其他选项时会自动滚动到屏幕顶部。

```javascript
window.$docsify = {
  auto2top: true,
};
```

3、添加全文搜索

在入口文件中添加全文搜索的配置

```js
  <script>
    window.$docsify = {
      search: {
        maxAge: 86400000, // 过期时间，单位毫秒，默认一天
        placeholder: 'Type to search',
        noData: 'No Results!',
        // 搜索标题的最大层级, 1 - 6
        depth: 4,
        hideOtherSidebarContent: false, // 是否隐藏其他侧边栏内容
      }
    }
  </script>

 <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```

4、添加代码高亮

在入口文件index.html中添加下列代码

```js
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-bash.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/prismjs@1/components/prism-php.min.js"></script>
```

5、添加一键拷贝代码

1. 在入口文件中添加下列代码
   
   ```js
   <script src="//cdn.jsdelivr.net/npm/docsify-copy-code/dist/docsify-copy-code.min.js"></script>
   ```

6、添加页面内目录插件——[docsify-plugin-toc插件](https://github.com/justintien/docsify-plugin-toc)



个人配置github项目地址：

相关较好的开源项目推荐：

## 在GitHub/Gitee上部署文档网站

1、提交代码到GitHub

2、GitHub Pages 部署

3、部署成功·

访问链接：https://arenxiaolanz.github.io/docsify_study/

4.tips，上传更新

```git
git init
git remote remove origin
git remote add origin git@github.com:arenxiaolanz/docsify_study.git
git add .
git commit -m "completed"
git push -u origin master
```

## 安装配置过程中相关问题

## 参考资料

[docsify官方教程](https://docsify.js.org/#/)

[开源低成本在线免费文档-docsify-plus模板 (gitee.io)](https://librarycodes.gitee.io/docsify-plus/#/)

[(33条消息) 工具--docsify详解_李宥小哥的博客-CSDN博客_docsify](https://blog.csdn.net/liyou123456789/article/details/124504727)

[docsify 常用插件地址收藏 - 简书 (jianshu.com)](https://www.jianshu.com/p/a093f58321b5)

[使用docsify生成简易的文档网站 (enjoytoday.cn)](https://www.enjoytoday.cn/2021/11/25/%E4%BD%BF%E7%94%A8docsify%E7%94%9F%E6%88%90%E7%AE%80%E6%98%93%E7%9A%84%E6%96%87%E6%A1%A3%E7%BD%91%E7%AB%99/)

[(33条消息) 【docsify基本使用】_docsify使用_呐呐呐呐。的博客-CSDN博客](https://blog.csdn.net/m0_56542349/article/details/125451229)

[(33条消息) Docsify+github/gitee搭建个人博客_gitee docsify博客模板_love~"的博客-CSDN博客](https://blog.csdn.net/m0_53538111/article/details/124557800)

<p style="text-align:right">Lastest Updated: {docsify-updated}</p>