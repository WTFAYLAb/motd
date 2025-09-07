# MOTD "Message of the Day"
A collection of beautiful and useful 'Message of the Day' scripts.

### How do I set it up?
* Copy the files you want in your MOTD to `/opt/etc/update-motd.d/`.
* Add the following to your `~/.zshrc`:
```bash
## MOTD
run-parts /opt/etc/update-motd.d
```
### Customize your MOTD
Adding your own MOTD is as easy as placing an executable script in `/opt/etc/update-motd.d`. The filename must be formatted as: **Two digits, hyphen, unique name**. Example:
```console
20-uptime
```
#### Rules
* Files can not contain an extension (e.g.: `.sh`, `.py`)
* The file can be *any* executable type your system is capable of running, usually defined by the she bang (`#!`) on the first line
* Scripts will execute in numerical order

To make a MOTD script executable: 
```console
chmod +x /etc/update-motd.d/{{nn-SCRIPT-NAME}}
```
