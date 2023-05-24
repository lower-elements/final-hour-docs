# 1. the map syntax
## 1.1. What are map elements?
Map elements are the different features that one uses to build a map, these are (and not limitted too):

 - platforms
 - doors
 - windows
 - etc

These elements can be combined together to create ritch and challenging maps to fight in making the game a more enjoyable and varied to play. 

## 1.2. How to spawn map elements
Map elements are spawned through a call in mapdata (the textual format in which we store maps). You specify the element then provide it with a series of parameters that define its properties.

You format it as follows

```
element_name{
parameter1=value
parameter2=value
parameter3=value
...
}
```



Here's a practicle example, don't worry, the parameters will be xplained at a later date:



Example:
-----
```
platform{
minx=-10
maxx=10
miny=-10
maxy=10
minz=0
maxz=0
type=grass
}
zone{
minx=-10
maxx=10
miny=-10
maxy=10
minz=0
maxz=10
text=A big greend and beautiful field
}
```


