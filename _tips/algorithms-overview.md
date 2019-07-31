---
title: "算法"
permalink: /tips/algorithms-overview
last_modified_at: 2019-07-23T09:51:09+08:00
toc: true
---

算法广义上是指一种确定的，有穷的和可执行的，用来解决问题的指令。我们这里要讨论的算法的范围定义相对较窄，主要指的是能够解决某个问题的一个程序。任何可以解决问题的程序都可以称之为算法，但正如数学里我们有各种定理一样，某些经典的算法可以为解决其它问题提供良好的基础。这篇文章的主要目的即是将我收集到的各种经典算法罗列出来，方便学习和参考。

## 排序

{% for post in site.tags["algorithm-sorting"] reversed %}

### [{{ post.title }}]({{ post.url }})
{{ post.excerpt }}

{% endfor %}

## 搜索

{% for post in site.tags["algorithm-searching"] reversed %}

### [{{ post.title }}]({{ post.url }})
{{ post.excerpt }}

{% endfor %}

## 图论

{% for post in site.tags["algorithm-graphs"] reversed %}

### [{{ post.title }}]({{ post.url }})
{{ post.excerpt }}

{% endfor %}

## 字符串

{% for post in site.tags["algorithm-strings"] reversed %}

### [{{ post.title }}]({{ post.url }})
{{ post.excerpt }}

{% endfor %}