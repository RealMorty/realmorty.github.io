---
title: next主题在hexo的应用
date: 2022-09-23 09:45:47
tags: 
    - next
    - hexo
categories:
    - 运维
    - hexo
---

## Next主题插件

### PDF

{% pdf https://www.orimi.com/pdf-test.pdf %}

### Mermaid

(Mermaid在线生成网站)[https://mermaid-js.github.io/mermaid-live-editor/]

{% mermaid %}
graph TD
A[Christmas] -->|Get money| B(Go shopping)
B --> C{Let me think}
C -->|One| D[Laptop]
C -->|Two| E[iPhone]
C -->|Three| F[fa:fa-car Car]
{% endmermaid %}

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

* `[number]`: 图片总数
* `[layout]`: 布局

例子：
```markdown
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
<div class="text-center">{% btn https://github.com, GitHub, fab fa-github fa-fw fa-lg, GitHub %}</div>

前后链接：

<div class="text-center">{% btn #, Previous Chapter, arrow-left fa-fw fa-lg, Previous Chapter (Full Image) %} {% btn #, Next Chapter, arrow-right fa-fw fa-lg, Next Chapter (Label) %}</div></div>

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
依次尝试了next默认提供的几个评论插件：

* disqus: 国内被墙，不然做的最好的一个，next官方采用本方案
* changyan:  追评UI个人觉得不够简洁
* livere: UI不习惯
* gitalk: 国内网络环境不好，Network Error
* utterances: 很棒，缺点是不能追评

暂时先用着utterances。

这里要吐槽一下gitalk，如果你和我一样域名类似于`realmorty.top`，那么在创建GitHub Application时`Authorization callback URL`
一定要是`https://realmorty.top`，其他的比如`https://www.realmorty.top`会报错：回调网址与GitHub默认网址不符。另外Homepage URL
和Authorization callback URL我写的是一样的。

## 添加新的文件夹（page）
初始化的hexo没有categories功能，需要新建该分类。  
```bash
hexo new page categories
```
新建之后会自动生成`\source\categories\index.md`，在front-matter中加入`type: categories`  
```markdown
---
title: categories
date: 2022-09-23 09:38:47
type: "categories"
---
```
后续添加新文章时，在front-matter中添加categories属性，即可收纳到该分类下。
```markdown
categories:
    - folder
    - folder's child
    - folder's child's child
    - ...
```
例如这篇文章的front-matter：
```markdown
title: next主题在hexo的应用
date: 2022-09-23 09:45:47
tags: 
    - next
    - hexo
categories:
    - 运维
    - hexo
```
tags功能同理：
{% tabs adding-tags-page %} 
<!-- tab 新建页面 → -->
```markdown
hexo new page tags
```
<!-- endtab -->
<!-- tab 添加属性 → -->
在`tags/index.md`的front-matter中添加：  
```markdown
type: tags   
```
<!-- endtab -->
<!-- tab 文章中添加标签 -->
在新建文章的front-matter中添加：
```markdown
tags:
- tag1
- tag2
```
或者
```markdown
tags: [tag1, tag2]
```
<!-- endtab -->
{% endtabs %}



    
