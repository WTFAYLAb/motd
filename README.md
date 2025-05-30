# MOTD "Message of the Day"
A collection of beautiful and useful 'Message of the Day' scripts.

### Requirements
* [update-motd](https://launchpad.net/update-motd)
* [FIGlet](http://www.figlet.org/), [TOIlet](https://linuxcommandlibrary.com/man/toilet), & [lolcat](https://github.com/busyloop/lolcat) (for `10-logo`)

### How do I set it up?
Copy the files you want in your MOTD to `/etc/update-motd.d/`.

### Tips for Using `lolcat` with MOTD
Because the MOTD is built dynamically upon login, `lolcat` requires additional options to display colors and/or non-standard characters such as those that often appear in ASCII art.

* `-f`, `--force`: Force color even when stdout is not a tty (the MOTD is not considered a tty)
* `LANG=en_US.UTF-8`: Use as a prefix in MOTD scripts when including non-standard characters

Examples:

`LANG=en_US.UTF-8 lolcat -f h6lix-logo.txt`

`toilet -f smslant "$(hostname)" | lolcat -f`

### Testing

The `run-parts` command is the easiest way to test the MOTD scripts as it will run all scripts in a directory in alphanumeric order:

	run-parts /etc/update-motd.d

### Customize your MOTD
Adding your own MOTD is as easy as placing an executable script in `/etc/update-motd.d/`. The filename must be formatted as: **Two digits, hyphen, unique name**. Example:

`20-uptime`

#### Rules
* Files can not contain an extension (e.g.: `.sh`, `.py`)
* The file can be *any* executable type your system is capable of running, usually defined by the she bang (`#!`) on the first line
* Scripts will execute in numerical order

To make a MOTD script executable: 

	chmod +x /etc/update-motd.d/{{##-SCRIPT-NAME}}
