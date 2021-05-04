
# Hide Finder and Trash Dock Icons

This script hides the Finder and Trash icons on the macOS Dock.

Originally developed for Mac OS X Mavericks (v10.9). Also tested on macOS High Sierra (v10.13.6).



## Overview of script

- turns off Dock indicator lights (little dots next to icon)
- restarts Dock
- hides Finder and Trash icons
- turns on indicator lights (so there is not a floating dot where the Finder icon was)



## Installation

First you need to add the "Remove from Dock" option to Finder and Trash.
- Helpful instructions at:
<https://discussions.apple.com/message/23591488#23591488>
- More detailed:
<http://apple.stackexchange.com/questions/30415/how-can-i-remove-the-finder-icon-from-my-dock>

Basically (to quote [softwater](https://github.com/softwater) and [donedamned](https://github.com/donedamned)):


1.) Make a backup of the `DockMenus.plist` file:<br/>

1a.) Create a copy of the file located at:<br/>
`/System/Library/CoreServices/Dock.app/Contents/Resources/DockMenus.plist`

1b.) Rename this new file to:<br/>
`DockMenus.backup.plist`


2.) Open `DockMenus.plist` file with a text editor (eg macOS TextEdit, or the powerful and free [Sublime Text](https://www.sublimetext.com)).


3.) Add the "Remove from Dock" menu items:

3a.) Search for `finder-running` and add at the end (right before the `</array>`):
```
		<dict>
			<key>command</key>
			<integer>1004</integer>
			<key>name</key>
			<string>REMOVE_FROM_DOCK</string>
		</dict>
```

3b.) Search for `trash` and add at the end (right before the `</array>`):
```
		<dict>
			<key>command</key>
			<integer>1004</integer>
			<key>name</key>
			<string>REMOVE_FROM_DOCK</string>
		</dict>
```



4.) To make it run at log in:

(Note: macOS may have issues with Installation step 4 (random inconsistencies, it seems). Systematically keep trying different ways if it doesn't work, is what I suggest.)

4a.) Save script to computer (can [download GitHub repo as .zip](https://www.itprotoday.com/mobile-management-and-security/how-do-i-download-files-github) and uncompress, then use the .txt file, or use the premade .app and skip to step 4e).

4b.) Change script name from `hide_finder_trash_dock_icons_scpt.scpt.txt` to `hide_finder_trash_dock_icons_scpt.scpt` (to take off the `.txt`).

4c.) Open file with [AppleScript Script Editor app](https://www.google.com/search?q=open+applescript+script+editor).

4d.) Script Editor -> File -> Export -> File Format -> Application -> Save

4e.) Turn on assistive access for the .app file in macOS via Administrative Assistance:

4e1.) Run .app. Click `OK` to accept that it's not allowed Assistive Access yet.

4e2.) Open [System Preferences app](https://www.google.com/search?q=macos+open+system+preferences) ((Apple in top left of screen) -> System Preferences...).

4e3.) System Preferences -> Security & Privacy -> (Privacy tab) -> (click lock in bottom left to unlock if necessary) -> (make sure .app file is checked to have access) -> (click lock in bottom left)

4e4.) System Preferences -> Users and Groups -> (click lock in bottom left to unlock if necessary) -> (Login Items tab) -> (plus symbol: +) -> (find and add the .app file) -> (click lock in bottom left)



## Configuration

If you don't want to toggle the indicator lights (the little icons next to the apps):

1.) Open script with AppleScript Script Editor.

2.) Change at 2 places: `my toggle_indicator_lights()` to `-- .meta my toggle_indicator_lights()`. This comments out (turns off) that function.

3.) Make the .app from the script using Installation step 4d, then continue with the rest of the installation guide.



## Issues

Not sure how to remove the left-over separator icon, yet, or if it's even possible.



## To uninstall

If you want to undo the entire procedure:

1.) Delete the `DockMenus.plist` file.

2.) Rename `DockMenus.backup.plist` to `DockMenus.plist`

2.) In [macOS Terminal](https://www.google.com/search?q=open+macos+terminal) run `killall Dock`

3.) If the .app was added to run at log in (via Installation step 4), do step 4e4 but use the minus symbol ("-") to remove the .app from startup.



## License

This is dedicated to the public domain (via the [0BSD license](https://choosealicense.com/licenses/0bsd/)).



## Contact info

If you have any issues, my contact info is at: [NoLiesPlease.com](http://NoLiesPlease.com/about)



## Thanks to

- [softwater](https://github.com/softwater)
- [donedamned](https://github.com/donedamned)
- Alexandr Mazanov
