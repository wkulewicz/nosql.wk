# Parametry Komputera 
|                      |                  Parametry                 |
|----------------------|--------------------------------------------|
|System Operacyjny     | Windows 7 Ultimate x64                     |
|Procesor              | Intel Pentium CPU B940 @2.00Ghz, 4 rdzenie |
|Pamięć RAM            | 4 GB DDR3, 1600 MHz                        |
|Dysk Twardy           | Hitachi HDD 500 GB, 3gb/s                  |
|MongoDB			   | 3.0.7										|
					                   




###Mongodb:


```js
db.rc.aggregate([
	{$match : { edited : false}}, 
	{$group : { _id : "$id", totalscore : {$sum: "$score"}}}, 
	{$sort : { totalscore : -1 }}, 
	{$limit : 10}], {allowDiskUse: true} 
)
```

###pymongo:

```js
import pymongo
client = pymongo.MongoClient("localhost", 27017)
db = client.rc
db.rc.aggregate([
	{$match : { edited : false}}, 
	{$group : { _id : "$id", totalscore : {$sum: "$score"}}}, 
	{$sort : { totalscore : -1 }}, 
	{$limit : 10}], {allowDiskUse: true} 
)
```

![](http://i.imgur.com/R1xphZP.png)

```js
{ "_id" : "wutshappening", "score" : -9122 }
{ "_id" : "dwimback", "score" : -5241 }
{ "_id" : "_PM_ME_YOUR_PROLAPSE", "score" : -5043 }
{ "_id" : "salmonhelmet", "score" : -3552 }
{ "_id" : "Andrea--Dworkin", "score" : -2460
{ "_id" : "serblop", "score" : -2410 }
{ "_id" : "fritzly", "score" : -2391 }
{ "_id" : "cwenham", "score" : -2235 }
{ "_id" : "MisterCannon", "score" : -2183 }
{ "_id" : "berylthranox4", "score" : -2153 }
```

```js
db.rc.aggregate
	([{$group:{_id:"$author", controversiality: {$sum: "$controversiality" }}}, 
    {$sort: {controversiality: 1}}, {$limit: 1} ], 
	{allowDiskUse:true}
)
```

![](http://i.imgur.com/b98Pzx2.png)


```js
import pymongo
client = pymongo.MongoClient("localhost", 27017)
db = client.rc
db.rc.aggregate
	([{$group:{_id:"$author", controversiality: {$sum: "$controversiality" }}}, 
    {$sort: {controversiality: 1}}, {$limit: 1} ], 
	{allowDiskUse:true}
)
```				  
```js				  
{ "_id" : "cnauvck", "totalscore" : 7934 }
{ "_id" : "cnatmcj", "totalscore" : 7614 }
{ "_id" : "cnatii0", "totalscore" : 6522 }
{ "_id" : "cnau6di", "totalscore" : 6384 }
{ "_id" : "cnasoau", "totalscore" : 6333 }
{ "_id" : "cnrdfcd", "totalscore" : 6105 }
{ "_id" : "co0vhbs", "totalscore" : 5703 }
{ "_id" : "cnxq08i", "totalscore" : 5694 }
{ "_id" : "cnrw9jn", "totalscore" : 5619 }
{ "_id" : "cnxq3om", "totalscore" : 5554 }				  
				  
				  

				  
```js		  
db.rc.aggregate ( [ 
	{$match: {edited: false, author_flair_text: "Male"} }, 
    {$group: { _id: null, count: 
    {$sum: 1}}} ],
	{allowDiskUse:true}
)
```

![](http://i.imgur.com/ITT1ZFj.png

```js
import pymongo
client = pymongo.MongoClient("localhost", 27017)
db = client.rc
db.rc.aggregate ( [ 
	{$match: {edited: false, author_flair_text: "Male"} }, 
    {$group: { _id: null, count: 
    {$sum: 1}}} ],
	{allowDiskUse:true}
)
```
```js
{ "_id" : null, "count" : 31446 }
```
```js				  
db.rc.aggregate ( [ 
	{$match: {edited: false, author_flair_text: "Female"} }, 
    {$group: { _id: null, count: 
    {$sum: 1}}} ],
	{allowDiskUse:true}
)

```js
import pymongo
client = pymongo.MongoClient("localhost", 27017)
db = client.rc
db.rc.aggregate ( [ 
	{$match: {edited: false, author_flair_text: "Female"} }, 
    {$group: { _id: null, count: 
    {$sum: 1}}} ],
	{allowDiskUse:true}
)
```
js```
{ "_id" : null, "count" : 5981 }
```
```js
db.rc.aggregate( [ 
	{$match: { author_flair_text: "Female" } }, 
	{ $group: { _id: null, count: {$sum: 1} } } ]
)
```
```js
import pymongo
client = pymongo.MongoClient("localhost", 27017)
db = client.rc
db.rc.aggregate( [ 
	{$match: { author_flair_text: "Female" } }, 
	{ $group: { _id: null, count: {$sum: 1} } } ]
)
```
{ "_id" : null, "count" : 5025 }

```js
db.rc.aggregate([ 
	{$match: { author_flair_text: "Male" } }, 
	{ $group: { _id: null, count: {$sum: 1} } } ]
)
```
```js
import pymongo
client = pymongo.MongoClient("localhost", 27017)
db = client.rc
db.rc.aggregate([ 
	{$match: { author_flair_text: "Male" } }, 
	{ $group: { _id: null, count: {$sum: 1} } } ]
)
```
```js
{ "_id" : null, "count" : 26193 }
```












