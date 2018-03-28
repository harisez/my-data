https://unix.stackexchange.com/questions/40242/scroll-inside-screen-or-pause-output

===

Screen has its own scroll buffer, as it is a terminal multiplexer and has to deal with several buffers.

Maybe there's a better way, but I'm used to scrolling using the "copy mode" (which you can use to copy text using screen itself, although that requires the paste command too):

Hit your screen prefix combination (C-a / control+A by default), then hit Escape.

Move up/down with the arrow keys (↑ and ↓).

When you're done, hit q or Escape to get back to the end of the scroll buffer.

(If instead of q or Escape you hit Enter or Return and then move the cursor, you will be selecting text to copy, and hitting Enter or Return a second time will copy it. Then you can paste with C-a followed by ].)

Of course, you can always use more and less, two commonly used pagers, which may be enough for some commands.

===


Using the screen buffer as pointed out by njsg is a good solution. You can also disable the alternate text buffer in the xterm termcap info inside screen. When disabled you can use the scroll bars (and mouse wheel) to scroll up and down.

Add this to your ~/.screenrc.

# Enable mouse scrolling and scroll bar history scrolling
termcapinfo xterm* ti@:te@
You can read more discussion https://unix.stackexchange.com/questions/18006/can-mouse-wheel-scrolling-work-in-a-usr-bin-screen-session


===

All these answers addressed how to navigate within a screen session, but there is a built-in functionality in screen command to store everything in a file through the -L argument according to the manual which reads:

-L tells screen to turn on automatic output logging for the windows.

so you can do:

screen -L -S testscreen
and it will create a file withe the screenlog.# where the # is a number for that screen starting from 0.

This has lots of advantages and the most important ones for me are:

Keeping record of what i have done since I can save the log file in the project folder for future reference.
You can inactively and passively monitor the process:
use tailf to monitor the progress in realtime without being attached to the screen.
use grep to check for certain term in the log and produce notifications (email, popup, voip, etc.). This can be applied on multiple screens without you actively looking at them.

==

