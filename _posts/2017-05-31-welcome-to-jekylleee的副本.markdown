---
layout: post
title:  "搭建这个独立博客"
date:   2017-07-05 14:58:00 +0800
categories: jekyll update
---

首先贴链接，主要参考了这篇博文：
[“授人以渔”的教你搭建个人独立博客][Link1]：http://www.jianshu.com/p/8f843034c7ec

文章中介绍的非常详细，然而在实际搭建的过程中，还是遇到了很多坑，尝试了各种思路。

其实早在几周前，已经在另一台电脑上安装成功了，但是今天装到macbook上时，还是遇到了一些新问题，当然，主要也是因为我尝试新思路而给自己挖的坑。（此处该有表情🤦‍）

来总结一下遇到的问题吧：

{% highlight ruby %}
ERROR:  While executing gem ... (Errno::EPERM)

    Operation not permitted - /usr/bin/bundler
{% endhighlight %}

[参考][Link2]：http://blog.csdn.net/leaf8742/article/details/50466619

解决方法1：换个路径安装，`sudo gem install -n /usr/local/bin bundler`
需要[配置环境变量][Link3]，但是治标不治本，还是会有这种情况出现

解决方法2：
下载命令行工具： `http://brew.sh`
下载过后，运行命令行 `brew install ruby`

{% highlight ruby %}
Bundler::GemNotFound
{% endhighlight %}
这个就非常麻烦了，在原来的电脑上，由于上一步是用解决方法1，所以配置环境变量.bash_profile就可以解决

但是在macbook上使用了解决方法2，而工程还用原本的git，所以一直找不到ruby路径，最终使用bundle替代（不能算解决）

{% highlight ruby %}
# 1.如果没有安装bundle
gem install bundle
# 2.jekyll-blog目录创建Gemfile文件，内容参考链接
# 3.运行bundle，安装Gemfile里的插件(姑且叫插件吧，我也不知道叫啥~_~!)
bundle install 
# 4.打开服务
bundle exec jekyll serve
# or
jekyll serve
{% endhighlight %}

目前jekyll serve依然报错，bundle exec jekyll serve可以运行成功。（待解决）

[Link1]: http://www.jianshu.com/p/8f843034c7ec
[Link2]: http://blog.csdn.net/leaf8742/article/details/50466619
[Link3]: http://www.cnblogs.com/nekoooo/p/5477987.html
