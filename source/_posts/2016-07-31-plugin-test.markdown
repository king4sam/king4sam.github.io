---
layout: post
title: "plugin test"
date: 2016-08-1 14:05:33 +0800
comments: true
tags:
- octopress
- plugin

---
<!--more-->

## Codeblock

### Syntax
{% raw %}
    {% codeblock [lang:language] [title] [url] [link text] %}
    code snippet
    {% endcodeblock %}
{% endraw %}

### 效果
``` ruby Discover if a number is prime http://www.noulakaz.net/weblog/2007/03/18/a-regular-expression-to-check-for-prime-numbers/ Source Article
class Fixnum
  def prime?
    ('1' * self) !~ /^1?$|^(11+?)\1+$/
  end
end
```

## Youtube 嵌入
<iframe width="560" height="315" src="https://www.youtube.com/embed/YCuk1kdQuNo" frameborder="0" allowfullscreen></iframe>

##Image Tag

### Syntax
{% raw %}
    {% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
{% endraw %}

### 效果

{% img [class names] http://www.marieclaire.com.hk/sites/default/files/editors/user11/image6_28.jpeg %}

---

後記

- install new theme oct2
- excerpt_link 改為中文
- include Mathjax
- change markdown parser