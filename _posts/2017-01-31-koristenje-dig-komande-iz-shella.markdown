---
layout: post
title:  "Koristenje dig alata iz shella "
author: admeer
date:   2017-01-31 17:48:07 +0100
categories: linux
---
### DNS upiti pomocu dig alata.

Koristiti cemo dig alat za upit dns domenskih postavki.

###### Instalacija.

{% highlight shell %}
apt-get install dnsutils
{% endhighlight %}

##### Procedura za dobijanje liste Name Servera za domenu:

*    dobijanje liste svih root servera
*    upit na bilo koji root server za AUTHORITATIVE GTLD(Generic Top Level Domain) dns servere
*    upit na GTLD server


#### 1.  Dobijanje liste svih root servera
Dig bez argumenata dat ce listu root servera

{% highlight shell %}
$ dig

; <<>> DiG 9.10.3-P4-Ubuntu <<>>
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59928
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 26

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;.				IN	NS

;; ANSWER SECTION:
.			89460	IN	NS	d.root-servers.net.
.			89460	IN	NS	c.root-servers.net.
.			89460	IN	NS	m.root-servers.net.
.			89460	IN	NS	e.root-servers.net.
.			89460	IN	NS	j.root-servers.net.
.			89460	IN	NS	b.root-servers.net.
.			89460	IN	NS	k.root-servers.net.
.			89460	IN	NS	i.root-servers.net.
.			89460	IN	NS	a.root-servers.net.
.			89460	IN	NS	h.root-servers.net.
.			89460	IN	NS	g.root-servers.net.
.			89460	IN	NS	l.root-servers.net.
.			89460	IN	NS	f.root-servers.net.

;; ADDITIONAL SECTION:
a.root-servers.net.	22599	IN	A	198.41.0.4
a.root-servers.net.	450101	IN	AAAA	2001:503:ba3e::2:30
b.root-servers.net.	171388	IN	A	192.228.79.201
b.root-servers.net.	428118	IN	AAAA	2001:500:84::b
c.root-servers.net.	599099	IN	A	192.33.4.12
c.root-servers.net.	428118	IN	AAAA	2001:500:2::c
d.root-servers.net.	162826	IN	A	199.7.91.13
d.root-servers.net.	428118	IN	AAAA	2001:500:2d::d
e.root-servers.net.	162826	IN	A	192.203.230.10
e.root-servers.net.	428118	IN	AAAA	2001:500:a8::e
f.root-servers.net.	162826	IN	A	192.5.5.241
f.root-servers.net.	162826	IN	AAAA	2001:500:2f::f
g.root-servers.net.	162826	IN	A	192.112.36.4
h.root-servers.net.	504808	IN	A	198.97.190.53
h.root-servers.net.	162826	IN	AAAA	2001:500:1::53
i.root-servers.net.	504808	IN	A	192.36.148.17
i.root-servers.net.	162826	IN	AAAA	2001:7fe::53
j.root-servers.net.	162826	IN	A	192.58.128.30
j.root-servers.net.	162826	IN	AAAA	2001:503:c27::2:30
k.root-servers.net.	162826	IN	A	193.0.14.129
k.root-servers.net.	162826	IN	AAAA	2001:7fd::1
l.root-servers.net.	162826	IN	A	199.7.83.42
l.root-servers.net.	334494	IN	AAAA	2001:500:9f::42
m.root-servers.net.	146326	IN	A	202.12.27.33
m.root-servers.net.	150154	IN	AAAA	2001:dc3::35

;; Query time: 13 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Jan 31 18:04:30 CET 2017
;; MSG SIZE  rcvd: 783

{% endhighlight %}

#### 2.  Upit na bilo koji root server za AUTHORITATIVE GTLD(Generic Top Level Domain) dns servere

###### Uzmite bilo koji root server i postavite upit za GTLD server


{% highlight shell %}
$ dig @c.root-servers.net debian.org

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @c.root-servers.net debian.org
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15573
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 6, ADDITIONAL: 13
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;debian.org.			IN	A

