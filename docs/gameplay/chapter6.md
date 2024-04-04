# The Location Template
The location template is a very powerful tool. It allows you to configure what information is given to you when you press the location key (C by default).

Its fairely complicated so be patient



It is a line of text that contains variables, these variables are replaced by the game with values. 
Variables are surrounded in braces (`{` and `}`). 


The variables are:

 - `x` - your x coordenate.
 - `y` - your y coordenate
 - `z` - your z coordenate
 - `x_rounded` - your x coordenate rounded to the nearest integer
 - `y_rounded` - your y coordenate rounded to the nearest integer
 - `z_rounded` - your z coordenate rounded to the nearest integer.
 - `tile` - the tile type you're currently standing on
 `direction` - your cardinal direction (north, east, south west, etc)
 - `angle` - your angle (in line with your cardinal direction)
 - `pitch` - Your verticle angle, so how far you are tilted forward or backwards.
 - `lean` - how far you are leaning to the left or right.
 - `balanced` - Weather you are balanced or unbalanced. 


### a very verbose Example:
```template
You are standing at {x}, {y}, {z} - {x_rounded}, {y_rounded}, {z_rounded}. You are standing on {tile}. You are facing {direction} at an angle of {angle} degrees. You are pitched at an angle of {pitch} degrees and are leaning by {lean} degrees, therefore you are {balanced}.
```