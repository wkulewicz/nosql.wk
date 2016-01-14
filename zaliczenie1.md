# Parametry Komputera 
|                      |                  Parametry                 |
|----------------------|--------------------------------------------|
|System Operacyjny     | Windows 7 Ultimate x64                     |
|Procesor              | Intel Pentium CPU B940 @2.00Ghz, 4 rdzenie |
|Pamięć RAM            | 4 GB DDR3, 1600 MHz                        |
|Dysk Twardy           | Hitachi HDD 500 GB, 3gb/s                  |
|MongoDB			         | 3.0.7								                        		|
|PostgreSQL		    	   | 9.5.0							                      			|



##Zadanie.1a (Import bazy reddit)

###Mongodb:

```sh

mongoimport -d zad1 -c rc -type json --file "C:\RC_2015-01.json
4:12:37

```

![](http://i.imgur.com/xXI9ufd.png)
Wykres pracy procesora:
![](http://i.imgur.com/NxwDz9G.png)
Szczegółowe dane na temat pracy komputera:
![](http://i.imgur.com/uAhKrty.png)




###PosgreSQL

![](http://i.imgur.com/94DjQth.png) ![](http://i.imgur.com/xQPbqXv.png) ![](http://i.imgur.com/RNDlbvY.png) ![](http://i.imgur.com/6jb0vwa.png)









###Przykładowy rekord z zimportowanej bazy danych

![](http://i.imgur.com/1iD73z5.png)


##Zadanie.1b (Zliczanie rekordów)

###Mongodb:

![](http://i.imgur.com/lLgdQq9.png)

```sh

00:21:43

```
###PostgreSQL:

![](http://i.imgur.com/hVpZ5yd.png)

```sh

00:15:16

```

##Zadanie.1c

...


##Zadanie.1d

Specjalnie dla potrzeb projektu stworzyłem mape Geojson dla lotnisk znajdujących się na terenie Polski. W tym celu wykorzystałem stronę http://geojson.io/.

![](http://i.imgur.com/1p9odFi.png)


###Import bazy:

```sh

mongoimport -c lotniskacoll7 < C:\lotniska.json

```

###Przykładowy rekord bazy

```sh

db.lotniskacoll7.findOne()

```

![](http://i.imgur.com/dYQXjHE.png)

###Dodanie geo-indexów

```sh

db.places.ensureIndex({"loc" : "2dsphere"})

```

























