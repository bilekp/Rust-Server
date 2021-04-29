# Rust server that runs inside a Docker container

---

**DISCLAIMER:**
```
Cracked or pirated versions of Rust are not supported in any way, shape or form. Please do not post issues regarding these.
```

---

**FEATURES**

       1. Automatic updates on release (Default: Enabled in config)
       2. Auto Wipe on server updates
       3. Login with Stean username and password if required
       4. UPnP support for auto port forwarding when running server (Default: Enabled in config)
       5. MORE YET TO COME



# TUTORIAL:
**If you want to manually install this container you can by these simple steps**

1. Add new container under Docker tab.
2. Give the container a name you prefer.
3. Add ``` bilekp/rust-server ``` in Repository.
4. Add the variables you want from the list below.
5. Add ports to container, (8080/TCP, 28015/TCP&UDP, 28016/TCP).
6. Save Template and RUN :)

**NOTE**: This image will install/update on startup. The path ```/steamcmd/rust``` can be mounted on the host for data persistence.  
Also note that this image provides the new web-based RCON, so you should set ```RUST_RCON_PASSWORD``` to a more secure password.
This image also supports having a modded server (using Oxide), check the ```RUST_OXIDE_ENABLED``` variable below.


The following environment variables are available if you wish to modify the template:
```
PUBLIC - 1 = On, 0 = Off. Will automatically port forward your router. (UPnP)
PVE - 1 = Enabled  (Player Vs Entities), 0 = Disabled (Player Vs Player) 
AUTO - 1 = Yes, 0 = No. Notifies players and automatically updates server/oxide and manages wipes.
WIPEDAYS - Blank = No server wipes, or enter the amount of days until server wipes
WIPE_TITLE - 1 = Enabled, 0 = Disabled. Will show the the server wiped date in the server name. 
OXIDE - 1 = Enabled, 0 = Disable. Be able to install plugins from Oxide. 
PERFORMANCE - 1 = Resource Friendly (Optimized), 2 = Original (Rust Default Settings), 3 = Competitive (Resource Gobbler)
RELEASE - public = (Latest update), prerelease = (Under development)
NAME - Server name.
DESCRIPTION - Server description.
BANNER - Server banner (Banner must be 512x256 PNG)
PLAYERS - Max amount of players that can join the server.
PASSWORD - Rcon Password
ARGUMENTS - Extra Startup Arguments
ANNOUNCE1 - Leave BLANK to disable announcements. 
ANNOUNCE2 - Leave BLANK to disable announcements. 
ANNOUNCE3 - Leave BLANK to disable announcements. 
ANNOUNCE4 - Leave BLANK to disable announcements. 
ANNOUNCE5 - Leave BLANK to disable announcements. 
MAPSIZE - tiny, small, medium, large, massive, or a number between 1000-8000
PORTFORWARD_WEB - Rcon web port
PORTFORWARD_RUST - Rust game port
PORTFORWARD_RCON - Rcon port
MAPSEED - 0 = Random, Or enter your own value
IDENTITY - Server folder name,  e.g My-server-name, server-01 etc
SAVE_INTERVAL - In seconds
ANNOUNCE_DELAY - Delay in minutes between each announcement.

```

# Logging and rotating logs

The image now supports log rotation, and all you need to do to enable it is to remove any `-logfile` arguments from your startup arguments.
Log files will be created under `logs/` with the server identity and the current date and time.
When the server starts up or restarts, it will move old logs to `logs/archive/`.

# How to send or receive command to/from the server

A small application, called *rcon*, that can both send and receive messages to the server, much like the console on the Windows version, but this happens to use RCON (webrcon).
To use it, simply run the following on the host: `docker exec rust-server rcon say Hello World`, substituting *rust-server* for your own container name

# SUPPORT    [Click Here](https://github.com/tobiaspedersen/Rust-Server/issues)

