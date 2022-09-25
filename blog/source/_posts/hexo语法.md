---
title: hexo语法
categories:
  - 运维
date: 2022-09-23 10:38:05
tags:
---
## 实用的hexo md渲染组件
#### 提示小插件
```markdown
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

#### 图片
```markdown
1. {% img [class names] /path/to/image [width] [height] '"title text" "alt text"' %}
2. !()[]
```
{% img [class names] /images/屏幕截图102742.jpg [80px] [20px] '"title text" "alt text"' %}
安装了插件，可以解决图片路径问题，需要建立文件夹：`source\images`  
`npm i hexo-easy-images -s`
 
#### 代码块流程

```
   {% tabs adding-tags-page %}
    <!-- tab 新建页面 → -->
    ``` hexo new page tags```
    <!-- endtab -->
    <!-- tab 添加属性 -->
    在`tags/index.md`的front-matter中添加：
    ``` type: tags  ```
    <!-- endtab -->
    {% endtabs %}
```

{% note success %}
实现效果：
![代码块流程图](/images/屏幕截图102742.jpg)
{% endnote %}

## md语法测试
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

