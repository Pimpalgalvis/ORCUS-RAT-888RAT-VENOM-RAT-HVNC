# ORCUS-RAT-888RAT-VENOM-RAT-HVNC
-----------------------------------------

ORCUS:

![OIP](https://user-images.githubusercontent.com/120501530/207944675-b0138e72-a0b3-432a-9196-42ec936a0d61.jpg)


-----------------------------------------

C# RAT with lots of features.
If you were searching for the perfect RAT, I have a good message for you: Congratulation, you found it. Schnorchel is the perfect RAT for everyone. It provides all standard features like Registry Editor, Webcam, Remote Desktop,... (a full list of all features is linked below).

But what makes it special? We implemented lots of features which make it unique and easy to use. With one of the best GUI framework, WPF, the GUI is really clean and just beautiful. Remote Desktop and webcam are rendered with Direct X for the maximum frame rate. For developers, we implemented a plugin system (plugins can be written in vb.net, C# and C++). With an exception view, you can see what goes wrong with the Client. With a patcher, you can add and remove plugins, change settings or just update the client. If you build the Client with a service, it will install a Windows service on the victims System. The service can do lots of operations which need administrator privileges, for example change the registry or trigger a bluescreen.

One of our goals is to make everything as fast as possible. To reach that, we use a lot of tricks. To reduce the size of the packages to a minimum, we use the zero-overhead-princip. Every Byte counts. Most of the time, we dont use serialisation, we just send plain bytes and interpret them on the other side. But If we really need serialisation, we use a really good serializer, NetSerializer. It is one of the fastest and only outputs what is really necessary. If we need to send large data, we use a fast compression algorithm, QuickLZ. For sure we use a small video codec for the webcam and remote desktop. To gurantee a really good performance for the server, we use a smart way of receiving packages - the server was successfully tested with 10000 clients.

The server is an extra application. For sure, you can run it on the same system like the attacker client, but we also wrote one which will execute on linux systems, for example on a raspberry pi. To successfully execute it, you need to install the mono runtime.

All attacker clients are perfectly synchronized. If one changes for example the group of a client, all other will see the change in realtime. The server will store all data in a SQL database. Key logs, passwords and computer information of a client will also be saved there.

The fun aspect is not missing at all. Beside the standard features like hiding the clock or taskbar, blocking keyboard and mouse or trigger a real bluescreen, we were also creative and implemented things like changing the playback and Mikrophone volume, a very cool combo which will the User make crazy and playing audios like a Skype call or Steam message to fool the user.

Error handling is a really important aspect of every RAT. Because of really clean and OOP coding, the possible exceptions are reduced to a minimum. Almost every action will be executed in a seperate thread - if something goes wrong, it wont take down the application. In this case, a message with the status fatal will be send to the attacker and an exception report will be send to the server. In the worst case scenario, if an unhandled exception occurres, nothing will be lost. With a global event, every unhandled exception will be caught, create an error report and make a safe restart of the client application.

Just take a look at the complete feature list:
# Main
## Build
- Set the group
- Generate a mutex
- Enable/Disable the keylogger
- Change the requested privileges as you like:
  - Always request administrator rights (the builder will change the manifest)
  - Just request at installation
  - Just request if installed
- Set the connection details (ip, port, reconnect delay)
- Define if it should start if attached to a debugger or executed in a virtual machine
- Define it it should try to connect to the server even if a tcp analyzer is running
- Define installation behavior
  - Installation location (supports system variables)
  - Hide the file
  - Modify the creation date
  - Hidden autostart
  - Install service
- Change assembly information
- Select plugins which should be added (BSoD protection for example)
- Select plugins which should modify the build result (File Pumper for example)
- Select an icon

![Preview1](http://fs5.directupload.net/images/151115/yhmycmx9.png)
![Preview2](http://fs5.directupload.net/images/151115/d86sv674.png)
![Preview3](http://fs5.directupload.net/images/151115/jbxvgted.png)

## Power mode
- The Power-Mode is made for a large amount of clients. The default client list will be replaced by a more suitable in order to guarantee an almost lag free environment. Also, data virtualization will be activated to only download information about visible clients (tested with 10,000 clients)
- Power mode is automatically activated if more than 200 clients are connected to the server (you can disable or always enable it in the settings)

![Preview](http://fs5.directupload.net/images/151115/dxtbgbpk.png)

## Android App
I wrote a beautiful Android app which can connect to the server like the administration. For example, if you want to shut down your laughing brother at 9 am on sunday, just shut him down with your smartphone

## Service
The client can install a Windows service which can execute some commands that require administrator privileges, for example trigger a bluescreen, make changes in the registry or change the host file 

# Commands
## Client
**Control**
- Uninstall
- Kill
- Make admin
- Patch
- Replace (upload a file, uninstall the client and execute the downloaded file)

![Preview](http://fs5.directupload.net/images/151115/3eqfqert.png)

**Config**
- View all settings

![Preview](http://fs5.directupload.net/images/151115/4sxbnhmr.png)

**Plugins**
- View all installed plugins

![Preview](http://fs5.directupload.net/images/151115/nveots3w.png)

## Information
**Active Connections**
- View all UDP and TCP connections

![Preview](http://fs5.directupload.net/images/151115/fojuzbex.png)

**Computer**
- Collects lots of information about the target system
- System (OS, system directory, username, user domain name, processor count, drives, system page size, CLR version, admin password status, dns host name, manufacturer, total physical memory, system type, model, up time, status)
- Hardware
  - Processor (architecture, id, type, name, max clock speed, description, status)
  - Video Card (name, device id, video mode description, video processor, max refresh rate, video architecture, video memory type)
  - Screens (resolution, primary?, bits per pixel, device name)
- Software
  - Installed anti virus programs
  - Firewalls
- Location (city, country, ISP, organization, region, timezone, zip code)

![Preview](http://fs5.directupload.net/images/151115/uph27c5y.png)

**Performance**
- Performance graphs for CPU, Memory and Ethernet
- Windows 10 task manager design

![Preview](http://fs5.directupload.net/images/151115/9fbonkos.png)

**Passwords**
- Finds cookies for Chrome and Firefox
- Finds passwords for Chrome, Firefox, Internet Explorer, Opera, Yandex, CoreFTP, Pidgin, FileZilla, Thunderbird, WinSCP, JDownloader 2.0
- Custom export format

![Preview](http://fs5.directupload.net/images/151115/8mhbrmif.png)

## Fun
**Audio**
- 26 cool sounds (Skype call, Steam message, horror sounds)
- With plugins extendable
- Set playback device and volume

![Preview](http://fs5.directupload.net/images/151115/55t2ihcz.png)

**Common**
- Show/Hide taskbar
- Show/Hide desktop
- Show/Hide clock
- Swap/Restore mouse
- Enable/Disable task manager
- Block user input
- Hold mouse
- Open website in standard browser
- Change desktop wallpaper
- Turn monitor off
- Trigger bluescreen
- Shutdown/Log off/Restart
- Rotate monitor
- Hang system
- [This](http://9gag.com/gag/aLQOvg6) 100 % automatically
- Change keyboard layout (QWERTZ, QWERTY, AZERTY)

![Preview](http://fs5.directupload.net/images/151115/rrvkotia.png)

**MessageBox**
- Design a message box and open it

![Preview](http://fs5.directupload.net/images/151115/t8gmq35b.png)

**Volume Control**
- Change master volume of all playback and recording devices
- Change the volume of the channels

![Preview](http://fs5.directupload.net/images/151115/5vvpplr2.png)

## System
**Code**
- Write code in C# and execute it
- Detects errors

![Preview](http://fs5.directupload.net/images/151115/oxg2wk3y.png)

**Console**
- Open/Close a Windows Command (CMD)

![Preview](http://fs5.directupload.net/images/151115/kxcq3bdt.png)

**Event Log**
- Get the event log
- Supports system, application and security event log

![Preview](http://fs5.directupload.net/images/151115/7rojzgv2.png)

**File Explorer**
- Download file/directory (multiple files can be downloaded at the same time)
- Rename file/directory
- Remove file/directory
- Create file/directory
- Execute file
- Upload file

![Preview](http://fs5.directupload.net/images/151115/fbg67uw3.png)

**Hosts File**
- Read/Write the Windows hosts file (to disable or redirect hostnames)

![Preview](http://fs5.directupload.net/images/151115/negedclp.png)

**Internet**
- Download & execute from an url
- Mass download (to slow down the internet speed)

![Preview](http://fs5.directupload.net/images/151115/3yhuhmuq.png)

**Programs**
- List all installed programs
- Start the uninstaller

![Preview](http://fs5.directupload.net/images/151115/dp65e9fn.png) 

**Registry**
- Edit registry (feels exactly like regedit)

![Preview](http://fs5.directupload.net/images/151115/kziu92hx.png)

**Reverse Proxy**
- You can access the client's internet with every SOCKS5 compatible application (Firefox, Chrome, ...)

![Preview](http://fs5.directupload.net/images/151115/ysnx4w8d.png) 

**Task-Manager**
- List and search all open processes
- Kill processes
- Change priority

![Preview](http://fs5.directupload.net/images/151115/uefm9tyj.png)

## Spy
**Keylogger**
- View the key logs
- Formatted keylogs for the best overview

![Preview](http://fs5.directupload.net/images/151117/7hugwsxn.png) 

**Screen**
- Take a screenshot from the remote system
- See the other side live and control keyboard & mouse
- Open in a new window to use the other commands at the same time

![Preview](http://fs5.directupload.net/images/151115/kjh9zc3k.png) 
![Preview](http://fs5.directupload.net/images/151115/tpqvesmi.png)

**Webcam**
- Live webcam
- Maximum FPS because of rendering with Direct X
- Fast video codec
- Set the resolution and quality to improve performance

![Preview](http://fs5.directupload.net/images/151117/pamksqmx.png)

# Other
**DDoS**
- Comfortable manager
  - You can stop attacks on targets or clients
- HTTP, UDP, ICMP, SYN are supported

![Preview](http://fs5.directupload.net/images/151121/kr8sk6cz.png)

**Exceptions**

If something goes wrong with a client, it will send an error report to the server
- Select the range when the exceptions occurred
- View the exceptions details: Timestamp, Exception Type, Status, Message, Client Version and Stack Trace
- View environment information: Total Memory, Available Memory, Process Memory, Operating System, Architecture, Process Type, Runtime Version, Administrator privileges, service status, path
- A ready-for-copy report is available if you want to send it to the developer

![Preview](http://fs5.directupload.net/images/151115/bauzeq9n.png)

**Map**
- A world map which shows the position of all clients (blue screen: online, red screen: offline)

![Preview](http://fs5.directupload.net/images/151115/3vf4tlmk.png)

**Statistics**
- Pie charts
- Categories: Clients (online/offline), operating system, privileges, language

![Preview](http://fs5.directupload.net/images/151115/mabdrgr9.png)

# Server
The server is an extra program. There are two different assemblys available: One with a GUI for Windows and the other one is a command line application which can be executed on linux systems.
Both have build-in support for No-Ip. The connection is encrypted with SSL.

# Facts
**Client**

| Name  | Value |
| ------------- | ------------- |
| Size  | ca. 500 kb  |
| Supported .Net Framework Versions  | 3.5, 4.0, 4.5  |
| Supported Operating Systems  | Windows 10, 8.1, 8, 7, Vista, XP  |
| Protocol  | TCP  |

**Server**

| Name  | Value |
| ------------- | ------------- |
| Maximum Clients  | 2147483648 (2^31)  |
| Maximum Attackers | 65536 (2^16)  |
| Database  | SQLite  |
| Certificate  | X.509 SSL  |

**Administration**

| Name  | Value |
| ------------- | ------------- |
| .Net Framework Version  | 4.5  |
| Languages  | German & English  |
| Supported Operating Systems  | Windows 10, 8.1, 8, 7  |

-----------------------------------------------------------------

VENOMRAT_HVNC

![mZmBIZc](https://user-images.githubusercontent.com/120501530/207944547-82904d58-7c13-4cef-8c71-5fc1f43b9808.png)


-----------------------------------------------------------------

A quality remote administration tool was the top request we had from our macro exploit users, and that’s how Venom Software was born. There’s no easier way to spread your exploit in any environment, and take advantage of remote file management & registry / command access.

Monitor on/off
Icon
Open/close CD
Icon
Show/Hide Taskbar
Icon
Show/Hide Start Button
Icon
Show/Hide Explorer
Icon
Show/Hide Clock
Icon
Show/Hide Tray
Icon
Show/Hide Mouse
Icon
Enable/Disable TaskMgr
Icon
Enable/Disable Regedit
Icon
Disable UAC
Icon
Remove Scheduler
Icon
Token Discord Recovery
Icon
Client Update
Icon
Password Recovery
Icon
Passwords.JSON/ History.JSON/ Autofill.JSON/ bookmarks.JSON/ cookies.JSON
Icon
Much more...
Icon
Icon
REMOTE FUN
Logo
Icon
System information
Icon
File Manager
Icon
Start Up Manager
Icon
Task Manager
Icon
Remote Shell
Icon
TCP Connection
Icon
Reverse Proxy
Icon
Registry Editor
Icon
UAC Exploit
Icon
Disbale WD
Icon
Mic Record
Icon
Download/execute to disk/memory
Icon
Thumbnail
Icon
Active Scheduler
Icon
Auto Password Recovery Stealer: Passwords/ History/ Autofill/ bookmarks/ cookies
Icon
MUCH MORE..
**STUB:**

Icon
Change client name
Icon
Enable install
Icon
USB spread
Icon
Anti kill
Icon
Enable key logger Offline/online
Icon
CHANGE LOG DIRECTOY NAME
Icon
Mutex
Icon
Disable defender
Icon
Hide file
Icon
Hide folder
Icon
Start up/persistence
Icon
Change client name
Icon
Change reconnect time
Icon
Change icon
Icon
Encrypted connection
Icon
Change assembly CLONE
Icon
Export as ShellCode
Icon
Hide keylogger folder
Icon
IP/DNS/No ip
Icon
Enable keylogger
Icon
Much more...

-----------------------------------------------------------------

888RAT

-----------------------------------------------------------------

![Screenshot_10](https://user-images.githubusercontent.com/120501530/207944194-d930f170-350c-4ce9-bcbe-da58ab863515.png)

![1](https://user-images.githubusercontent.com/120501530/207944860-7ea62be6-8f4d-4d71-adaf-08e165e9a83c.png)

![2](https://user-images.githubusercontent.com/120501530/207944882-0c84bb7d-5b8a-4e09-8a75-bc785953cc66.png)

![3](https://user-images.githubusercontent.com/120501530/207944911-c02e8571-9dbf-439e-85b1-730bf23a1540.png)

--------------------------------------------------------------



