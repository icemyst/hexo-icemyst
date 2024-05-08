---
title: hexo+butterfly 主题标签使用
tags:
  - hexo
cover: 'https://gcore.jsdelivr.net/npm/ushio-api-img-moe@5.0.81/img_819_1920x1080_1200_null_normal.jpg' #'https://tva3.sinaimg.cn/large/a15b4afegy1fmvj0m0n6mj21hc0u0dnf.jpg'
categories: 魔改教程
description: 使用Tag Plugins标签，记录它的使用过程。
abbrlink: 3d94
date: 2022-12-24 20:18:44
comments:
---

{% note blue 'fas fa-bullhorn' flat %} 这里记录我习惯用的外挂标签，同时也是为了让自己写文章更美化，也是为了记录我使用插件，为了后续可以使用，这里记录它的插件安装过程和使用的渲染。{% endnote %}


### 原教程：

{% link 糖果屋,店长原教程 ,https://akilar.top/posts/615e2dec/ %}

## 安装插件

1. 安装插件,在博客根目录[Blogroot]下打开终端，运行以下指令：

    ```bash
    npm install hexo-butterfly-tag-plugins-plus --save
    ```

    考虑到hexo自带的markdown渲染插件`hexo-renderer-marked`与外挂标签语法的兼容性较差，建议您将其替换成[hexo-renderer-kramed](https://www.npmjs.com/package/hexo-renderer-kramed)。

    ```bash
    npm uninstall hexo-renderer-marked --save
    npm install hexo-renderer-kramed --save
    ```

2. 添加配置信息，以下为写法示例

    在站点配置文件`_config.yml`或者主题配置文件`_config.butterfly.yml中`添加

    ```yaml
    # tag-plugins-plus
    # see https://akilar.top/posts/615e2dec/
    tag_plugins:
      enable: true # 开关
      priority: 5 #过滤器优先权
      issues: false #issues标签依赖注入开关
      link:
        placeholder: /img/link.png #link_card标签默认的图标图片
      CDN:
        anima: https://npm.elemecdn.com/hexo-butterfly-tag-plugins-plus@latest/lib/assets/font-awesome-animation.min.css #动画标签  anima的依赖
        jquery: https://npm.elemecdn.com/jquery@latest/dist/jquery.min.js #issues标签依赖
        issues: https://npm.elemecdn.com/hexo-butterfly-tag-plugins-plus@latest/lib/assets/issues.js #issues标签依赖
        iconfont: //at.alicdn.com/t/font_2032782_8d5kxvn09md.js #参看https://akilar.top/posts/d2ebecef/
        carousel: https://npm.elemecdn.com/hexo-butterfly-tag-plugins-plus@latest/lib/assets/carousel-touch.js
        tag_plugins_css: https://npm.elemecdn.com/hexo-butterfly-tag-plugins-plus@latest/lib/tag_plugins.css
    ```

3. 参数释义

| 参数                | 备选值/类型                        | 释义                                                         |
| :------------------ | :--------------------------------- | :----------------------------------------------------------- |
| enable              | true/false                         | 【必选】控制开关                                             |
| priority            | number                             | 【可选】过滤器优先级，数值越小，执行越早，默认为10，选填     |
| issues              | true/false                         | 【可选】issues标签控制开关，默认为false                      |
| link.placeholder    | 【必选】link卡片外挂标签的默认图标 |                                                              |
| CDN.anima           | URL                                | 【可选】动画标签anima的依赖                                  |
| CDN.jquery          | URL                                | 【可选】issues标签依赖                                       |
| CDN.issues          | URL                                | 【可选】issues标签依赖                                       |
| CDN.iconfont        | URL                                | 【可选】iconfont标签symbol样式引入，如果不想引入，则设为false |
| CDN.carousel        | URL                                | 【可选】carousel旋转相册标签鼠标拖动依赖，如果不想引入则设为false |
| CDN.tag_plugins_css | URL                                | 【可选】外挂标签样式的CSS依赖，为避免CDN缓存延迟，建议将@latest改为具体版本号 |

## 行内文本样式 text

{% tabs test4 %}
<!-- tab 标签语法-->
```markdown
{% u 文本内容 %}
{% emp 文本内容 %}
{% wavy 文本内容 %}
{% del 文本内容 %}
{% kbd 文本内容 %}
{% psw 文本内容 %}
```
<!-- endtab -->

<!-- tab 样式预览 -->
1. 带 {% u 下划线 %} 的文本
2. 带 {% emp 着重号 %} 的文本
3. 带 {% wavy 波浪线 %} 的文本
4. 带 {% del 删除线 %} 的文本
5. 键盘样式的文本 {% kbd command %} + {% kbd D %}
6. 密码样式的文本：{% psw 这里没有验证码 %}
<!-- endtab -->

<!-- tab 示例源码-->
```markdown
1. 带 {% u 下划线 %} 的文本
2. 带 {% emp 着重号 %} 的文本
3. 带 {% wavy 波浪线 %} 的文本
4. 带 {% del 删除线 %} 的文本
5. 键盘样式的文本 {% kbd command %} + {% kbd D %}
6. 密码样式的文本：{% psw 这里没有验证码 %}
```
<!-- endtab -->
{% endtabs %}

## 行内文本

{% tabs test4 %}
<!-- tab 标签语法-->
```markdown
{% span 样式参数(参数以空格划分), 文本内容 %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. 字体: logo, code
2. 颜色:{% span red, red %}、{% span yellow, yellow %}、{% span green, green %}、{% span cyan, cyan %}、{% span blue, blue %}、{% span gray, gray %}。
3. 大小: small, h4, h3, h2, h1, large, huge, ultra
4. 对齐方向: left, center, right
<!-- endtab -->

<!-- tab 样式预览 -->
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% span center logo large, Volantis %}
{% span center small, A Wonderful Theme for Hexo %}
<!-- endtab -->

<!-- tab 示例源码-->
```markdown
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% span center logo large, Volantis %}
{% span center small, A Wonderful Theme for Hexo %}
```
<!-- endtab -->
{% endtabs %}

## 段落文本 p

{% tabs test4 %}
<!-- tab 标签语法-->
```markdown
{% p 样式参数(参数以空格划分), 文本内容 %}
```
<!-- endtab -->

<!-- tab 配置参数 -->
1. 字体: logo, code
2. 颜色: % p red, red %}、{% p yellow, yellow %}、{% p green, green %}、{% p cyan, cyan %}、{% p blue, blue %}、{% p gray, gray %}。
3. 大小: small, h4, h3, h2, h1, large, huge, ultra
4. 对齐方向: left, center, right
 <!-- endtab -->

<!-- tab 样式预览 -->
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% p red, 红色 %}、{% p yellow, 黄色 %}、{% p green, 绿色 %}、{% p cyan, 青色 %}、{% p blue, 蓝色 %}、{% p gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% p center logo large, Volantis %}
{% p center small, A Wonderful Theme for Hexo %}
<!-- endtab -->

<!-- tab 示例源码-->
```markdown
- 彩色文字
在一段话中方便插入各种颜色的标签，包括：{% span red, 红色 %}、{% span yellow, 黄色 %}、{% span green, 绿色 %}、{% span cyan, 青色 %}、{% span blue, 蓝色 %}、{% span gray, 灰色 %}。
- 超大号文字
文档「开始」页面中的标题部分就是超大号文字。
{% span center logo large, Volantis %}
{% span center small, A Wonderful Theme for Hexo %}
```
<!-- endtab -->
{% endtabs %}

## 引用 note

{% tabs test4 %}

{% note waring  flat %} 以下是`butterfly`主题的`note`写法{% endnote %}

<!-- tab 标签语法-->
```yml
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  border_radius: 3
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```
<!-- endtab -->

<!-- tab 语法样式 -->
{% folding 方法一 %}

```markdown
{% note [class] [no-icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

{% endfolding %}

{% folding yellow, 方法二 %}

```markdown
{% note [color] [icon] [style] %}
Any content (support inline tags too.io).
{% endnote %}
```

{% endfolding %}
<!-- endtab -->

<!-- tab 配置参数 -->

{% folding 方法一 %}

| 参数    | 用法                                                         |
| :------ | :----------------------------------------------------------- |
| class   | 【可选】标识，不同的标识有不同的配色 （ default / primary / success / info / warning / danger ） |
| no-icon | 【可选】不显示 icon                                          |
| style   | 【可选】可以覆盖配置中的 style （simple/modern/flat/disabled） |

{% endfolding %}

{% folding yellow, 方法二 %}

| 参数    | 用法                                                         |
| :------ | :----------------------------------------------------------- |
| class   | 【可选】标识，不同的标识有不同的配色 （ default / blue / pink / red / purple / orange / green ） |
| no-icon | 【可选】可配置自定义 icon (只支持 fontawesome 图标, 也可以配置 no-icon ) |
| style   | 【可选】可以覆盖配置中的 style （simple/modern/flat/disabled） |

{% endfolding %}

 <!-- endtab -->

<!-- tab 样式预览 -->

{% folding 方法一 %}

1. `simple`样式

  {% note simple %}默认 提示块标签{% endnote %}

  {% note default simple %}default 提示块标签{% endnote %}

  {% note primary simple %}primary 提示块标签{% endnote %}

  {% note success simple %}success 提示块标签{% endnote %}

  {% note info simple %}info 提示块标签{% endnote %}

  {% note warning simple %}warning 提示块标签{% endnote %}

  {% note danger simple %}danger 提示块标签{% endnote %}

2. `modern`样式

  {% note modern %}默认 提示块标签{% endnote %}

  {% note default modern %}default 提示块标签{% endnote %}

  {% note primary modern %}primary 提示块标签{% endnote %}

  {% note success modern %}success 提示块标签{% endnote %}

  {% note info modern %}info 提示块标签{% endnote %}

  {% note warning modern %}warning 提示块标签{% endnote %}

  {% note danger modern %}danger 提示块标签{% endnote %}

3. `flat`样式

  {% note flat %}默认 提示块标签{% endnote %}

  {% note default flat %}default 提示块标签{% endnote %}

  {% note primary flat %}primary 提示块标签{% endnote %}

  {% note success flat %}success 提示块标签{% endnote %}

  {% note info flat %}info 提示块标签{% endnote %}

  {% note warning flat %}warning 提示块标签{% endnote %}

  {% note danger flat %}danger 提示块标签{% endnote %}

4. `disabled`样式

  {% note disabled %}默认 提示块标签{% endnote %}

  {% note default disabled %}default 提示块标签{% endnote %}

  {% note primary disabled %}primary 提示块标签{% endnote %}

  {% note success disabled %}success 提示块标签{% endnote %}

  {% note info disabled %}info 提示块标签{% endnote %}

  {% note warning disabled %}warning 提示块标签{% endnote %}

  {% note danger disabled %}danger 提示块标签{% endnote %}

5. `no-icon`样式

  {% note no-icon %}默认 提示块标签{% endnote %}

  {% note default no-icon %}default 提示块标签{% endnote %}

  {% note primary no-icon %}primary 提示块标签{% endnote %}

  {% note success no-icon %}success 提示块标签{% endnote %}

  {% note info no-icon %}info 提示块标签{% endnote %}

  {% note warning no-icon %}warning 提示块标签{% endnote %}

  {% note danger no-icon %}danger 提示块标签{% endnote %}

{% endfolding %}

{% folding blue , 方法二 %}

1. simple样式

  {% note 'fab fa-cc-visa' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' simple %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' simple %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' simple%}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' simple %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' simple %}前端最讨厌的浏览器{% endnote %}

2. modern样式

  {% note 'fab fa-cc-visa' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' modern %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' modern %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' modern%}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' modern %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' modern %}前端最讨厌的浏览器{% endnote %}

3. flat样式

  {% note 'fab fa-cc-visa' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' flat %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' flat %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' flat%}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' flat %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' flat %}前端最讨厌的浏览器{% endnote %}


4. disabled样式

  {% note 'fab fa-cc-visa' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' disabled %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' disabled %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' disabled %}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' disabled %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' disabled %}前端最讨厌的浏览器{% endnote %}

5. no-icon样式

  {% note no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue no-icon %}2021年快到了....{% endnote %}

  {% note pink no-icon %}小心开车 安全至上{% endnote %}

  {% note red no-icon %}这是三片呢？还是四片？{% endnote %}

  {% note orange no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple no-icon %}剪刀石头布{% endnote %}

  {% note green no-icon %}前端最讨厌的浏览器{% endnote %}

{% endfolding %}

<!-- endtab -->

<!-- tab 示例源码-->

{% folding cyan , 方法一 %}


1. `simple`样式

  ```markdown
  {% note simple %}默认 提示块标签{% endnote %}

  {% note default simple %}default 提示块标签{% endnote %}

  {% note primary simple %}primary 提示块标签{% endnote %}

  {% note success simple %}success 提示块标签{% endnote %}

  {% note info simple %}info 提示块标签{% endnote %}

  {% note warning simple %}warning 提示块标签{% endnote %}

  {% note danger simple %}danger 提示块标签{% endnote %}
  ```

2. `modern`样式

  ```markdown
  {% note modern %}默认 提示块标签{% endnote %}

  {% note default modern %}default 提示块标签{% endnote %}

  {% note primary modern %}primary 提示块标签{% endnote %}

  {% note success modern %}success 提示块标签{% endnote %}

  {% note info modern %}info 提示块标签{% endnote %}

  {% note warning modern %}warning 提示块标签{% endnote %}

  {% note danger modern %}danger 提示块标签{% endnote %}
  ```

3. `flat`样式

  ```markdown
  {% note flat %}默认 提示块标签{% endnote %}

  {% note default flat %}default 提示块标签{% endnote %}

  {% note primary flat %}primary 提示块标签{% endnote %}

  {% note success flat %}success 提示块标签{% endnote %}

  {% note info flat %}info 提示块标签{% endnote %}

  {% note warning flat %}warning 提示块标签{% endnote %}

  {% note danger flat %}danger 提示块标签{% endnote %}
  ```

4. `disabled`样式

  ```markdown
  {% note disabled %}默认 提示块标签{% endnote %}

  {% note default disabled %}default 提示块标签{% endnote %}

  {% note primary disabled %}primary 提示块标签{% endnote %}

  {% note success disabled %}success 提示块标签{% endnote %}

  {% note info disabled %}info 提示块标签{% endnote %}

  {% note warning disabled %}warning 提示块标签{% endnote %}

  {% note danger disabled %}danger 提示块标签{% endnote %}
  ```

5. `no-icon`样式

  ```markdown
  {% note no-icon %}默认 提示块标签{% endnote %}

  {% note default no-icon %}default 提示块标签{% endnote %}

  {% note primary no-icon %}primary 提示块标签{% endnote %}

  {% note success no-icon %}success 提示块标签{% endnote %}

  {% note info no-icon %}info 提示块标签{% endnote %}

  {% note warning no-icon %}warning 提示块标签{% endnote %}

  {% note danger no-icon %}danger 提示块标签{% endnote %}
  ```

{% endfolding %}
{% folding blue , 方法二 %}

1. `simple`样式

  ```markdown
  {% note 'fab fa-cc-visa' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' simple %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' simple %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' simple%}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' simple %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' simple %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' simple %}前端最讨厌的浏览器{% endnote %}
  ```

2. `modern`样式

  ```markdown
  {% note 'fab fa-cc-visa' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' modern %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' modern %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' modern%}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' modern %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' modern %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' modern %}前端最讨厌的浏览器{% endnote %}
  ```

3. `flat`样式

  ```markdown
  {% note 'fab fa-cc-visa' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' flat %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' flat %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' flat%}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' flat %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' flat %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' flat %}前端最讨厌的浏览器{% endnote %}
  ```

4. `disabled`样式

  ```markdown
  {% note 'fab fa-cc-visa' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue 'fas fa-bullhorn' disabled %}2021年快到了....{% endnote %}

  {% note pink 'fas fa-car-crash' disabled %}小心开车 安全至上{% endnote %}

  {% note red 'fas fa-fan' disabled %}这是三片呢？还是四片？{% endnote %}

  {% note orange 'fas fa-battery-half' disabled %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple 'far fa-hand-scissors' disabled %}剪刀石头布{% endnote %}

  {% note green 'fab fa-internet-explorer' disabled %}前端最讨厌的浏览器{% endnote %}
  ```

5. `no-icon`样式

  ```markdown
  {% note no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note blue no-icon %}2021年快到了....{% endnote %}

  {% note pink no-icon %}小心开车 安全至上{% endnote %}

  {% note red no-icon %}这是三片呢？还是四片？{% endnote %}

  {% note orange no-icon %}你是刷 Visa 还是 UnionPay{% endnote %}

  {% note purple no-icon %}剪刀石头布{% endnote %}

  {% note green no-icon %}前端最讨厌的浏览器{% endnote %}
  ```

{% endfolding %}

<!-- endtab -->
{% endtabs %}

## 上标标签 tip

{% tip cogs %}
主要样式参考自[小康的butterfly渐变背景标签](https://www.antmoe.com/posts/3b43914f/),自己写了个`tip.js`来渲染标签，精简了一下代码。
{% endtip %}

{% tabs tip,3 %}
<!-- tab 标签语法 -->

```markdown
{% tip [参数，可选] %}文本内容{% endtip %}
```

<!-- endtab -->
<!-- tab 配置参数 -->

1. 样式: success,error,warning,bolt,ban,home,sync,cogs,key,bell
2. 自定义图标: 支持fontawesome。
   <!-- endtab -->
   <!-- tab 样式预览 -->
   {% tip %}default{% endtip %}
   {% tip info %}info{% endtip %}
   {% tip success %}success{% endtip %}
   {% tip error %}error{% endtip %}
   {% tip warning %}warning{% endtip %}
   {% tip bolt %}bolt{% endtip %}
   {% tip ban %}ban{% endtip %}
   {% tip home %}home{% endtip %}
   {% tip sync %}sync{% endtip %}
   {% tip cogs %}cogs{% endtip %}
   {% tip key %}key{% endtip %}
   {% tip bell %}bell{% endtip %}
   {% tip fa-atom %}自定义font awesome图标{% endtip %}
   <!-- endtab -->
   <!-- tab 示例源码 -->

```markdown
{% tip %}default{% endtip %}
{% tip info %}info{% endtip %}
{% tip success %}success{% endtip %}
{% tip error %}error{% endtip %}
{% tip warning %}warning{% endtip %}
{% tip bolt %}bolt{% endtip %}
{% tip ban %}ban{% endtip %}
{% tip home %}home{% endtip %}
{% tip sync %}sync{% endtip %}
{% tip cogs %}cogs{% endtip %}
{% tip key %}key{% endtip %}
{% tip bell %}bell{% endtip %}
{% tip fa-atom %}自定义font awesome图标{% endtip %}
```

<!-- endtab -->
{% endtabs%}

## 复选列表 checkbox

{% tabs checkbox,3 %}
<!-- tab 标签语法 -->

```markdown
{% checkbox 样式参数（可选）, 文本（支持简单md） %}
```

<!-- endtab -->
<!-- tab 配置参数 -->

1. 样式: plus, minus, times
2. 颜色: {% span red, red %},{% span yellow, yellow %},{% span green, green %},{% span cyan, cyan %},{% span blue, blue %},{% span gray, gray %}
3. 选中状态: checked
   <!-- endtab -->
   <!-- tab 样式预览 -->
   {% checkbox 纯文本测试 %}
   {% checkbox checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
   {% checkbox red, 支持自定义颜色 %}
   {% checkbox green checked, 绿色 + 默认选中 %}
   {% checkbox yellow checked, 黄色 + 默认选中 %}
   {% checkbox cyan checked, 青色 + 默认选中 %}
   {% checkbox blue checked, 蓝色 + 默认选中 %}
   {% checkbox plus green checked, 增加 %}
   {% checkbox minus yellow checked, 减少 %}
   {% checkbox times red checked, 叉 %}
   <!-- endtab -->
   <!-- tab 示例源码 -->

```markdown
{% checkbox 纯文本测试 %}
{% checkbox checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% checkbox red, 支持自定义颜色 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
{% checkbox cyan checked, 青色 + 默认选中 %}
{% checkbox blue checked, 蓝色 + 默认选中 %}
{% checkbox plus green checked, 增加 %}
{% checkbox minus yellow checked, 减少 %}
{% checkbox times red checked, 叉 %}
```

<!-- endtab -->
{% endtabs%}


## 单选列表 radio

{% tabs radio,3 %}
<!-- tab 标签语法 -->

```markdown
{% radio 样式参数（可选）, 文本（支持简单md） %}
```

<!-- endtab -->
<!-- tab 配置参数 -->

1. 颜色: {% span red, red %},{% span yellow, yellow %},{% span green, green %},{% span cyan, cyan %},{% span blue, blue %},{% span gray, gray %}
2. 选中状态: checked
   <!-- endtab -->
   <!-- tab 样式预览 -->
   {% radio 纯文本测试 %}
   {% radio checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
   {% radio red, 支持自定义颜色 %}
   {% radio green, 绿色 %}
   {% radio yellow, 黄色 %}
   {% radio cyan, 青色 %}
   {% radio blue, 蓝色 %}
   <!-- endtab -->
   <!-- tab 示例源码 -->

```markdown
{% radio 纯文本测试 %}
{% radio checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% radio red, 支持自定义颜色 %}
{% radio green, 绿色 %}
{% radio yellow, 黄色 %}
{% radio cyan, 青色 %}
{% radio blue, 蓝色 %}
```

<!-- endtab -->
{% endtabs%}


## 时间轴 timeline

{% tip fa-wrench %}
插件版v1.0.16以后，为避免与Butterfly_v4.0+版本中的timeline外挂标签冲突，已经移除了插件内的timeline外挂标签，请低于Butterfly_v4.0的用户升级主题或安装1.0.15版本的外挂标签插件，或者自行添加timeline.js和timeline.styl文件至对应文件夹。请使用了原有timeline外挂标签的用户受累替换语法格式。
Butterfly_v4.0+自带的timeline外挂标签样式更加好看。语法语意也更加清晰。
{% endtip %}

{% tabs timeline,2 %}
<!-- tab 标签语法 -->

```markdown
{% timeline 时间线标题（可选）[,color] %}
<!-- timeline 时间节点（标题） -->
正文内容
<!-- endtimeline -->
<!-- timeline 时间节点（标题） -->
正文内容
<!-- endtimeline -->
{% endtimeline %}
```

<!-- endtab -->

<!-- tab 参数配置 -->

| 参数            | 解释                                                         |
| :-------------- | :----------------------------------------------------------- |
| title           | 标题/时间线                                                  |
| color           | `timeline`颜色:default(留空) / blue / pink / red / purple / orange / green |
<!-- endtab -->                                                              |

<!-- tab 样式预览 -->
{% timeline 时间轴样式,blue %}

<!-- timenode 2020-07-24 [2.6.6 -> 3.0](https://github.com/volantis-x/hexo-theme-volantis/releases) -->

1. 如果有 `hexo-lazyload-image` 插件，需要删除并重新安装最新版本，设置 `lazyload.isSPA: true`。
2. 2.x 版本的 css 和 js 不适用于 3.x 版本，如果使用了 `use_cdn: true` 则需要删除。
3. 2.x 版本的 fancybox 标签在 3.x 版本中被重命名为 gallery 。
4. 2.x 版本的置顶 `top: true` 改为了 `pin: true`，并且同样适用于 `layout: page` 的页面。
5. 如果使用了 `hexo-offline` 插件，建议卸载，3.0 版本默认开启了 pjax 服务。

<!-- endtimeline -->

<!-- timeline 2020-05-15 [2.6.3 -> 2.6.6](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.6) -->

不需要额外处理。

<!-- endtimeline -->

<!-- timeline 2020-04-20 [2.6.2 -> 2.6.3](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.3) -->

1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变，使用 group 组件的文章内，`group: group_name` 对应的组件名必须是 `group_name`。
3. group 组件的列表名优先显示文章的 `short_title` 其次是 `title`。

<!-- endtimeline -->

{% endtimeline %}
<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
{% timeline 时间轴样式,blue %}

<!-- timeline 2020-07-24 [2.6.6 -> 3.0](https://github.com/volantis-x/hexo-theme-volantis/releases) -->

1. 如果有 `hexo-lazyload-image` 插件，需要删除并重新安装最新版本，设置 `lazyload.isSPA: true`。
2. 2.x 版本的 css 和 js 不适用于 3.x 版本，如果使用了 `use_cdn: true` 则需要删除。
3. 2.x 版本的 fancybox 标签在 3.x 版本中被重命名为 gallery 。
4. 2.x 版本的置顶 `top: true` 改为了 `pin: true`，并且同样适用于 `layout: page` 的页面。
5. 如果使用了 `hexo-offline` 插件，建议卸载，3.0 版本默认开启了 pjax 服务。

<!-- endtimeline -->

<!-- timeline 2020-05-15 [2.6.3 -> 2.6.6](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.6) -->

不需要额外处理。

<!-- endtimeline -->

<!-- timeline 2020-04-20 [2.6.2 -> 2.6.3](https://github.com/volantis-x/hexo-theme-volantis/releases/tag/2.6.3) -->

1. 全局搜索 `seotitle` 并替换为 `seo_title`。
2. group 组件的索引规则有变，使用 group 组件的文章内，`group: group_name` 对应的组件名必须是 `group_name`。
2. group 组件的列表名优先显示文章的 `short_title` 其次是 `title`。

<!-- endtimeline -->

{% endtimeline %}
```

<!-- endtab -->
{% endtabs%}

## 链接卡片 link

{% tip info %}由于会时不时的出现套壳问题，这里更换为[Heo](https://blog.zhheo.com/p/ccaf9148.html)大佬`tag`外挂标签{% endtip %}

{% tabs link,2 %}
<!-- tab 标签语法 -->

```markdown
{% link 标题,介绍,链接 %}
```

<!-- endtab -->

<!-- tab 样式预览 -->

<div>
    {% link 糖果屋,店长原教程,https://akilar.top/ %}
</div>
<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
 {% link 糖果屋,店长原教程 ,https://fontawesome.com/ %}
```

<!-- endtab -->
{% endtabs%}

## 按钮 btns

{% note blue 'fas fa-bullhorn' simple %}
`Volantis`的按钮使用的是`btn`和`btns`标签。`btns`和`butterfly`的`button`不冲突，但是`btn`会被强制渲染，导致部分参数失效,而且`btn`的效果还是`butterfly`的`button`更好看些。所以就只适配了`btns`。
{% endnote %}
{% tabs btn,3 %}
<!-- tab 标签语法 -->

```markdown
{% btns 样式参数 %}
{% cell 标题, 链接, 图片或者图标 %}
{% cell 标题, 链接, 图片或者图标 %}
{% endbtns %}
```

<!-- endtab -->
<!-- tab 参数配置 -->

1. 圆角样式：rounded, circle
2. 增加文字样式：可以在容器内增加 `<b>标题</b> `和` <p>描述文字</p>`
3. 布局方式：
   默认为自动宽度，适合视野内只有一两个的情况。

| 参数   | 含义                                   |
| :----- | :------------------------------------- |
| wide   | 宽一点的按钮                           |
| fill   | 填充布局，自动铺满至少一行，多了会换行 |
| center | 居中，按钮之间是固定间距               |
| around | 居中分散                               |
| grid2  | 等宽最多2列，屏幕变窄会适当减少列数    |
| grid3  | 等宽最多3列，屏幕变窄会适当减少列数    |
| grid4  | 等宽最多4列，屏幕变窄会适当减少列数    |
| grid5  | 等宽最多5列，屏幕变窄会适当减少列数    |

<!-- endtab -->
<!-- tab 样式预览 -->

1. 如果需要显示类似「团队成员」之类的一组含有头像的链接：

  {% btns circle grid5 %}
  {% cell 糖果屋, https://akilar.top, https://npm.elemecdn.com/akilar-candyassets/image/siteicon/favicon.png %}
  {% cell 糖果屋, https://akilar.top, https://npm.elemecdn.com/akilar-candyassets/image/siteicon/favicon.png %}
  {% cell 糖果屋, https://akilar.top, https://npm.elemecdn.com/akilar-candyassets/image/siteicon/favicon.png %}
  {% cell 糖果屋, https://akilar.top, https://npm.elemecdn.com/akilar-candyassets/image/siteicon/favicon.png %}
  {% cell 糖果屋, https://akilar.top, https://npm.elemecdn.com/akilar-candyassets/image/siteicon/favicon.png %}
  {% endbtns %}

1. 或者含有图标的按钮：

  {% btns rounded grid5 %}
  {% cell 下载源码, /, fas fa-download %}
  {% cell 查看文档, /, fas fa-book-open %}
  {% cell 心率管家, https://apps.apple.com/cn/app/heart-mate-pro-hrm-utility/id1463348922?ls=1, fab fa-apple %}
  {% endbtns %}

3. 圆形图标 + 标题 + 描述 + 图片 + 网格5列 + 居中

  {% btns circle center grid5 %}
  <a href='https://apps.apple.com/cn/app/heart-mate-pro-hrm-utility/id1463348922?ls=1'>
    <i class='fab fa-apple'></i>
    <b>心率管家</b>
    {% p red, 专业版 %}
  </a>
  <a href='https://apps.apple.com/cn/app/heart-mate-lite-hrm-utility/id1475747930?ls=1'>
    <i class='fab fa-apple'></i>
    <b>心率管家</b>
    {% p green, 免费版 %}
  </a>
  {% endbtns %}

<!-- endtab -->
<!-- tab 示例源码 -->

1. 如果需要显示类似「团队成员」之类的一组含有头像的链接：

  ```markdown
{% btns circle grid5 %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% cell xaoxuu, https://xaoxuu.com, https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/avatar/avatar.png %}
{% endbtns %}
  ```

2. 或者含有图标的按钮：

  ```markdown
{% btns rounded grid5 %}
{% cell 下载源码, /, fas fa-download %}
{% cell 查看文档, /, fas fa-book-open %}
{% endbtns %}
  ```

3. 圆形图标 + 标题 + 描述 + 图片 + 网格5列 + 居中

  ```markdown
{% btns circle center grid5 %}
<a href='https://apps.apple.com/cn/app/heart-mate-pro-hrm-utility/id1463348922?ls=1'>
  <i class='fab fa-apple'></i>
  <b>心率管家</b>
  {% p red, 专业版 %}
  <img src='https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/qrcode/heartmate_pro.png'>
</a>
<a href='https://apps.apple.com/cn/app/heart-mate-lite-hrm-utility/id1475747930?ls=1'>
  <i class='fab fa-apple'></i>
  <b>心率管家</b>
  {% p green, 免费版 %}
  <img src='https://cdn.jsdelivr.net/gh/xaoxuu/cdn-assets/qrcode/heartmate_lite.png'>
</a>
{% endbtns %}
  ```

<!-- endtab -->
{% endtabs%}

## 网站卡片 sites

{% tabs site,2 %}
<!-- tab 标签语法 -->

```markdown
{% sitegroup %}
{% site 标题, url=链接, screenshot=截图链接, avatar=头像链接（可选）, description=描述（可选） %}
{% site 标题, url=链接, screenshot=截图链接, avatar=头像链接（可选）, description=描述（可选） %}
{% endsitegroup %}
```

<!-- endtab -->

<!-- tab 样式预览 -->

{% sitegroup %}
{% site xaoxuu, url=https://xaoxuu.com, screenshot=https://i.loli.net/2020/08/21/VuSwWZ1xAeUHEBC.jpg, avatar=https://xaoxuu.com/assets/xaoxuu/avatar/rect-256@2x.png, description=简约风格 %}
{% site inkss, url=https://inkss.cn, screenshot=https://i.loli.net/2020/08/21/Vzbu3i8fXs6Nh5Y.jpg, avatar=https://inkss.cn/img/avatar.png, description=这是一段关于这个网站的描述文字 %}
{% site MHuiG, url=https://blog.mhuig.top, screenshot=https://i.loli.net/2020/08/22/d24zpPlhLYWX6D1.png, avatar=https://blog.mhuig.top/lib/avatar/avatar-240.webp?v=9e40245bc4, description=这是一段关于这个网站的描述文字 %}
{% site Colsrch, url=https://colsrch.top, screenshot=https://i.loli.net/2020/08/22/dFRWXm52OVu8qfK.png, avatar=https://cdn.jsdelivr.net/gh/Colsrch/images/Colsrch/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site Linhk1606, url=https://linhk1606.github.io, screenshot=https://i.loli.net/2020/08/21/3PmGLCKicnfow1x.png, avatar=https://i.loli.net/2020/02/09/PN7I5RJfFtA93r2.png, description=这是一段关于这个网站的描述文字 %}
{% endsitegroup %}

<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
{% sitegroup %}
{% site xaoxuu, url=https://xaoxuu.com, screenshot=https://i.loli.net/2020/08/21/VuSwWZ1xAeUHEBC.jpg, avatar=https://xaoxuu.com/assets/xaoxuu/avatar/rect-256@2x.png, description=简约风格 %}
{% site inkss, url=https://inkss.cn, screenshot=https://i.loli.net/2020/08/21/Vzbu3i8fXs6Nh5Y.jpg, avatar=https://inkss.cn/img/avatar.png, description=这是一段关于这个网站的描述文字 %}
{% site MHuiG, url=https://blog.mhuig.top, screenshot=https://i.loli.net/2020/08/22/d24zpPlhLYWX6D1.png, avatar=https://blog.mhuig.top/lib/avatar/avatar-240.webp?v=9e40245bc4, description=这是一段关于这个网站的描述文字 %}
{% site Colsrch, url=https://colsrch.top, screenshot=https://i.loli.net/2020/08/22/dFRWXm52OVu8qfK.png, avatar=https://cdn.jsdelivr.net/gh/Colsrch/images/Colsrch/avatar.jpg, description=这是一段关于这个网站的描述文字 %}
{% site Linhk1606, url=https://linhk1606.github.io, screenshot=https://i.loli.net/2020/08/21/3PmGLCKicnfow1x.png, avatar=https://i.loli.net/2020/02/09/PN7I5RJfFtA93r2.png, description=这是一段关于这个网站的描述文字 %}
{% endsitegroup %}
```

<!-- endtab -->
{% endtabs%}

## 音频 audio

{% tabs audio,2 %}
<!-- tab 标签语法 -->

```markdown
{% audio 音频链接 %}
```

<!-- endtab -->

<!-- tab 样式预览 -->

{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}

<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
{% audio https://github.com/volantis-x/volantis-docs/releases/download/assets/Lumia1020.mp3 %}
```

<!-- endtab -->
{% endtabs%}


## 视频 video


{% tabs video,3 %}
<!-- tab 标签语法 -->

```markdown
{% video 视频链接 %}
```

<!-- endtab -->
<!-- tab 参数配置 -->

1. 对其方向：left, center, right
2. 列数：逗号后面直接写列数，支持 1 ～ 4 列。
   <!-- endtab -->
   <!-- tab 样式预览 -->
3. 100%宽度

  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}

2. 50%宽度
   {% videos, 2 %}
     {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
     {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
     {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
     {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
     {% endvideos %}

3. 25%宽度

  {% videos, 4 %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  {% endvideos %}

<!-- endtab -->
<!-- tab 示例源码 -->


1. 100%宽度

  ```markdown
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
  ```

2. 50%宽度

  ```markdown
{% videos, 2 %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% endvideos %}
  ```

3. 25%宽度

  ```markdown
{% videos, 4 %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% video https://github.com/volantis-x/volantis-docs/releases/download/assets/IMG_0341.mov %}
{% endvideos %}
  ```

<!-- endtab -->
{% endtabs%}

## 相册 gallery

{% note blue 'fas fa-bullhorn' disabled %}
`Butterfly`自带`gallery`相册，而且会根据图片大小自动调整排版，效果比`Volantis`的`gallery`更好，故不再收录`Volantis`的`gallery`标签。
{% endnote %}
{% note %}
以下为`Butterfly`自带的`gallery`标签写法。相册图库和相册配合使用。
{% endnote %}

{% tabs gallery,3 %}
<!-- tab 标签语法 -->

1. gallerygroup 相册图库

  ```markdown
<div class="gallery-group-main">
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
{% galleryGroup name description link img-url %}
</div>
  ```

2. gallery 相册

  ```markdown
{% gallery %}
markdown 圖片格式
{% endgallery %}
  ```

<!-- endtab -->
<!-- tab 参数配置 -->

- gallerygroup 相册图库

| 参数名      | 释义                 |
| :---------- | :------------------- |
| name        | 图库名字             |
| description | 图库描述             |
| link        | 链接到对应相册的地址 |
| img-url     | 图库封面             |

{% note info %}
思维拓展一下，相册图库的实质其实就是个快捷方式，可以自定义添加描述、封面、链接。那么我们未必要把它当做一个相册，完全可以作为一个链接卡片，链接到视频、QQ、友链都是不错的选择。
{% endnote %}

- gallery 相册
  区别于旧版的Gallery相册,新的Gallery相册会自动根据图片长度进行排版，书写也更加方便，与markdown格式一样。可根据需要插入到相应的md。无需再自己配置长宽。**建议在粘贴时故意使用长短、大小、横竖不一的图片**，会有更好的效果。（尺寸完全相同的图片只会平铺输出，效果很糟糕）
  <!-- endtab -->
  <!-- tab 样式预览 -->
- gallerygroup 相册图库

<div class="gallery-group-main">
{% galleryGroup 二次元 在吾之博客中留下足迹 '/gallery/dimensional/' https://tva1.sinaimg.cn/large/0072Vf1pgy1foxkfnmbgcj31kw0w0qsa.jpg %}
{% galleryGroup 风景图 一些好看的风景图片！ '/gallery/Gundam/' https://api.r10086.com/%E5%9B%BE%E5%8C%85/%E9%A3%8E%E6%99%AF%E7%B3%BB%E5%88%979/0jp8jw.jpg %}
</div>



- gallery 相册

{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}

<!-- endtab -->
<!-- tab 示例源码 -->

{% note info %}
对于很多同学提问的`gallerygroup`和`gallery`相册页的链接问题。这里说下我个人的使用习惯。
一般使用相册图库的话，可以在导航栏加一个gallery的page(**使用指令`hexo new page gallery`添加**)，里面放相册图库作为封面。然后在`[Blogroot]/source/gallery/`下面建立相应的文件夹，例如若按照这里的示例，若欲使用`/gallery/MC/`路径访问MC相册，则需要新建`[Blogroot]/source/gallery/MC/index.md`，并在里面填入`gallery`相册内容。
{% endnote %}

1. gallerygroup 相册图库

  ```markdown
<div class="gallery-group-main">
{% galleryGroup 二次元 在吾之博客中留下足迹 '/gallery/dimensional/' https://cdn.afdelivr.top/npm/saiodgm-api@1.0.1/randomimg-my/27.webp %}
{% galleryGroup 风景图 一些好看的风景图片！ '/gallery/Gundam/' https://npm.elemecdn.com/akilar-candyassets/image/20200907110508327.png %}
</div>
  ```

2. gallery 相册

  ```markdown
{% gallery %}
![](https://i.loli.net/2019/12/25/Fze9jchtnyJXMHN.jpg)
![](https://i.loli.net/2019/12/25/ryLVePaqkYm4TEK.jpg)
![](https://i.loli.net/2019/12/25/gEy5Zc1Ai6VuO4N.jpg)
![](https://i.loli.net/2019/12/25/d6QHbytlSYO4FBG.jpg)
![](https://i.loli.net/2019/12/25/6nepIJ1xTgufatZ.jpg)
![](https://i.loli.net/2019/12/25/E7Jvr4eIPwUNmzq.jpg)
![](https://i.loli.net/2019/12/25/mh19anwBSWIkGlH.jpg)
![](https://i.loli.net/2019/12/25/2tu9JC8ewpBFagv.jpg)
{% endgallery %}
  ```

<!-- endtab -->
{% endtabs%}

## 折叠框 folding

{% note blue 'fas fa-bullhorn' disabled %}
`Butterfly`虽然也有内置折叠框`hideToggle`标签，但是`Volantis`的`folding`折叠框更好看一些。
{% endnote %}
{% tabs folding,3 %}
<!-- tab 标签语法 -->

```markdown
{% folding 参数（可选）, 标题 %}
![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)
{% endfolding %}
```

<!-- endtab -->
<!-- tab 配置参数 -->

1. 颜色：blue, cyan, green, yellow, red
2. 状态：状态填写 open 代表默认打开。
   <!-- endtab -->
   <!-- tab 样式预览 -->

{% folding 查看图片测试 %}

![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)

{% endfolding %}

{% folding cyan open, 查看默认打开的折叠框 %}

这是一个默认打开的折叠框。

{% endfolding %}

{% folding green, 查看代码测试 %}

```markdown
![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)
```

{% endfolding %}

{% folding yellow, 查看列表测试 %}

- haha
- hehe

{% endfolding %}

{% folding red, 查看嵌套测试 %}

{% folding blue, 查看嵌套测试2 %}

{% folding 查看嵌套测试3 %}

hahaha <span><img src='https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/tieba/%E6%BB%91%E7%A8%BD.png' style='height:24px'></span>

{% endfolding %}

{% endfolding %}

{% endfolding %}

<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
{% folding 查看图片测试 %}

![](https://cdn.jsdelivr.net/gh/volantis-x/cdn-wallpaper/abstract/41F215B9-261F-48B4-80B5-4E86E165259E.jpeg)

{% endfolding %}

{% folding cyan open, 查看默认打开的折叠框 %}

这是一个默认打开的折叠框。

{% endfolding %}

{% folding green, 查看代码测试 %}
假装这里有代码块（代码块没法嵌套代码块）
{% endfolding %}

{% folding yellow, 查看列表测试 %}

- haha
- hehe

{% endfolding %}

{% folding red, 查看嵌套测试 %}

{% folding blue, 查看嵌套测试2 %}

{% folding 查看嵌套测试3 %}

hahaha <span><img src='https://cdn.jsdelivr.net/gh/volantis-x/cdn-emoji/tieba/%E6%BB%91%E7%A8%BD.png' style='height:24px'></span>

{% endfolding %}

{% endfolding %}

{% endfolding %}
```

<!-- endtab -->
{% endtabs%}

## 分栏 tab

{% note blue 'fas fa-bullhorn' disabled %}
`Butterfly`的`tab`标签和`Volantis`的`tab`标签都是移值自`NexT`主题，所以写法和效果一模一样。
{% endnote %}
{% tabs folding,3 %}
<!-- tab 标签语法 -->

```markdown
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}


```

<!-- endtab -->
<!-- tab 配置参数 -->

1. Unique name :
   - 选项卡块标签的唯一名称，不带逗号。
   - 将在#id中用作每个标签及其索引号的前缀。
   - 如果名称中包含空格，则对于生成#id，所有空格将由破折号代替。
   - 仅当前帖子/页面的URL必须是唯一的！
2. [index]:
   - 活动选项卡的索引号。
   - 如果未指定，将选择第一个标签（1）。
   - 如果index为-1，则不会选择任何选项卡。
   - 可选参数。
3. [Tab caption]:
   - 当前选项卡的标题。
   - 如果未指定标题，则带有制表符索引后缀的唯一名称将用作制表符的标题。
   - 如果未指定标题，但指定了图标，则标题将为空。
   - 可选参数。
4. [@icon]:
   - FontAwesome图标名称（全名，看起来像“ fas fa-font”）
   - 可以指定带空格或不带空格；
   - 例如'Tab caption @icon' 和 'Tab caption@icon'.
   - 可选参数。
     <!-- endtab -->
     <!-- tab 样式预览 -->

{% note primary %}
Demo 1 - 预设选择第一个【默认】
{% endnote %}

{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

{% note primary %}
Demo 2 - 预设选择tabs
{% endnote %}

{% tabs test2, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

{% note primary %}
Demo 3 - 没有预设值
{% endnote %}

{% tabs test3, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}

{% note primary %}
Demo 4 - 自定义Tab名 + 只有icon + icon和Tab名
{% endnote %}

{% tabs test4 %}
<!-- tab 第一个Tab -->
**tab名字为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}

<!-- endtab -->
<!-- tab 示例源码 -->


{% note primary %}
Demo 1 - 预设选择第一个【默认】
{% endnote %}

```markdown
{% tabs test1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```

{% note primary %}
Demo 2 - 预设选择tabs
{% endnote %}

```markdown
{% tabs test2, 3 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```

{% note primary %}
Demo 3 - 没有预设值
{% endnote %}

```markdown
{% tabs test3, -1 %}
<!-- tab -->
**This is Tab 1.**
<!-- endtab -->

<!-- tab -->
**This is Tab 2.**
<!-- endtab -->

<!-- tab -->
**This is Tab 3.**
<!-- endtab -->
{% endtabs %}
```

{% note primary %}
Demo 4 - 自定义Tab名 + 只有icon + icon和Tab名
{% endnote %}

```markdown
{% tabs test4 %}
<!-- tab 第一个Tab -->
**tab名字为第一个Tab**
<!-- endtab -->

<!-- tab @fab fa-apple-pay -->
**只有图标 没有Tab名字**
<!-- endtab -->

<!-- tab 炸弹@fas fa-bomb -->
**名字+icon**
<!-- endtab -->
{% endtabs %}
```

<!-- endtab -->
{% endtabs%}

## 诗词标签 poem

{% tabs poem,3 %}
<!-- tab 标签语法 -->

```markdown
{% poem [title],[author] %}
诗词内容
{% endpoem %}
```

<!-- endtab -->
<!-- tab 参数配置 -->

1. title：诗词标题
2. author：作者，可以不写

<!-- endtab -->
<!-- tab 样式预览 -->

{% poem 水调歌头,苏轼 %}

明月几时有？把酒问青天。
不知天上宫阙，今夕是何年？
我欲乘风归去，又恐琼楼玉宇，高处不胜寒。
起舞弄清影，何似在人间？
转朱阁，低绮户，照无眠。
不应有恨，何事长向别时圆？
人有悲欢离合，月有阴晴圆缺，此事古难全。
但愿人长久，千里共婵娟。
{% endpoem %}

<!-- endtab -->

<!-- tab 示例源码 -->

```markdown
{% poem 水调歌头,苏轼 %}
丙辰中秋，欢饮达旦，大醉，作此篇，兼怀子由。
明月几时有？把酒问青天。
不知天上宫阙，今夕是何年？
我欲乘风归去，又恐琼楼玉宇，高处不胜寒。
起舞弄清影，何似在人间？

转朱阁，低绮户，照无眠。
不应有恨，何事长向别时圆？
人有悲欢离合，月有阴晴圆缺，此事古难全。
但愿人长久，千里共婵娟。
{% endpoem %}
```

<!-- endtab -->
{% endtabs%}

## 进度条 progress

{% note info morden %}
进度条标签参考[沂佰孜猫-给HEXO文章添加彩色进度条](https://rongbuqiu.com/jdt.html)。
源样式提取自[Cuteen](https://zwying0814.gitbook.io/cuteen/)主题。
{% endnote %}
{% tabs progress,3 %}
<!-- tab 标签语法 -->

```markdown
{% progress [width] [color] [text] %}
```

<!-- endtab -->
<!-- tab 参数配置 -->
`width`: 0到100的阿拉伯数字
`color`: 颜色，取值有{% span red, red %},{% span yellow, yellow %},{% span green, green %},{% span cyan, cyan %},{% span blue, blue %},{% span gray, gray %}
`text`:进度条上的文字内容
<!-- endtab -->
<!-- tab 样式预览 -->
{% progress 10 red 进度条样式预览 %}
{% progress 30 yellow 进度条样式预览 %}
{% progress 50 green 进度条样式预览 %}
{% progress 70 cyan 进度条样式预览 %}
{% progress 90 blue 进度条样式预览 %}
{% progress 100 gray 进度条样式预览 %}
<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
{% progress 10 red 进度条样式预览 %}
{% progress 30 yellow 进度条样式预览 %}
{% progress 50 green 进度条样式预览 %}
{% progress 70 cyan 进度条样式预览 %}
{% progress 90 blue 进度条样式预览 %}
{% progress 100 gray 进度条样式预览 %}
```

<!-- endtab -->
{% endtabs%}

## 注释 notation

{% tabs notation,3 %}
<!-- tab 标签语法 -->

```markdown
{% nota [label] , [text] %}
```

<!-- endtab -->
<!-- tab 参数配置 -->
`label`: 注释词汇
`text`: 悬停显示的注解内容
<!-- endtab -->
<!-- tab 样式预览 -->
{% nota 把鼠标移动到我上面试试 ,可以看到注解内容出现在顶栏 %}
<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
{% nota 把鼠标移动到我上面试试 ,可以看到注解内容出现在顶栏 %}
```

<!-- endtab -->
{% endtabs%}

## 气泡注释 bubble

{% tabs bubble,3 %}
<!-- tab 标签语法 -->

```markdown
{% bubble [content] , [notation] ,[background-color] %}
```

<!-- endtab -->
<!-- tab 参数配置 -->
`content`: 注释词汇
`notation`: 悬停显示的注解内容
`background-color`: 可选，气泡背景色。默认为“#71a4e3”
<!-- endtab -->
<!-- tab 样式预览 -->
{% raw %}

<p>最近我学到了不少新玩意儿（虽然对很多大佬来说这些已经是旧技术了），比如 CSS 的<span class="bubble-content">兄弟相邻选择器</span><span class="bubble-notation"><span class="bubble-item" style="background-color:#71a4e3;">例如 h1 + p {margin-top:50px;}</span></span>，<span class="bubble-content">flex 布局</span><span class="bubble-notation"><span class="bubble-item" style="background-color:#ec5830;"> Flex 是 Flexible Box 的缩写，意为弹性布局 "，用来为盒状模型提供最大的灵活性"</span></span>，<span class="bubble-content">transform 变换</span><span class="bubble-notation"><span class="bubble-item" style="background-color:#1db675;"> transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。</span></span>，animation 的<span class="bubble-content">贝塞尔速度曲线</span><span class="bubble-notation"><span class="bubble-item" style="background-color:#de4489;">贝塞尔曲线 (Bézier curve)，又称贝兹曲线或贝济埃曲线，是应用于二维图形应用程序的数学曲线。一般的矢量图形软件通过它来精确画出曲线，贝兹曲线由线段与节点组成，节点是可拖动的支点，线段像可伸缩的皮筋</span></span>写法，还有今天刚看到的<span class="bubble-content"> clip-path</span><span class="bubble-notation"><span class="bubble-item" style="background-color:#868fd7;">clip-path 属性使用裁剪方式创建元素的可显示区域。区域内的部分显示，区域外的隐藏。</span></span>属性。这些对我来说很新颖的概念狠狠的冲击着我以前积累起来的设计思路。</p>

{% endraw %}
<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
最近我学到了不少新玩意儿（虽然对很多大佬来说这些已经是旧技术了），比如CSS的{% bubble 兄弟相邻选择器,"例如 h1 + p {margin-top:50px;}" %}，{% bubble flex布局,"Flex 是 Flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性","#ec5830" %}，{% bubble transform变换,"transform 属性向元素应用 2D 或 3D 转换。该属性允许我们对元素进行旋转、缩放、移动或倾斜。","#1db675" %}，animation的{% bubble 贝塞尔速度曲线,"贝塞尔曲线(Bézier curve)，又称贝兹曲线或贝济埃曲线，是应用于二维图形应用程序的数学曲线。一般的矢量图形软件通过它来精确画出曲线，贝兹曲线由线段与节点组成，节点是可拖动的支点，线段像可伸缩的皮筋","#de4489" %}写法，还有今天刚看到的{% bubble clip-path,"clip-path属性使用裁剪方式创建元素的可显示区域。区域内的部分显示，区域外的隐藏。","#868fd7" %}属性。这些对我来说很新颖的概念狠狠的冲击着我以前积累起来的设计思路。
```

<!-- endtab -->
{% endtabs%}

## 引用文献 reference

{% tabs bubble,3 %}
<!-- tab 标签语法 -->

```markdown
{% referto [id] , [literature] %}
{% referfrom [id] , [literature] , [url] %}
```

<!-- endtab -->
<!-- tab 参数配置 -->

{% tip ban %}
考虑到锚点跳转的特性，不建议您将引用出处标签referfrom写在常隐外挂标签(如folding、tab、hideToggle)中，这样能有效避免跳转失败。
{% endtip %}

1. referto 引用上标
   `id`: 上标序号内容，需与referfrom标签的id对应才能实现跳转
     `literature`: 引用的参考文献名称

2. referfrom 引用出处
   `id`: 序号内容，需与referto标签的id对应才能实现跳转
     `literature`: 引用的参考文献名称
     `url`: 引用的参考文献链接，可省略

<!-- endtab -->
<!-- tab 样式预览 -->
{% raw %}

<p>Akilarの糖果屋(akilar.top)是一个私人性质的博客<span class="hidden-anchor" id="referto_[1]"></span><sup class="reference"><a href="#referfrom_[1]" data-pjax-state="">[1]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">Akilarの糖果屋群聊简介</span><span class="reference-title">参考资料</span></span></span>，从各类教程至生活点滴，无话不谈。建群的目的是提供一个闲聊的场所。博客采用Hexo框架<span class="hidden-anchor" id="referto_[2]"></span><sup class="reference"><a href="#referfrom_[2]" data-pjax-state="">[2]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">Hexo中文文档</span><span class="reference-title">参考资料</span></span></span>，Butterfly主题<span class="hidden-anchor" id="referto_[3]"></span><sup class="reference"><a href="#referfrom_[3]" data-pjax-state="">[3]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">Butterfly 安装文档(一) 快速开始</span><span class="reference-title">参考资料</span></span></span></p>
<p>本项目参考了Volantis<span class="hidden-anchor" id="referto_[4]"></span><sup class="reference"><a href="#referfrom_[4]" data-pjax-state="">[4]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">hexo-theme-volantis 标签插件</span><span class="reference-title">参考资料</span></span></span>的标签样式。引入<code>[tag].js</code>，并针对<code>butterfly</code>主题修改了相应的<code>[tag].styl</code>。在此鸣谢<code>Volantis</code>主题众开发者。<br>主要参考内容包括各个volantis的内置标签插件文档<span class="hidden-anchor" id="referto_[5]"></span><sup class="reference"><a href="#referfrom_[5]" data-pjax-state="">[5]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">Volantis文档:内置标签插件</span><span class="reference-title">参考资料</span></span></span><br>Butterfly主题的各个衍生魔改<span class="hidden-anchor" id="referto_[6]"></span><sup class="reference"><a href="#referfrom_[6]" data-pjax-state="">[6]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">Butterfly 安装文档:标签外挂（Tag Plugins</span><span class="reference-title">参考资料</span></span></span><span class="hidden-anchor" id="referto_[7]"></span><sup class="reference"><a href="#referfrom_[7]" data-pjax-state="">[7]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">小弋の生活馆全样式预览</span><span class="reference-title">参考资料</span></span></span><span class="hidden-anchor" id="referto_[8]"></span><sup class="reference"><a href="#referfrom_[8]" data-pjax-state="">[8]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">l-lin-font-awesome-animation</span><span class="reference-title">参考资料</span></span></span><span class="hidden-anchor" id="referto_[9]"></span><sup class="reference"><a href="#referfrom_[9]" data-pjax-state="">[9]</a></sup><span class="reference-bubble"><span class="reference-item"><span class="reference-literature">小康的butterfly主题使用文档</span><span class="reference-title">参考资料</span></span></span></p>

{% endraw %}

{% referfrom '[1]','Akilarの糖果屋群聊简介','https://jq.qq.com/?_wv=1027&k=pGLB2C0N' %}
{% referfrom '[2]','Hexo中文文档','https://hexo.io/zh-cn/docs/' %}
{% referfrom '[3]','Butterfly 安装文档(一) 快速开始','https://butterfly.js.org/posts/21cfbf15/' %}
{% referfrom '[4]','hexo-theme-volantis 标签插件','https://volantis.js.org/v5/tag-plugins/' %}
{% referfrom '[5]','Volantis文档:内置标签插件','https://volantis.js.org/tag-plugins/' %}
{% referfrom '[6]','Butterfly 安装文档:标签外挂（Tag Plugins','https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89' %}
{% referfrom '[7]','小弋の生活馆全样式预览','https://lovelijunyi.gitee.io/posts/c898.html' %}
{% referfrom '[8]','l-lin-font-awesome-animation','https://github.com/l-lin/font-awesome-animation' %}
{% referfrom '[9]','小康的butterfly主题使用文档','https://www.antmoe.com/posts/3b43914f/' %}

<!-- endtab -->
<!-- tab 示例源码 -->

```markdown
Akilarの糖果屋(akilar.top)是一个私人性质的博客{% referto '[1]','Akilarの糖果屋群聊简介' %}，从各类教程至生活点滴，无话不谈。建群的目的是提供一个闲聊的场所。博客采用Hexo框架{% referto '[2]','Hexo中文文档' %}，Butterfly主题{% referto '[3]','Butterfly 安装文档(一) 快速开始' %}

本项目参考了Volantis{% referto '[4]','hexo-theme-volantis 标签插件' %}的标签样式。引入`[tag].js`，并针对`butterfly`主题修改了相应的`[tag].styl`。在此鸣谢`Volantis`主题众开发者。
主要参考内容包括各个volantis的内置标签插件文档{% referto '[5]','Volantis文档:内置标签插件' %}
Butterfly主题的各个衍生魔改{% referto '[6]','Butterfly 安装文档:标签外挂（Tag Plugins' %}{% referto '[7]','小弋の生活馆全样式预览' %}{% referto '[8]','l-lin-font-awesome-animation' %}{% referto '[9]','小康的butterfly主题使用文档' %}

{% referfrom '[1]','Akilarの糖果屋群聊简介','https://jq.qq.com/?_wv=1027&k=pGLB2C0N' %}
{% referfrom '[2]','Hexo中文文档','https://hexo.io/zh-cn/docs/' %}
{% referfrom '[3]','Butterfly 安装文档(一) 快速开始','https://butterfly.js.org/posts/21cfbf15/' %}
{% referfrom '[4]','hexo-theme-volantis 标签插件','https://volantis.js.org/v5/tag-plugins/' %}
{% referfrom '[5]','Volantis文档:内置标签插件','https://volantis.js.org/tag-plugins/' %}
{% referfrom '[6]','Butterfly 安装文档:标签外挂（Tag Plugins','https://butterfly.js.org/posts/4aa8abbe/#%E6%A8%99%E7%B1%A4%E5%A4%96%E6%8E%9B%EF%BC%88Tag-Plugins%EF%BC%89' %}
{% referfrom '[7]','小弋の生活馆全样式预览','https://lovelijunyi.gitee.io/posts/c898.html' %}
{% referfrom '[8]','l-lin-font-awesome-animation','https://github.com/l-lin/font-awesome-animation' %}
{% referfrom '[9]','小康的butterfly主题使用文档','https://www.antmoe.com/posts/3b43914f/' %}
```

<!-- endtab -->
{% endtabs%}

## 旋转相册 carousel

{% tip warning %}
旋转相册标签与fancybox灯箱存在兼容性bug，若发现旋转相册呈扁平状，请关闭fancybox或换用medium_zoom。
{% endtip %}
{% tabs notation,3 %}

<!-- tab 标签语法 -->

```markdown
{% carousel [Id] , [name] %}
![](/img/1.jpg)
![](/img/2.jpg)
![](/img/3,jpg)
{% endcarousel %}
```

<!-- endtab -->
<!-- tab 参数配置 -->
`Id`: 相册唯一ID，用于监测相册鼠标动作。禁止使用中文。同一页内不得出现相同ID的carousel相册。
`name`: 相册中间显示的内容，建议用英文单引号包裹。
<!-- endtab -->

<!-- tab 示例源码 -->

```markdown
{% carousel 'dimensional','二次元阁' %}
![](http://img.xjh.me/img/57330326_p0.jpg)
![](http://img.xjh.me/img/62114697_p1_master1200.jpg)
![](http://img.xjh.me/img/63673137_p0.jpg)
![](http://img.xjh.me/img/47560048_p0.jpg)
![](http://img.xjh.me/img/62726240_p0.jpg)
![](http://img.xjh.me/img/62179212_p0.jpg)
![](http://img.xjh.me/img/62368969_p0.jpg)
![](http://img.xjh.me/img/62828151_p0.jpg)
![](http://img.xjh.me/img/63567081_p0.jpg)
![](http://img.xjh.me/img/63411064_p0.jpg)
{% endcarousel %}
```
<!-- endtab -->

<!-- tab 样式预览 -->
{% raw %}
<div>
<div id="SF" class="carousel">
<div id="SF-drag-container" class="drag-container">
<div id="SF-spin-container" class="spin-container"><br>
<img src="http://img.xjh.me/img/57330326_p0.jpg"><br>
<img src="http://img.xjh.me/img/62114697_p1_master1200.jpg"><br>
<img src="http://img.xjh.me/img/63673137_p0.jpg"><br>
<img src="http://img.xjh.me/img/47560048_p0.jpg"><br>
<img src="http://img.xjh.me/img/62726240_p0.jpg"><br>
<img src="http://img.xjh.me/img/62179212_p0.jpg"><br>
<img src="http://img.xjh.me/img/62368969_p0.jpg"><br>
<img src="http://img.xjh.me/img/62828151_p0.jpg"><br>
<img src="http://img.xjh.me/img/63567081_p0.jpg"><br>
<img src="http://img.xjh.me/img/63411064_p0.jpg">
<p>strike freedom</p>
<div id="SF-carousel-ground" class="carousel-ground" style="width:720px;height:720px"></div>
</div>
<script>carouselinit("SF")</script>
</div>
{% endraw %}
<!-- endtab -->

{% endtabs%}

