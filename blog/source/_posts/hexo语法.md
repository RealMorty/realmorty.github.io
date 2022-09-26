---
title: hexo语法
categories:
  - 运维
  - hexo
date: 2022-09-23 10:38:05
tags:
description: hexo语法总结，主要是一些小插件和流程块的使用。
---

## 日常写博客的 bash 流程

1. 创建博客
   - hexo new post "file_name"
   -
2. 推送博文
   - hexo clean: 清理/public 文件夹
   - hexo g -d: 重新生成/public 文件夹并推送到 GitHub，博客网站依靠/public 的内容对外展示
   - hexo s: 本地启动服务器，用于本地测试

## 用于同步博客源码的一般 git 流程

1. 项目刚开始建立时

   - `git init`: 在本地文件夹创建仓库
   - `git clone <repo>`: 从 GitHub 拷贝项目到本地，一般可以从 GitHub 直接 copy 命令过来

2. 项目更新代码时

   - `git checkout -b <branch_name> origin/<remote_branch>`: 拉取远程某特定分支到本地，并新建分支，切换到该分支
   - `git fetch origin` + `git merge origin/v0.1.20220925`: 获取远程更新的数据并同步 merge 到本地，效果等同于`git pull`
   - `git commit .`: 提交新修改的文件到本地暂存
   - `git push origin v0.1.20220925`: 将本地暂存文件 push 到远程仓库

3. 一些 git info 的查看命令
   - `git config --list`: 查看 git 配置信息。
   - `git status`: 查看仓库当前状态，显示有变更的文件
   - `git log`: 查看历史提交信息
   - `git blame <file>`: 查看某个文件的历史修改信息
   - `git diff`: 比较暂存区文件和工作区文件的不同

## 实用的 hexo md 渲染组件

### 首页文章预览

在文章中需要截断的地方插入以下代码即可：

```
<!-- more -->
```

<!-- more -->

### 提示小插件

```
{% note default %}default{% endnote %}
{% note primary %}primary{% endnote %}
{% note success %}success{% endnote %}
{% note info %}info{% endnote %}
{% note warning %}warning{% endnote %}
{% note danger %}danger{% endnote %}
```

{% note default %}default{% endnote %}
{% note primary %}primary{% endnote %}
{% note success %}success{% endnote %}
{% note info %}info{% endnote %}
{% note warning %}warning{% endnote %}
{% note danger %}danger{% endnote %}

### 图片

```
1. {% img [class names] /path/to/image [width] [height] '"title text" "alt text"' %}
2. !()[]
```

{% img [class names] /images/屏幕截图102742.jpg %}
安装以下插件解决图片路径问题，需要建立文件夹：`source\images`  
`npm i hexo-easy-images -s`

### 代码块流程

````
   {% tabs adding-tags-page %}
    <!-- tab 新建页面 → -->
    ``` hexo new page tags```
    <!-- endtab -->
    <!-- tab 添加属性 -->
    在`tags/index.md`的front-matter中添加：
    ``` type: tags  ```
    <!-- endtab -->
    {% endtabs %}
````

{% note success %}
实现效果：
![代码块流程图](/images/屏幕截图102742.jpg)
{% endnote %}

---

## md 语法测试

$$e^2$$

$$
\begin{equation} \label{eq1}
e = m c ^ 2
\end{equation}
$$

The famous matter-energy equation $\eqref{eq1}$ proposed by Einstein...

$$
\begin{equation} \label{eq2}
\begin{aligned}
a &= b + c\\
  &= d + e + f \\
  &= h + i
\end{aligned}
\end{equation}
$$

Equation $\eqref{eq2}$ is a multi-line equation.
