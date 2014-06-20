ESET-Custom-Installer-for-Mac
=============================

The apple script supports the GUI installation of ESET Custom Installer for Mac

# Construction in DMG file

- ESET_Setup.app: Installer (Apple Script)
- README.rtf: Handling manual (Template)
- .background: Background image folder (Hidden Folder)
- .packages: Standalone ESET Custom Installer files (esets_remote_install.pkg, esets_remote_uninstall.sh, esets_setup.sh)
* Three files are dummy because they are created by ESET remote installer.

## Attribution of DMG file

For automatically opening the mounted volume when the DMG file is opened, the following command was done.

1. Mount DMG file (for example, mounted volume name is "/Volumes/ESET-Custom-Installer").
1. Open "Terminal" application 
2. Type "bless /Volumes/ESET-Custom-Installer --openfolder /Volumes/ESET-Custom-Installer" and push "Enter" key.

## Before provide the DMG file.
You had better convert it to the DMG file with compression 
Because the converted DMG file is mounted as read-only file system.

1. Open "Disk Utility" application in Utility folder.
2. Click on "Convert" button in the menu bar and select the DMG file.
3. Confirm to enable "compress" option, save as it.

# Prepalation

There are some hidden folders, so you had better change the setting of the hidden folder/file visualization.

## How to view the hidden folder/file.

1. Open "Terminal" application in the Utilities folder (in Application folder).
2. Type "defaults write com.apple.finder AppleShowAllFiles -boolean true" command and push "Enter" key.
3. Type "killall Finder" command and push "Enter" key.

## How to hide the hidden folder/file.

1. Open "Terminal" application in the Utilities folder (in Application folder).
2. Type "defaults delete com.apple.finder AppleShowAllFiles" command and push "Enter" key.
3. Type "killall Finder" command and push "Enter" key.

# Explanation

## ESET_Setup.app
It's very simple apple script.
It carries out the following behavior.

1. Copy "esets_remote_install.pkg" and "esets_setup.sh" to "/tmp/" folder with administrator permission.
2. Carry out "esets_remote_install.pkg" including the custom setting (esets_setup.sh) with administrator permission 

If you'd like to change the mounted name of DMG file (default: ESET-Custom-Installer), you open "ESET_Setup.app" using Apple Script Editor (Search "Apple Script" on Spotlight) and edit the name of "ESET-Custom-Installer".

## README.rtf
This is very simple handling manual in English and Japanese.

Especially, you need to pay attention about the security execution policy setting of the application.
Basically, MacOSX blocks the execution of the untrusted application under the security setting.
For getting the permission, it needs to right click the application icon and select "Open".

This is the manual for explaining it.

## .background

This is the hidden folder, so if you access it, there are three approaches.

- 1) Push "Command+Shift+G" and Input the full path (/Voulmes/ESET-Custom-Installer/.background) in the dialog box.
- 2) Open "Terminal" application, Type "open /Voulmes/ESET-Custom-Installer/.background" and push "Enter" key..
- 3) If you enable to display the hidden files/folders, right click ".background" folder and select "Open" menu.

If you would like to change the background image, please carry out the following operation.

1. Save the background image to ".background" folder
2. Open the top folder of the mounted volume (/Voulmes/ESET-Custom-Installer)
3. Type "Command+J" and Select "Picture" in the background section.
4. The image file drag and drop to the "Drag image here".

I think that the section 8 "Change the Views" in following site is easy explanation.

Reference: [How To: Create DMG Art for Fancy Application Installations](http://mac101.net/content/how-to/how-to-create-dmg-art-for-fancy-application-installations/) (Mac 101)

### How to create ".background" hidden folder.

1. Create ".background" folder in "/Voulmes/ESET-Custom-Installer/".
2. Open "Terminal" application.
3. Type "SetFile -a V "/Voulmes/ESET-Custom-Installer/.background" and push "Enter" key.
* This is to add the hidden attribution to the folder.

## .packages

This folder consists of the standalone preconfigured installation package for installing the  ESET software with the custom settings including the linkage  setting of the administration server.

About how to create ESET custom installer package, please see "[How do I remotely install ESET NOD32 Antivirus Business Edition for Mac OS X?](http://kb.eset.com/esetkb/index?page=content&id=SOLN2524)". 
* Japanese information: http://canon-its.jp/supp/eset/etlr40015.html

