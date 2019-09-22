---
title: 各种调用2
date: 2019-08-09 11:09:49
tags: [折腾ing]
published: true
hideInList: false
feature: /post-images/无他.png
---
[Markdown 语法简单教程](https://fehey.com/post/markdown-yu-fa-jian-dan-jiao-cheng/)


<!-- more -->

北村熏的空中飞马
[这是哔哩哔哩](https://www.bilibili.com)
**矮个人如何**
## 嘎嘎
### 如图
尝试调用今日诗词api（图形）
![今日诗词](https://v2.jinrishici.com/one.svg?font-size=20&spacing=2&color=brown)
尝试调用今日诗词api（文字）
<span id="jinrishici-sentence">正在加载今日诗词....</span>
<script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
今日诗词api高级用法
<script src="https://sdk.jinrishici.com/v2/browser/jinrishici.js" charset="utf-8"></script>
<div id="poem_sentence"></div>
<div id="poem_info"></div>
<script type="text/javascript">
  jinrishici.load(function(result) {
    var sentence = document.querySelector("#poem_sentence")
    var info = document.querySelector("#poem_info")
    sentence.innerHTML = result.data.content
    info.innerHTML = '【' + result.data.origin.dynasty + '】' + result.data.origin.author + '《' + result.data.origin.title + '》'
  });
</script>



<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=450 src="https://music.163.com/outchain/player?type=0&id=2423545044&auto=1&height=430"></iframe>

<script type="text/javascript" src="https://api.xygeng.cn/dailywd/api/getjs.php"></script>

<img src="https://api.xygeng.cn/bing/1920.php" alt="Bing每日图片超高清" />
