---
layout: post
title:  "Ruby: Kako generisati random lozinku pomocu Ruby programskog jezika"
author: nedim
date:   2017-01-28 21:07:26 +0100
categories: ruby
---

### Nekoliko primjera kako pomocu `Ruby` generisati random lozinke


Pokrenute IRB pomocu komande `irb` zatim prekucajte kod ispod

{% highlight ruby %}
(0...8).map { (65 + rand(26)).chr }.join
{% endhighlight %}

Takodjer isti kod mozete pokrenuti direktno iz CLI 

{% highlight bash %}
ruby -e "puts (0...8).map { (65 + rand(26)).chr }.join"
{% endhighlight %}

### Drugi primjer

{% highlight ruby %}
(0...50).map { ('a'..'z').to_a[rand(26)] }.join
{% endhighlight %}

