# Tidal-DL
Tool written in Python to download AACs & FLACs from Tidal for Windows (and soon to be Linux).
Sister of [Qobuz-DL](https://github.com/Sorrow446/Qobuz-DL).

Latest version:    
Tidal-DL: 24th Feb 19 - Release 1

![](https://thoas.feralhosting.com/sorrow/Tidal-DL/b1.jpg)
![](https://thoas.feralhosting.com/sorrow/Tidal-DL/b2.jpg)

# Setup
## Mandatory ##
The following need to be inputted into the config file:
- Email address
- Quality - 1 = LOW (96 kbps), 2 = HIGH (320 kbps), 3 = LOSSLESS, 4 = HI_RES. If the chosen qual is unavailable, the next best option will be used as a fallback.
- Plain text password
- Locale
- Naming scheme - file naming scheme (1 = "01. ", 2 = "01 -").
- Cover size - cover size to request from API (1 = 160x160, 2 = 320x320, 3 = 640x640, 4 = 1280x1280).
- Keep_cover' - leave folder.jpg in album dir, Y or N.
- All tags under "[Tags]" except comment - "Y" or "N".

**You can't download ANY tracks with a free account.**
## Optional ##
- Comment tag - custom comment. You can also input "URL" to write the album URL to the field. 
You can specify what you want to be put into the comment field in your tracks. Special characters will be escaped.
- Move_to - specify where to move album folder after downloading, "" = default.

# Usage
Fill in your config file first.
### Windows ###
Run the exe.

Tidal-DL can also be used via command line. It'll exit automatically once it finishes with no errors.
Ex:
```
Download album:
Tidal-DL_x64.exe https://listen.tidal.com/album/53834847
Download from list (List.txt) of URLs: 
Tidal-DL_x64.exe list
```

# Update Log
## Tidal-DL ##
### 24th Feb 19 - Release 1 ###

# Misc Info
Written around Python v3.6.7.  
Used libraries:
- clint
- codecs
- configparser
- datetime
- glob
- mutagen
- os
- pathlib
- re
- requests
- shutil
- sys
- time
- urllib.request

Misc:
- Any specials characters that Windows doesn't support in filenames are replaced with "-".  
- If an album folder needs to be made, but already exists, it and its contents will be deleted.  
- **If the following files exist in the current working dir, they'll be deleted: (1-1000).flac/.mp3, cover.jpg, booklet.pdf. This is to avoid any filename clashes. Filename clashes are also handled inside of album folders.**

If you need to get in touch: Sorrow#5631

# To Do
- **Restricted tracks handler.**
- **Check for checking if user's subscription is eligible to get tracks in chosen quality. Need a Premium account for this (not a Hi-Fi one).**
- GUI version.
- Single track support.
- Playlist support.
- More command line options.
- General code clean up.
- Option in config file to wipe misc tags from tracks after downloading.
Some tracks come with tags like encoder, MQA tags etc. straight from the API.


# Known Issues
- Printing languages like Chinese, Japanese & Korean to the console prints garbage instead.

This can be fixed by temporarily changing your OS' locale.
- If the "Downloading track x out of y" line is too long for the console, it'll be spammed instead of printed on a single line.

This can be fixed by setting the width & height before calling the exe, like this:
```
REM 200 & 30 should be fine
MODE CON cols=200 lines=30
QOBUZ-DL_X64.EXE
```
Enlarging the console window manually by dragging out from the edges might also work.

# Disclaimer
This tool does NOT contain code to decrypt encrypted tracks from Tidal.   
I will not be responsible for how you use this tool.
