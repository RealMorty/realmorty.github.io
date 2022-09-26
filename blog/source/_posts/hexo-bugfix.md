---
title: hexo bugfix
tags:
  - bugfix
categories:
  - 运维
  - hexo
description: hexo遇到的bug修复
date: 2022-09-26 20:17:09
---

## `title: '[object Object]': null`

同样的还有`date: '[object Object]': null`，排查原因是在用 VS code 的 prettier 插件格式化 md 文件时（保存文件时自动格式化，因此不易察觉），会将 md 头文件 front-matter 中的 {% raw %} `{{ }}` {% endraw %}格式化为 { { } }，导致变量无法自动填充。
例如，我的 scaffolds/post.md（用于 hexo 生成模板文件）的 front-matter 是：

```text
---
title: {{ title }}
date: {{ date }}
tags:
  - null
categories:
  - null
description: ..
---
```

当我修改了 post.md 后保存文件时，prettier 自动格式化，头文件变成了：

```text
---
title: { { title } }
date: { { date } }
tags:
  - null
categories:
  - null
description: ..
---
```

{% note warning %}
yaml 只会识别{% raw %} `{{ }}` {% endraw %}，而不会识别`{ { } }`，因此初始化为 null。
{% endnote %}

解决方案是在开头添加`# prettier-ignore`，表示不加入格式化。也可以新建`.prettierignore`文件排除 scaffolds 文件夹，具体方案参考：<https://prettier.io/docs/en/ignore.html>

改进后的 front-matter:

```text
---
# prettier-ignore
title: {{ title }}
date: {{ date }}
tags:
  - null
categories:
  - null
description: ..
---
```

{% note warning %}
就算是一般的文件，在写代码块时，如果标注代码为 YAML 类型，prettier 也可能将代码块中的内容格式化，造成代码块无法复现，因此尽量标注代码为 text。
{% endnote %}

新的问题来了，hexo 采用 Nunjucks 实现 md 渲染，然而 Nunjucks 遇到 {% raw %} `{{ }}` {% endraw %}会报错导致部署失败，因此需要改成：

```text
 {% raw %} `{{ }}` {% endraw %}
```

无语死 😶
