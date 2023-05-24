# 3. the platform element
The platform is the most key map element of all, you use it to build floors and walls and what several other elements use in order to manipulate the map. 
The platform can be used to create floorings, walls and staircases. 

Here is an example of the platform element being called, using all available parameters...

```
platform{
minx=-10
maxx=10
miny=15
maxy=35
minz=0
maxz=0
type=wood
}
```

We'll go through each parameter individually below.

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

If you ignore the maxz parameter it will default to 0.

## type
The type is the parameter that defines what tile or wall is used in the platform. 
All walls start with wall (e.g. walldesk) whereas all tiles are just a plane name (i.e. wet_ground).

If type is left blank it will act as air, although it is recommended to put the word air for readability:

`type=air`

Type will default to a blank string (acting as air).