;; AUTHORITY SECTION:
org.			172800	IN	NS	a2.org.afilias-nst.info.
org.			172800	IN	NS	a0.org.afilias-nst.info.
org.			172800	IN	NS	d0.org.afilias-nst.org.
org.			172800	IN	NS	b0.org.afilias-nst.org.
org.			172800	IN	NS	b2.org.afilias-nst.org.
org.			172800	IN	NS	c0.org.afilias-nst.info.

;; ADDITIONAL SECTION:
a0.org.afilias-nst.info. 172800	IN	A	199.19.56.1
a2.org.afilias-nst.info. 172800	IN	A	199.249.112.1
b0.org.afilias-nst.org.	172800	IN	A	199.19.54.1
b2.org.afilias-nst.org.	172800	IN	A	199.249.120.1
c0.org.afilias-nst.info. 172800	IN	A	199.19.53.1
d0.org.afilias-nst.org.	172800	IN	A	199.19.57.1
a0.org.afilias-nst.info. 172800	IN	AAAA	2001:500:e::1
a2.org.afilias-nst.info. 172800	IN	AAAA	2001:500:40::1
b0.org.afilias-nst.org.	172800	IN	AAAA	2001:500:c::1
b2.org.afilias-nst.org.	172800	IN	AAAA	2001:500:48::1
c0.org.afilias-nst.info. 172800	IN	AAAA	2001:500:b::1
d0.org.afilias-nst.org.	172800	IN	AAAA	2001:500:f::1

;; Query time: 53 msec
;; SERVER: 192.33.4.12#53(192.33.4.12)
;; WHEN: Tue Jan 31 18:06:04 CET 2017
;; MSG SIZE  rcvd: 441

{% endhighlight %}

#### 3. Upit na GTLD server

{% highlight shell %}
$ dig @b0.org.afilias-nst.org debian.org

