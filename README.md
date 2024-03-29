<p align="right"><img src="https://github.com/isc-at/CPIPE/blob/master/archived.jpg"/></p>

## Fast JSON formatting (IRIS)
It's also an example for a customized command extension (ZZJSON) in IRIS 
  
IRIS has a nice %JSON.Formatter class.   
But for debugging it is not really handy.  
see:
```
ZWRITE js1  
js1="{""Name"":""Cunningham,John C."",""SSN"":""294-11-9150"",""DOB"":""1933-01-08"",""Home"":{""Street"":""4249 Ash Street"",""City"":""Tampa"",""State"":""MD"",""Zip"":""30176""},""FavoriteColors"":\[""White"",""Red"",""Green""]}"   
```  
so you proceed  for the most simple case  
```    
set formatter=##class(%JSON.Formatter).%New()   
do formatter.Format(js1)  
{   
  "Name":"Cunningham,John C.",  
  "SSN":"294-11-9150",  
  "DOB":"1933-01-08",  
  "Home":{  
     "Street":"4249 Ash Street",  
     "City":"Tampa",  
     "State":"MD",  
     "Zip":"30176"  
  },  
  "FavoriteColors":\[  
    "White",  
    "Red",  
    "Green"  
  ]  
}  
```  
Not a big thing.   
You do it once, you do it twice, and after the 5th time your fingers get tired.

So this is a shorthand to save time and reduce mistyping.

The attached ZZJSON.inc is to be included into your %ZLANGC00.mac
```  
ZZJSON js1         ; does the Output to Terminal / Device  
```  
```  
set st=##class(%Stream.GlobalCharacter).%New()
ZZJSON js1:st      ; write result to Stream
```  
```  
ZZJSON js1:"BOBBY"  ; writes it to local variable BOBBY
```  

[Article in DC](https://community.intersystems.com/post/fast-json-formatting-iris)

