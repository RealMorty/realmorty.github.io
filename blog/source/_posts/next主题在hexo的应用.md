---
title: next主题在hexo的应用
date: 2022-09-23 09:45:47
tags:
  - next
  - hexo
categories:
  - 运维
  - hexo
description: next主题在hexo的部署与初步改造。
---

## Next 主题插件

### Mermaid

[Mermaid 在线生成网站](https://mermaid-js.github.io/mermaid-live-editor/)

{% mermaid %}
graph TD
A[Christmas] -->|Get money| B(Go shopping)
B --> C{Let me think}
C -->|One| D[Laptop]
C -->|Two| E[iPhone]
C -->|Three| F[fa:fa-car Car]
{% endmermaid %}

### PDF

{% pdf https://www.orimi.com/pdf-test.pdf %}

---

### 群组图片

```
{% grouppicture [number]-[layout] %}
{% endgrouppicture %}
```

或者

```
{% gp [number]-[layout] %}
{% endgp %}
```

- `[number]`: 图片总数
- `[layout]`: 布局

例子：

```
{% grouppicture 3-3 %}
![](/images/next.svg)
![](/images/next.svg)
![](/images/next.svg)
{% endgrouppicture %}
```

{% grouppicture 3-3 %}
![](/images/next.svg)
![](/images/next.svg)
![](/images/next.svg)
{% endgrouppicture %}

### 按钮

```
{% button url, text, icon [class], [title] %}
```

或者

```
{% btn url, text, icon [class], [title] %}
```

示例:

单链接：

```jinja
<div class="text-center">{% btn https://github.com, GitHub, fab fa-github fa-fw fa-lg, GitHub %}</div>
```

<div class="text-center">{% btn https://github.com, GitHub, fab fa-github fa-fw fa-lg, GitHub %}</div>

前后链接：

```jinja
<div class="text-center">{% btn #, Previous Chapter, arrow-left fa-fw fa-lg, Previous Chapter (Full Image) %} {% btn #, Next Chapter, arrow-right fa-fw fa-lg, Next Chapter (Label) %}</div>
```

<div class="text-center">{% btn /docs/tag-plugins/full-image, Previous Chapter, arrow-left fa-fw fa-lg, Previous Chapter (Full Image) %} {% btn /docs/tag-plugins/label, Next Chapter, arrow-right fa-fw fa-lg, Next Chapter (Label) %}</div>

其他按钮：

{% btn #,, fab fa-edge %} `{% btn #,, fab fa-edge %}`

{% btn #,, times %} `{% btn #,, times %}`

{% btn #,, circle-notch %} `{% btn #,, circle-notch %}`

{% btn #,, italic %} `{% btn #,, italic %}`

{% btn #,, fab fa-scribd %} `{% btn #,, fab fa-scribd %}`

{% btn #,, fab fa-google %} `{% btn #,, fab fa-google %}`

{% btn #,, fab fa-chrome %} `{% btn #,, fab fa-chrome %}`

{% btn #,, fab fa-opera %} `{% btn #,, fab fa-opera %}`

{% btn #,, fab fa-opera %} `{% btn #,, gem fa-rotate-270 %}`

## 添加评论功能

依次尝试了 next 默认提供的几个评论插件：

- disqus: 国内被墙，不然做的最好的一个，next 官方采用本方案
- changyan: 追评 UI 个人觉得不够简洁
- livere: UI 不习惯
- gitalk: 国内网络环境不好，Network Error
- utterances: 很棒，缺点是不能追评

暂时先用着 utterances。

这里要吐槽一下 gitalk，如果你和我一样域名类似于`realmorty.top`，那么在创建 GitHub Application 时`Authorization callback URL`
一定要是`https://realmorty.top`，其他的比如`https://www.realmorty.top`会报错：回调网址与 GitHub 默认网址不符。另外 Homepage URL
和 Authorization callback URL 我写的是一样的。

## 添加新的文件夹（page）

初始化的 hexo 没有 categories 功能，需要新建该分类。

```shell
hexo new page categories
```

新建之后会自动生成`\source\categories\index.md`，在 front-matter 中加入`type: categories`

```
---
title: categories
date: 2022-09-23 09:38:47
type: "categories"
---
```

后续添加新文章时，在 front-matter 中添加 categories 属性，即可收纳到该分类下。

```
categories:
    - folder
    - folder's child
    - folder's child's child
    - ...
```

例如这篇文章的 front-matter：

```
title: next主题在hexo的应用
date: 2022-09-23 09:45:47
tags:
    - next
    - hexo
categories:
    - 运维
    - hexo
```

tags 功能同理：

{% tabs adding-tags-page %}

<!-- tab 新建页面 → -->

```
hexo new page tags
```

<!-- endtab -->
<!-- tab 添加属性 → -->

在`tags/index.md`的 front-matter 中添加：

```
type: tags
```

<!-- endtab -->
<!-- tab 文章中添加标签 -->

在新建文章的 front-matter 中添加：

```
tags:
- tag1
- tag2
```

或者

```
tags: [tag1, tag2]
```

<!-- endtab -->

{% endtabs %}
