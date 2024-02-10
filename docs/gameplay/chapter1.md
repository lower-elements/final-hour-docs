# 1. Configuring the game and getting connected
This chapter will guide you through the offline process of setting up the game and creating an account.
If you have sight, the games text is printed to the screen, however otherwise you will need 

 - A SAPI voice you are comfortable with, NVDA or JAWS (if you are on windows, no installed software is needed for linux or macOS)

and

 - A set of deacent headphones or a surround sound speaker setup

Now you are ready to go, lets jump in.


## 1.1. The Main Menu
This is all fairely self-explanitary so i'll just give a brief overview of each item.

Menus are navigated using the arrows and the return key. 


 - Login: If you have an account set, this will log you directly into the server.
 - Set Account: this opens a dialog in which you must enter your username and password for an existing account.
 - Create Account: this opens a dialog in which you must enter a username and password to your new account. You will also have to agree to [our rules](https://finalhour.lowerelements.club/agreement) at this stage. 
 - options: this opens the options menu, which we will go through in the next section. 
 - exit: quits the game.

## 1.2. The options menu
The options menu is a little more complicated and so i'll go through each option indevidually


### player beacons
Player beacons are an audio source tied to a player so that you are able to locate their character as they navigate the map. 

This also allows you to distinguish them between players and zombies in matches, so if you easily get frightened by footsteps in matches, you might want to keep this one on, no need to shoot your mates. 


### Stream Ambience 
Stream Ambience means that ambience sounds, which are general background sounds like birds or wind, will be played directly from disc opposed from memory. 

this means that if you have this on, your CPU usage will be higher but the amount of RAM used by the game will be less; although, this change will most-likely be marginal. 


Its safe to say that, if you're not having issues, you can leave this option be, its mainly a performence consideration for less powerful computers. 


### Receive Typing Indicators
Typing Indicators are spoken text telling you when somebody has started typing, this might be worth turning off when the game has a lot of players chatting at once. 

### Set how you would like timestamps in the end of buffer items to be displayed
This option opens a menu with 3 options:

 - absolute time,
 - relative time,
and
 - don't display time stamps

time stamps are displayed at the end of buffer items in the main game (chats and other game messages).

Relative time is how long ago a buffer item was received by the client whereas absolute time shows an exact time such as 04:20PM.


### Set which Head-related Transform Function Model you would like to use. 
Head-Related Transform function (HRTF) is a method of creating more realistic sounding 3d audio. We current previde 3 models and the option to disable HRTF entirely.

Some people prefer it to OpenAL's (our audio library's) default 3d audio and some people much prefer it. 

Each model has suttle differences and we recommend trying a few games on different models once you've settled into the game a bit so you can find which works best for you. 


### edit location template
This i will leave for a later part of the documentation as this deserves its own chapter, for now leave this as it is. 

### configure key bindings
This opens a menu of different actions in the game. If you select one of these options, you can press a key and the game will use it for that action from now on.
