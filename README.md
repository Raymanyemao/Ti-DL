# Tidal-DL
Tool written in Python to download AACs & FLACs from Tidal for Windows and Linux.
Sister of [Qobuz-DL](https://github.com/Sorrow446/Qobuz-DL).

Latest version:    
Tidal-DL: 3rd Mar 19 - Release 1c
Tidal-DL Linux: 3rd Mar 19 - Release 1c

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

Tidal-DL can also be used via command line.
Ex:
```
usage: Tidal-DL.py [-h] [-url URL] [-q Q] [-p P] [-list LIST] [-c C] [-s S]
                   [-k K]
optional arguments:
  -h, --help        show this help message and exit
  -url URL          Tidal web player URL.
  -q Q              Download quality. 1 = low (96 kbps), 2 = high (320 kbps),
                    3 = lossless, 4 = HI_RES. If the chosen qual is
                    unavailable, the next best option will be used as a
                    fallback.
  -p P              Where to move album after downloading. Make sure you wrap
                    this up in double quotes.
  -list LIST        Download from a list of URLs. -list <txt filename>.
  -c C              Cover size to fetch. 1 = 160x160, 2 = 320x320, 3 =
                    640x640, 4 = 1280x1280.
  -s S              File naming scheme. 1 = "01. ", 2 = "01 -"
  -k K              Leave folder.jpg in album dir. Y or N.
  -comment COMMENT  Custom comment. You can also input "URL" to write the
                    album URL to the field. Make sure you wrap this up in
                    double quotes.
```
# Update Log
## Tidal-DL ##
### 24th Feb 19 - Release 1 ###
### 25th Feb 19 - Release 1a ###
The below would show for everyone but me. Fixed.
```
Account doesn't have a subscription.
```
### 28th Feb 19 - Release 1b ###
- Fixed downloading albums via CLI.
- Much more command line options.
### 3rd Mar 19 - Release 1c ###
- Linux build added.
- Single track download support. This can be used with the "-url" arg too.
- Fixed album artist & track artist tags. If there are more than one, they'll be written to the tags now.
- allowStreaming check for single tracks (still need to do for albums).
- New command line arg option: comment.
- Less strict filename & dir name replace regex. Brackets and commas were being replaced before.
- Windows' max path limit handled. I couldn't do much about this. Tidal-DL won't crash anymore if it runs into this. The track's filename will be left as it was before the renaming attempt. Tags won't be affected.
- Unneeded cover.jpg wasn't being deleted before termination. This would only happen when used via command line.

# Misc Info
Written around Python v3.6.7.
Used libraries:
- argparse
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
- **If the following files exist in the current working dir, they'll be deleted: (1-1000).flac/.m4a, cover.jpg. This is to avoid any filename clashes. Filename clashes are also handled inside of album folders.**

If you need to get in touch: Sorrow#5631

# To Do
- **Check for checking if users' subscription is eligible to get tracks in chosen quality. Need a Premium account for this (not a Hi-Fi one).**
- Playlist support.
- General code clean up.
- Option in config file to wipe misc tags from tracks after downloading.
Some tracks come with tags like encoder, MQA tags etc. straight from the API.

# Known Issues
- The below will show when downloading single tracks with the -p arg / Move_to active that belong to the same album while the destination album folder already exists. This would make sense for albums, but not for single tracks.
```
"The destination album folder already exists, and access to delete it was denied. Delete it manually and then press any key.")
```
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
