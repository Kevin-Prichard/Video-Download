# Video-Download.py

Description: GUI for downloading lists of video URLs using yt-dlp library.
Author: Josh Buchbinder

## General usage

`Video-Download` is a PySide6 (Qt) GUI wrapper around the `yt-dlp`
python library that will parse a text file containing a list of URLs
or an HTML file of bookmarks exported from a browser and attempt to
download the video in each URL. See `yt-dlp` documentation to see
what type of video sites are
[supported](https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md).

## Setup

After cloning this repo, follow these steps to get up and running-

1. Ensure you have a recent Python 3 installed (python 3.10 and later)
2. Create a venv virtual environment, where packages installed for Video-Download will live:
```bash
you@localhost $ python3.10 -m venv venv   # change the version number as desired
```
3. Activate the venv environment (for *nix shells)
```bash
you@localhost $ source venv/bin/activate
```
4. Now install requirements.txt
```bash
(venv) you@localhost $ pip install -r requirements.txt
```
5. And make the script executable-
```bash
(venv) you@localhost $ chmod u+x Video-Download.py
```

The first time you execute the script, you may find that additional system libraries are required, such as `ffmpeg`.

For example, a first run on Ubuntu 22.04 LTS gave the following response-
```bash
(venv) you@localhost $ ./Video-Download.py 
qt.qpa.plugin: From 6.5.0, xcb-cursor0 or libxcb-cursor0 is needed to load the Qt xcb platform plugin.
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, xcb, minimal, offscreen, vnc, linuxfb, wayland, wayland-egl, minimalegl, vkkhrdisplay.

Aborted (core dumped)
```

An `apt` search for the two packages shows one of them available-
```bash
$ apt search xcb-cursor0 libxcb-cursor0
Sorting... Done
Full Text Search... Done
libxcb-cursor0/jammy 0.1.1-4ubuntu1 amd64
  utility libraries for X C Binding -- cursor
```

Installing that library was the last requirement needed to get the app running on that system-
```bash
(venv) you@localhost $ sudo apt install libxcb-cursor0
[sudo] password for you: 
Reading package lists... Done
...
Preparing to unpack .../libxcb-cursor0_0.1.1-4ubuntu1_amd64.deb ...
Unpacking libxcb-cursor0:amd64 (0.1.1-4ubuntu1) ...
Setting up libxcb-cursor0:amd64 (0.1.1-4ubuntu1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
```

You may encounter errors about additional dependencies and requirements, such as installing the QT libraries and runtime system.


### Usage

To run the program, after having completed setup, you can simply execute it from a shell-
```bash
(venv) you@localhost $ ./Video-Download.py
```

URL list can either be a text file (.txt) with a list of URLs (lines beginning
with # are ignored) or an HTML file (.html) of bookmarks exported from a browser.
Google "`export bookmarks <browser>`" for detail on how to export bookmarks from
your browser. Most browsers except for Safari (thanks Apple) use a common HTML
file format so unlisted browsers are likely to be supported.  

Tested with browsers:  
. Brave (Windows)  
. Chrome (Windows)  
. DuckDuckGo (Windows)  
. Edge (Windows)  
. Firefox (Windows)  
. Opera (Windows)  
. Safari (MacOS)  
. Vivaldi (Windows)  

### Notes

All settings in the GUI are stored between executions including the window size.  
