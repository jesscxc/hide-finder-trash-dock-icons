
# Hide Finder and Trash Dock Icons
For Mac OS X Mavericks (10.9)
I use the [Path Finder](http://cocoatech.com/pathfinder/) app instead of the default OS X Finder, and I never use the Trash icon on the Dock either, so I wrote this AppleScript to hide those icons and leave only what I use.


## Overview of Script
* turns off Dock indicator lights (little dots next to icon)
* restarts Dock
* hides Finder and Trash icons
* turns on indicator lights (so there is not a floating dot where the Finder icon was)


## Installation
First you need to add the "Remove from Dock" option to Finder and Trash.
* Helpful instructions at:
<https://discussions.apple.com/message/23591488#23591488>
* More detailed:
<http://apple.stackexchange.com/questions/30415/how-can-i-remove-the-finder-icon-from-my-dock>

Basically (to quote softwater and donedamned):

1) Make a backup of the file:
/System/Library/CoreServices/Dock.app/Contents/Resources/DockMenus.plist

(copy file and rename this new file to "DockMenus.backup.plist")

2) In DockMenus.plist, search for:

  a. "finder-running"

  b. and "trash" in the plist file and add at the end of both (right before the "`</array>`") in both the following:
```
<dict>
                              <key>command</key>
                              <integer>1004</integer>
                              <key>name</key>
                              <string>REMOVE_FROM_DOCK</string>
</dict>
```

You can do it with a text editor like the powerful and free [Sublime Text](https://www.sublimetext.com).


(Note: OS X seems wonky here with Section 3. Random inconsistencies, it seems. Systematically keep trying different ways if it doesn't work, is all I can suggest.)

3) To make it run at log in:

  a. Rename script without the ".txt" extension. Open script in AppleScript Editor.

  b. File > Export > File Format > Application > Save

  Alternatively for a & b: Download .app from Github repo

  c. Run app. Accept that it's not allowed Assistive Access yet.

  d. System Preferences > Security & Privacy > (Privacy tab) > (click lock) > (uncheck then check box for script app) > (click lock)

  e. System Preferences > Users and Groups > Login Items > (plus symbol: +) > (add file)

  You'll need to allow access in Administrative Assistance.


## Uninstallation
If you want to undo the entire procedure:

1) Delete the file called 'DockMenus.plist' and then rename 'DockMenus.backup.plist' to 'DockMenus.plist'.

2) In Terminal run "killall Dock".


## License

This is dedicated to public domain (via [0BSD](https://choosealicense.com/licenses/0bsd/) license).


### Message Me

If you have any issues, my contact info is at: [NoLiesPlease.com](http://NoLiesPlease.com/about)


### Thanks To
- [softwater](https://github.com/softwater)
- [donedamned](https://github.com/donedamned)
- Alexandr Mazanov
