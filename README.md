# OSWavPlayer
This is a simple wave player that uses the command line to issue instructions to the OS to play wav files.

I wanted to write the simplest cross-platform wav player, that can do the basics and would not have
any sort of dependencies.  It simply issues subprocess calls to the operating system to play the sound, and
as long as the operating system has not been significantly altered (you have not removed the operating systems
wave playing applications) it should work.  The player issues commands to stop the subprocesses to stop playing
the sounds.

#### -Windows10 uses the Media.Soundplayer module built into Windows 10

#### -Linux uses ALSA which is part of the Linux kernel since version 2.6 and later

#### -MacOS uses the afplay module which is present OS X 10.5 and later`

To use the module simply add:
```
from wavecliplayer import *`
```
and this will import all its functions.

The module essentially contains 3 functions:
```
playwave("yourfilename")

stopwave(yourSound)

getIsPlaying(yourSound)
```
Here are some examples on how to use them.
Note that with 'playwave' it can be used as a standalone function, but if you want to stop the file from playing,
you will have to use the return value of playwave.  Read a little further and the examples should be obvious.

### Examples:

To play a wave file:
```
playwave("coolhipstersong.wav") #-> this plays the wav file

mysong=play("coolhipstersong.wav") #-> this plays the wav file and also returns the song subprocess
```

To stop your song:
```
stopwave(mysong) # -> this stops the subprocess, mysong, which you created in the line above
```

To find out if your wave file is playing:

```
isitplaying = getIsPlaying(mysong) -> sets a variable to True or False, depending on if process is running

print(getIsPlaying(mysong)) -> prints True or False depending on if process is running

if getIsPlaying(mysong)==True:
    print("Yes, your song is playing")
else:
    print("Your song is not playing")
```

To play a wave file synchronously:
```
playwave("coolhipstersong.wav",1) #-> this plays the wav file synchronously

or

playwave("coolhipstersong.wav",block=True)


* Note: commands below will work, but you cannot stop the song, because your progam will be blocked until the song is done playing

mysong=play("coolhipstersong.wav",1) #-> this plays the wav file synchronously and also returns the song subprocess
or 
mysong=play("coolhipstersong.wav",block=True) #-> this plays the wav file synchronously and also returns the song subprocess


```

### Notes about using this module as a replacement in the playsound module:

Additionally, I included an alias to the function named 'playsound', and if used, the default block will be true, or synchronous play.  This way, the
module can be used in place of the playsound module (https://github.com/TaylorSMarks/playsound/blob/master/playsound.py) with the same syntax.  If the playsound module does not work as it is no longer maintained, you can load this module and use the import statement

```
from oswavplayer import playsound
```

