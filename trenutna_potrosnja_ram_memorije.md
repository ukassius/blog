---
layout: page
title: Kako prikazati trenutnu potrosnju RAM memorije?
permalink: /linux_ako_prikazati_trenutnu_potrosnju_ram_memorije/
---

Jedan od nacina je koristiti grep alat za filter kljucnih rijeci MemFree iz sistemskog fajla /proc/meminfo
grep Mem /proc/meminfo
Za prikaz ukupe RAM memorije
grep MemTotal /proc/meminfo
Za prikaz slobodne memorije
grep MemFree /proc/meminfo
FREE KOMANDA
Komanda cesto koristena za prikazivanje trenutne potrosnje RAM memorije je komanda free. 
Primjeri upotrebe:
- Prikaz potrosnje u Gigabajtima
free -g
- Prikazm potrosnje u formatu lakse citljivom za covjeka tzv human 
free -g -h
- Total odnosno zbirni prikaz kolicine RAM memorije i velcine swap particije
free -g -h -t
- Opcija -o izbacuje prikaz linije "buffer adjusted"
free -g -h -o
- Zbog lakseg koristenja format pisanja se moze pojednostaviti u sljedeci
free -ghto
Help stranice za free komandu.
free --help
Istraziti
Actual Free Memory
Actual Free Memory = Free (39 MB) + Buffers (95) + Cached (3590) = 3,724 MB 
- Cachirana memorije? Kako se racuna? Kako iskljuciti level cachiranja u kernelu?
