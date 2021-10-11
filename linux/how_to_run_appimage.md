---
alias: [How to run AppImage, How to run an AppImage file]
tags: [appimage, how-to, execute, run, linux]
status: ongoing
edited: 2021-10-10
---

# How to run an AppImage file
There are two ways to go about it.
- GUI
- Terminal

## Using the GUI
1. Open your file manager and browse to the location of the AppImage
2. Right-click on the AppImage and click the ‘Properties’ entry
3. Switch to the Permissions tab and
4. Click the ‘Allow executing file as program’ checkbox if you are using a Nautilus-based file manager (Files, Nemo, Caja), or click the ‘Is executable’ checkbox if you are using Dolphin, or change the ‘Execute’ drop down list to ‘Anyone’ if you are using PCManFM
5. Close the dialog
6. Double-click on the AppImage file to run

## Using the Terminal

1. Open a terminal
2. Change to the directory containing the AppImage, e.g., using `cd <my directory>`
3. Make the AppImage executable: `chmod +x my.AppImage`
4. Run the AppImage: `./my.AppImage`

## Source
https://docs.appimage.org/introduction/quickstart.html