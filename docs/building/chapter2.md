# 2. The map element
The map element is what you need to start every map with, it defines the size of the map, whether it is public and what, if any, map script it uses is.

Here is an example of a map element being called, using all the available parameters.

```
map{
minx=-200
maxx=200
miny=-100
maxy=100
minz=0
maxz=50
public=true
script=my_example_script
}
```

We'll go through each parameters individually below.


## minx
the minx (meaning minimum x) parameter is the west most boundry of the map. 

If you ignore the minx parameter it will default to 0

## maxx
the maxx (meaning maximum x) parameter is the east most boundry of the map. 

If you ignore the maxx parameter it will default to 0


## miny
the miny (meaning minimum y) parameter is the south most boundry of the map. 

If you ignore the miny parameter it will default to 0

## maxy
the maxy (meaning maximum y) parameter is the north most boundry of the map. 

If you ignore the maxy parameter it will default to 0

## minz
the minz (meaning minimum z) parameter is the bottom most boundry of the map. 

If you ignore the minz parameter it will default to 0

## maxz
the maxz (meaning maximum z) parameter is the up most boundry of the map. 

If you ignore the maxz parameter it will default to 0


## public
Public defines if a map should be playable from the main menu. No maps will be public until confirmed to be playable.

Public defaults to false.


## script
The script parameter takes a map script and loads it (more on map scripts later)

script defaults to null.