; <<>> DiG 9.10.3-P4-Ubuntu <<>> @b0.org.afilias-nst.org debian.org
; (2 servers found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16453
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 3, ADDITIONAL: 3
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;debian.org.			IN	A

;; AUTHORITY SECTION:
debian.org.		86400	IN	NS	dnsnode.debian.org.
debian.org.		86400	IN	NS	sec2.rcode0.net.
debian.org.		86400	IN	NS	sec1.rcode0.net.

;; ADDITIONAL SECTION:
dnsnode.debian.org.	86400	IN	A	194.146.106.126
dnsnode.debian.org.	86400	IN	AAAA	2001:67c:1010:32::53

;; Query time: 52 msec
;; SERVER: 199.19.54.1#53(199.19.54.1)
;; WHEN: Tue Jan 31 18:06:36 CET 2017
;; MSG SIZE  rcvd: 153

{% endhighlight %}

###### Dig ce dati odgovor sa **AUTHORITY SECTION** gdje se moze naci AUTHORITY name server

##### Generic dig upit
###### Dobijanje bilo kojih postavki

{% highlight shell %}
$ dig any debian.org

; <<>> DiG 9.10.3-P4-Ubuntu <<>> any debian.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 43796
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 3, ADDITIONAL: 7

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;debian.org.			IN	ANY

;; ANSWER SECTION:
debian.org.		22362	IN	NS	sec2.rcode0.net.
debian.org.		22362	IN	NS	dnsnode.debian.org.
debian.org.		22362	IN	NS	sec1.rcode0.net.

;; AUTHORITY SECTION:
debian.org.		22362	IN	NS	dnsnode.debian.org.
debian.org.		22362	IN	NS	sec1.rcode0.net.
debian.org.		22362	IN	NS	sec2.rcode0.net.

;; ADDITIONAL SECTION:
sec1.rcode0.net.	243896	IN	A	192.174.68.100
sec1.rcode0.net.	243896	IN	AAAA	2001:67c:1bc::100
sec2.rcode0.net.	156164	IN	A	176.97.158.100
sec2.rcode0.net.	156164	IN	AAAA	2001:67c:10b8::100
dnsnode.debian.org.	18031	IN	A	194.146.106.126
dnsnode.debian.org.	18031	IN	AAAA	2001:67c:1010:32::53

;; Query time: 20 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Jan 31 18:06:58 CET 2017
;; MSG SIZE  rcvd: 728

{% endhighlight %}

###### Dobijanje MX recorda za debian.org


{% highlight shell %}
$ dig mx debian.org

; <<>> DiG 9.10.3-P4-Ubuntu <<>> mx debian.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 44681
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 3, ADDITIONAL: 9

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;debian.org.			IN	MX

;; ANSWER SECTION:
debian.org.		28692	IN	MX	0 muffat.debian.org.
debian.org.		28692	IN	MX	0 mailly.debian.org.

;; AUTHORITY SECTION:
debian.org.		28692	IN	NS	dnsnode.debian.org.
debian.org.		28692	IN	NS	sec2.rcode0.net.
debian.org.		28692	IN	NS	sec1.rcode0.net.

;; ADDITIONAL SECTION:
mailly.debian.org.	3492	IN	A	82.195.75.114
mailly.debian.org.	3492	IN	AAAA	2001:41b8:202:deb:6564:a62:52c3:4b72
muffat.debian.org.	3492	IN	A	209.87.16.33
muffat.debian.org.	3492	IN	AAAA	2607:f8f0:614:1::1274:33
sec1.rcode0.net.	30033	IN	A	192.174.68.100
sec1.rcode0.net.	30033	IN	AAAA	2001:67c:1bc::100
sec2.rcode0.net.	109157	IN	A	176.97.158.100
sec2.rcode0.net.	109157	IN	AAAA	2001:67c:10b8::100

;; Query time: 91 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Jan 31 18:08:46 CET 2017
;; MSG SIZE  rcvd: 331

{% endhighlight %}

**OBJASNJENJE**


*QUESTION SECTION*

Mozemo vidjeti koji smo upit postavili.

*ANSWER SECTION*

Unutar odjeljka mozemo vidjeti odgovor za trazeni upit.

##### Dobijanje NS servera za debian.org

{% highlight shell %}
$ dig ns debian.org

; <<>> DiG 9.10.3-P4-Ubuntu <<>> ns debian.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2519
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 7

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;debian.org.			IN	NS

;; ANSWER SECTION:
debian.org.		21167	IN	NS	sec1.rcode0.net.
debian.org.		21167	IN	NS	dnsnode.debian.org.
debian.org.		21167	IN	NS	sec2.rcode0.net.

;; ADDITIONAL SECTION:
sec1.rcode0.net.	242701	IN	A	192.174.68.100
sec1.rcode0.net.	242701	IN	AAAA	2001:67c:1bc::100
sec2.rcode0.net.	154969	IN	A	176.97.158.100
sec2.rcode0.net.	154969	IN	AAAA	2001:67c:10b8::100
dnsnode.debian.org.	16836	IN	A	194.146.106.126
dnsnode.debian.org.	16836	IN	AAAA	2001:67c:1010:32::53

;; Query time: 10 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Jan 31 18:26:53 CET 2017
;; MSG SIZE  rcvd: 241

{% endhighlight %}

##### Dobijanje A recorda za www.debian.org

{% highlight shell %}
$ dig ns debian.org

; <<>> DiG 9.10.3-P4-Ubuntu <<>> ns debian.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10740
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 7

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;debian.org.			IN	NS

;; ANSWER SECTION:
debian.org.		22054	IN	NS	sec1.rcode0.net.
debian.org.		22054	IN	NS	dnsnode.debian.org.
debian.org.		22054	IN	NS	sec2.rcode0.net.

;; ADDITIONAL SECTION:
sec1.rcode0.net.	243588	IN	A	192.174.68.100
sec1.rcode0.net.	243588	IN	AAAA	2001:67c:1bc::100
sec2.rcode0.net.	155856	IN	A	176.97.158.100
sec2.rcode0.net.	155856	IN	AAAA	2001:67c:10b8::100
dnsnode.debian.org.	17723	IN	A	194.146.106.126
dnsnode.debian.org.	17723	IN	AAAA	2001:67c:1010:32::53

;; Query time: 12 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Tue Jan 31 18:12:06 CET 2017
;; MSG SIZE  rcvd: 241
{% endhighlight %}

##### Dobijanje kratkih odgovora

{% highlight shell %}
$ dig +short ns debian.org
dnsnode.debian.org.
sec1.rcode0.net.
sec2.rcode0.net.
{% endhighlight %}
