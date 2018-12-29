---
title: "Linux sisteminde fayl agacina sade girish"
date: 2018-12-18T22:34:08+04:00
draft: false
tags: ["linuks","elave"]
---

## linux sade

### Fayl ve papkalar

linux sisteminde fayl agaci. 
Qeyd edekki fayl sistemini ierarxiv agac seklinde zenn ede bilerik. Bu sistemde kok ve yaxud en ust pillede **/** ingilisce **root**(esas, kok) adlanan qovluq (folder, directory) yerlesir. Diger qovluqlar onun alt qovluqlaridir. Eger sistemde **tree** emeliyati varsa onun vasitesile bu agaci visualizasiya ede bilerik.
(bu emeliyyati debian sistemde ```sudo apt install tree``` ile qurashdira bilersiniz)

```
nezeri olaraq yalanchi agac
/
├── budaq1
│   ├── budaq1.1
│   │   └── yarpaq1.0.txt
│   ├── budaq1.2
│   ├── yarpaq1.0.txt
│   └── yarpaq1.1.txt
├── budaq2
│   └── budaq2.1
├── budaq3
│   └── yarpaq3.txt
├── yarpaq0.txt
├── yarpaq1.txt
└── yarpaq2.txt
```

Agacdan gorunduyu kimi fayllar yarpaq seklinde qovluqlari ise ana budaq seklinde gostermek olar.
Eger biz numune olaraq budaq2.1,yarpaq3.txt,yarpaq1.0.txt ana qovluqdan yolu bildirmek isteyirikse asagidaki kimi yaza bilerik:
```
/budaq2/budaq2.1
/budaq3/yarpaq3.txt
/budaq1/yarpaq1.0.txt
/budaq1/budaq1.1/yarpaq1.0.txt
```
Burada ilk / en yuksek pilleni (root) bashlangici gosterir(Bir nov adsiz ust qovluqdan alta kechid kimi de baxa bilerik). novbeti /-ler ise diger pilleye kechidi gosterir.
Sonuncu misalda gorunduyu kimi (yarpaq1.0.txt) yollarda adlar deyil ierarxiya rol oynayir. Yani fayllarmizin adi eyni olsada yollari ferqlidir.
Hemcinin onuda deyekki ferqli yollarda eyniadli qovluq ve ya fayl yaza bilsekde eyni pillede yalniz tek benzersiz adda fayl ve qovluq ola biler.
Rahatliq olsun deye ust pillede olan qovlugu ana(parent) alt pillede olan qovlugu ovlad(child) eyni pillede olan qovluq ve fayllari baci(siblings) adlandira bilerik.Bizim misalda ```/budaq1``` -in ovladlari 
```
/budaq1/budaq1.2
/budaq1/yarpaq1.0.txt
/budaq1/yarpaq1.1.txt
```
Bunlar da oz aralarinda baci ```/budaq1``` ise onlarin anasi olacaq. 
Bu yollari gostermeyin 2 yolu var:  
- Mutleq (absolute)
- Nisbi (relative)
Bayaq baxdigimiz misal mutleq yoldur.Gorunduyu kimi fayl ve ya qovlugun yolunu bildirmek ucun baslangic ana qovluqdan gosteririk.Tebiiki bu cur yazilis uzun ve yorucudur.Eger biz budaqlarin birindeyikse onun alt budaqlarina ovladlarna, bacilarina, anasina nisbi yolla da muraciet etmek olar. Sade halda dediklerimizi  /budaq1 misalinda gosterek. Bu halda /-le baslamiriq,cunki,o en ust pilleni gosterir.
``` bash
# /budaq1/budaq1.1/yarpaq1.0.txt
budaq1.1/yarpaq1.0.txt
./budaq1.1/yarpaq1.0.txt
# / 
../
# /budaq2/
../budaq2/
```
Burada . ile cari .. ana qovlugu gosteririk. Bundan elave alt qovluqlara ./ evezine birbasa alt qovlugu yazmaqla da gostere bilerik.
> Sual Sizce budaq2 qovlughundan bu yol hara gedecek?
> ./../budaq2/../budaq3/././../budaq2/budaq2.1/.././

Sistemde cari qovlugun tam yolunu oyrenmek ucun ```pwd```(print working directory) emrini icra etmek kifayetdir.
Sistemde qovlughun yerini deyishmek uchun ise  ```cd```(change directory) emri ve qovlughun yolunu gostermek kifayetdir
```
cd qovlughun_yolu
```
