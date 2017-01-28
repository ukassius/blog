---
layout: post
title:  "Linux: Kako prikazati trenutnu potrosnju RAM memorije?"
date:   2017-01-28 18:58:26 +0100
categories: linux nedim
---

Jedan od nacina je koristiti grep alat za filter kljucnih rijeci `MemFree` iz sistemskog fajla `/proc/meminfo`

{% highlight shell %}
grep Mem /proc/meminfo
{% endhighlight %}


Za prikaz ukupe RAM memorije
{% highlight shell %}
grep MemTotal /proc/meminfo
{% endhighlight %}

Za prikaz slobodne memorije

{% highlight shell %}
grep MemFree /proc/meminfo
{% endhighlight %}

FREE KOMANDA
Komanda cesto koristena za prikazivanje trenutne potrosnje RAM memorije je komanda free. 

Primjeri upotrebe:

- Prikaz potrosnje u Gigabajtima

{% highlight shell %}
free -g
{% endhighlight %}


- Prikazm potrosnje u formatu lakse citljivom za covjeka tzv human 

{% highlight shell %}
free -g -h
{% endhighlight %}

- Total odnosno zbirni prikaz kolicine RAM memorije i velcine swap particije

{% highlight shell %}
free -g -h -t
{% endhighlight %}

- Opcija -o izbacuje prikaz linije "buffer adjusted"

{% highlight shell %}
free -g -h -o
{% endhighlight %}

- Zbog lakseg koristenja format pisanja se moze pojednostaviti u sljedeci

{% highlight shell %}
free -ghto
{% endhighlight %}

Help stranice za free komandu.

{% highlight shell %}
free --help
{% endhighlight %}

Istraziti
Actual Free Memory
Actual Free Memory = Free (39 MB) + Buffers (95) + Cached (3590) = 3,724 MB 
- Cachirana memorije? Kako se racuna? Kako iskljuciti level cachiranja u kernelu?
