# gcode-thumbnailer

Examples:

![Example at 2 * Zoom](https://github.com/ellensp/gcode-thumbnailer/blob/main/examples%20(2xZoom).png?raw=true)

A simple thumbnail generator for Gnome.
This extracts the encoded thumbnail data from within a gcode file and turns it into OS useable thumbnail, such as in nautilus.

Only tested on Ubuntu 20.04.4 LTS.

Consists of two files:

Gcode-with-thumbnail-thumbnailer.py
The python script that extracts and generates the required png file.

gcode-with-thumbnail.thumbnailer
Configuration file to associate *.gcode with the thumbnailer application.

Installation is manual:

Copy gcode-with-thumbnail.thumbnailer to /usr/share/thumbnails/
Copy gcode-with-thumbnail-thumbnailer.py to somewhere in you path. For eg /usr/local/bin/
Make sure it is executable.
Copy gcode-icon.png to /usr/share/icons/hicolor/48x48/apps/

This will be used as the default if there is no embedded thumbnail

```
sudo cp gcode-with-thumbnail.thumbnailer /usr/share/thumbnails/
sudo cp gcode-with-thumbnail-thumbnailer.py /usr/local/bin/
sudo chmod a+x /usr/local/bin/gcode-with-thumbnail-thumbnailer.py
sudo cp gcode-icon.png /usr/share/icons/hicolor/48x48/apps/
```

How to add thumbnail to gcode:

I used the method mentioned here https://github.com/mriscoc/Ender3V2S1/wiki/How-to-generate-a-gcode-preview

This is also compatable with PrusaSlicer 2.4.2 inbuilt thumbnail generator.

## Mime Type

For this to work, the files must have a mime type of `text/x.gcode`. On some systems, gcode files will be `text/plain`. You can confirm this by running this command in the terminal: `mimetype {gcode-file}`, replacing `{gcode-file}` with the name of a Gcode file on your computer.

If the output of this command is not `text/x.gcode`, you will need to add the correct mime type.

Copy gcode.xml to ~/.local/share/mime/packages

Now run the following commands to update the mime database:

```
sudo update-mime-database ~/.local/share/mime/
sudo update-mime
```