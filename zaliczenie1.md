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
4:21:34

```

![](http://i.imgur.com/xXI9ufd.png)
###Szczegółowe dane na temat pracy komputera:
![](http://i.imgur.com/NxwDz9G.png)

![](http://i.imgur.com/uAhKrty.png)




###PosgreSQL

![](http://i.imgur.com/94DjQth.png) ![](http://i.imgur.com/xQPbqXv.png) ![](http://i.imgur.com/RNDlbvY.png) ![](http://i.imgur.com/6jb0vwa.png)


2:34:50



###Wniosek: Import tej samej bazy do MongoDB trwał prawie dwa razy dłużej. Jeżeli chodzi o obciażenie podzespołów to było ono podobne.




###Przykładowy rekord z zimportowanej bazy danych

![](http://i.imgur.com/1iD73z5.png)


##Zadanie.1b (Zliczanie rekordów)

###Mongodb:

![](http://i.imgur.com/lLgdQq9.png)

```sh

00:21:40

```
###PostgreSQL:

![](http://i.imgur.com/hVpZ5yd.png)

```sh

00:15:20

```


##Zadanie.1c

##Mongodb

```sh

db.rc.find({"edited" : false, "author" : "YoungModern", "score" : {$gt: 15}}).count()
6

```
```sh


db.rc.find({"edited" : false}).count()
1618274

```




##Postgresql

```sh

SELECT count(*) FROM IMPORT.RC_2015_01 WHERE edited=false AND authoR=YoungModern AND score<15;
6

```

```sh

SELECT count(*) FROM IMPORT.RC_2015_01 WHERE edited=false;
1618274

```



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
###1. Point

```sh

var GrodziskMazowiecki = {
               "type": "Point",
               "coordinates":[ 21.020, 52.259]
               }

db.lotniskacoll7.find({ loc: {$near: {$geometry: GrodziskMazowiecki}} }).limit(3)

```

[Wyniki wygenerowane na mapie](https://github.com/wkulewicz/nosql.wk/blob/master/grodzisk.geojson)

###2. Point

```sh

		  var Mragowo = 
		            {
               "type": "Point",
               "coordinates":[ 21.298370361328125,
                53.88167850008248]
               }

db.lotniskacoll7.find({ loc: {$near: {$geometry: Mragowo}} }).limit(5)

```

[Wyniki wygenerowane na mapie](https://github.com/wkulewicz/nosql.wk/blob/master/mragowo.geojson)



###3. Polygon

```sh

db.l.find({
    loc: {
        $geoWithin: {
            $geometry: {
                "type": "Polygon",
                "coordinates": [[
            [
              19.324951171875,
              54.25238930276849
            ],
            .
            .
            .
            ]
          ] ]
      } } } }
 )

```

[Wyniki wygenerowane na mapie](https://github.com/wkulewicz/nosql.wk/blob/master/polygon.geojson)


###4. LineString

```sh
var line = {
    "type": "LineString",
    "coordinates": [[19.017333984375,
          50.29635802110316], [19.456787109374996,
          51.80182150078305]]
}

db.lotniskacoll7.find({
    loc: {
        $geoIntersects: {
            $geometry: line
        }
    }
}).limit(3)
```

Polecenie nie wygenerowało żadnych wyników.














