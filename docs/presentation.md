title: Linux 101
subtitle: ... for .NET Devs
class: animation-fade
layout: true

<!-- This slide will serve as the base layout for all your slides -->

.bottom-bar[
{{title}}
]

---

class: impact

# {{title}}

## {{subtitle}}

.title-oli[
Oliver Sturm &bull; @olivers &bull; oliver@oliversturm.com
]

.title-logo[
<img src="template/devexpress.png" id="devexpress" alt="DevExpress"><img src="template/mvp.png" id="mvp" alt="MVP">
]

---

## Oliver Sturm

* Training Director at DevExpress
* Consultant, trainer, author, software architect and developer for over 25 years
* Microsoft C# MVP

* Contact: oliver@oliversturm.com

---

## Agenda

* That Linux Thing
* Getting Started with Linux
  * Shells, Command Lines and Commands
  * File Systems and Permissions
  * Users and Processes
  * Editing and Configuring
  * Packages
* Creating a .NET Core App
* Setting Up a Runtime Environment

---

## On Day 1...

```text
From: Linus Benedict Torvalds
Date: August 25 1991
Subject: What would you like to see most in minix?

Hello everybody out there using minix -

I'm doing a (free) operating system (just a hobby, won't be big and
professional like gnu) for 386(486) AT clones. ...

PS. ... It is NOT protable (uses 386 task switching etc), and it
probably never will support anything other than AT-harddisks, as
that's all I have :-(.
```

Full thread: http://osturm.me/torvalds-linux-announcement

--

.overlay[.overlay-content[

# By the Way

Linus doesn't mention it, but his new OS was going to be called _Freax_ at this point.
]]

---

## On Day 9658 (Feb 1st 2018)...

* 37-67% of _Web Servers_ run Linux (April 2017).<br>On the top 1,000,000 domains, it's 96%.
* Since November 2017, _all 500 fastest super-computers_ (TOP500 project) run Linux
* IBM runs Linux on _Mainframes_ (System z), marketshare ~28% (December 2008)
* 70% of _Mobile Devices_ run Linux (Android, December 2017)
* 29% of _Embedded Devices_ run Linux (Android and others, March 2012)

--

In all those groups there are large percentages of other Unix-like systems that are not Linux (macOS, iOS, BSD, PlayStation, QNX...)

--

And finally:

* 2% of _Desktop and Laptop machines_ run Linux (December 2017)

---

## Amazing Scale and Diversity

* ~30 supported Processor Platforms
* An individual kernel release has > 1000 contributors, ~10000 patches, changing ~3500 lines of code per day.
* Latest kernels have > 20M lines of code. Also several hundred swear words. :)

--

This is not from the Linux kernel, but funny anyway :)

```text
// you can't fix this, but please increment the counter
// below if you try.
// hours wasted here: 56
```

---

## So what have we got?

* Linux is the _kernel_, though the project also includes _drivers_, _filesystems_ and other components
* Other parties maintain drivers, _system components_ and _application software_
  * Independent system components: _shell tools_, _graphical display servers_, _package management_, ...
* Yet others create _distributions_, with _installers_, _releases_, _updates_ and _support lifecycles_
  * Some distributions offer _commercial SLAs_
* Sometimes Linux is _integrated_ elsewhere, for instance in embedded systems, or in Windows
* Sometimes Linux is _derived from_, e.g. with Android

---

## As a .NET Dev, why should I give a \_?

* It's a _great deployment platform_

  * Fast
  * Performant
  * Scaleable
  * Free of license cost

* It's an _enthusiast/advanced user platform_

* It's small. It's big. It's stable. It boots fast. It's consistent. It's versatile. It's standardized. It's customizable.

--

* _It's a platform that does exactly what .eem[I] want._

---

## Getting Started

* Get a _distribution_ and install!
  * My recommendation: Ubuntu (https://www.ubuntu.com/download/desktop)
  * Use a VM if you lack spare machines :)
* Start up a Linux _virtual machine in the Cloud_ and connect via SSH
  * Details on SSH in a moment
* Use the _Windows Subsystem for Linux_
  * Activate "Developer Mode" and Windows 10 / Windows Server optional feature
  * Run `bash.exe` to install Ubuntu
  * Alternatively, get other distro installers from the Microsoft Store
  * `lxrun /uninstall [/full]` gets rid of your bungled installation :)
  * Might have to `lxrun /setdefaultuser ...` or `ubuntu config --default-user ...`

---

## The UI

```linuxprompt
linux:~$
```

---

## The UI &mdash; Graphical Desktop Environments

* Gnome, KDE, Xfce, MATE, LXDE, Budgie, (Unity) ...

  * Almost endless list
  * Usually focused around a Window Manager and a design and usage philosophy
  * Often associated with a library for graphical output and system functionality (Qt, GTK)

* "Independent" Window Managers
  * Personal preference: i3

--

* In many environments where you encounter Linux, you won't have a graphical UI!

---

## The Shell

* Again, choices: bash, zsh, fish, ksh, tcsh, ...
* Personal preference: zsh with oh-my-zsh extensions
* Shells have several jobs:
  * Command line editing
  * Prompting
  * Execution of commands
  * Job management
  * Automation

---

class: impact

# Let's Check It Out!

---

## The Docs

Documentation at your fingertips, since 1971.

```shell
man man
```

---

## Remote Shells

* Command: `ssh`, for *s*ecure *sh*ell
* Connects securely to a remote system and executes a shell there
* Don't use password authentication! &mdash; Public key preferred.
* Advanced features: SSH Agent, agent forwarding, port forwarding ...
* Associated: scp
* Recommendation: check out `tmux` or `screen` for multi-pane terminal layouts
  * `tmux`, `tmux ls` `tmux attach` to work with sessions
  * `C-b d` to detach, `C-b %` and `C-b "` to create panes, `C-b right/left/up/down` to navigate
  * Reconfigure as needed!

---

## Commands

* Shell built-ins
  * `alias`, `fg`, `cd`, `echo`, `set`, ...
* System commands in `/bin`, `/usr/bin` etc.
  * `ls`, `cp`, `mv`, `rm`, `cat`, `find`, `grep`, `less`, `ps` ...
  * On my system:

```text
linux:~$ ls -l /bin | wc -l
167
linux:~$ ls -l /usr/bin | wc -l
3432
```

---

## Command Line Features

* Aliasing: `alias`
* Completion with TAB: commands/aliases, files (wildcards &mdash; globbing)
  * Extensible completion in zsh (and others, but not so good!)
* Ctrl-R to search history
* Jobs: Ctrl-Z to suspend foreground process. `bg` (background), `fg` (foreground), `jobs`

---

## Shell Features

* Wildcards: `*`, `**`, `?`, `[123]`, `(txt|png)`
  * Zsh extensions: `*(/)`, `*(@)`, `*(.)`
* Piping: `echo Cool thing | grep ool`
* Redirection: `grep wow /proc/* > output 2>&1`
  * `echo More content >> existingFile`
  * `cat < in > out`
* Here Documents: `cat > output <<END`
* Substitution: <code>ls -l &#96;which cat&#96;</code>
  * Or longer: `ls -l $(which cat)`

---

## Working with the File System

.col-6[

* Everything is part of `/` (root)
* List: `ls`
  * Files starting with `.` are invisible, show with `ls -a`
* Directories: `mkdir`, `rmdir`, `cd`
* File operations: `cp`, `mv`, `rm`
* Create or update timestamp: `touch`
* Show file content: `cat`, `less`
* Detect file type: `file`

]

.col-6[

* Link: `ln`
* Mount: `mount`
* Space allocation: `df`, `du`
* Find files and more: `find`

* File names are _case-sensitive_!

]

---

## Permissions

```shell
linux:~$ ls -l /bin/ls
```

.svg-width[
![Permissions](permissions.svg)
]

---

## Manipulating Permissions

* `chown` changes owning user, `chgrp` changes owning group
* `chmod` changes permissions
  * `chmod u+x` adds `x` for owning user
  * `chmod +w` adds `w` everywhere
  * `chmod 755` sets `rwxr-xr-x`
* Directories need `x` so a user can "enter" them!

---

## User Management

* `whoami`
* `adduser` and `addgroup` create users and groups, set default shells and copy template home directories
* `usermod` modifies a user record
* `chsh` sets a user's shell
* Check `/etc/passwd` and `/etc/group` when in doubt

* `sudo` executes commands with root permissions
  * `sudo -s` gives you a root shell, but use with great caution!
  * The only known command to insult you if you want it to... google it! :)

---

## Processes

* `ps` shows processes
  * Modern `ps` confusingly supports various option sets
  * `ps aux` and `ps -ef` show all processes, incl. lots of detail
* `top` or `htop` for prettier output and interactive features
* `kill` sends a signal to a process, `kill -l` to see signal names
  * `kill -9` is a "hard kill"
  * `skill` tries to find the process by its name

---

## Editing Text Files

* `nano` for the ~~whimps~~ novices
  * Seriously: simple, easy to use text-based UI, recommended for first-time Linuxers
* `vi` for traditionalists
  * Very powerful, cryptic for first-time users
* `emacs` for the cool kids
  * An OS in its own right, everything-but-the-kitchensink application. Requires practice to use in text-based environments.

---

## Configuring Things

* `/etc` is the place for system config files
  * Editing them requires `sudo`
  * It can also break your system!
  * Services may need to be restarted or instructed to reload config files, once changes have been made.
* _dot files_ start with `.` (invisible, remember?) and mostly live in user home directories
  * Often they override the system-wide configuration of an application
* Many UI applications use files in `~/.config` these days

---

## Package Management

* Package Management system depends on your distribution
  * `dpkg`, `apt`, `aptitude` on Debian/Ubuntu systems
  * `rpm` on Red Hat and derived systems
  * `yum`, `dnf`, `pacman`, `emerge`, `zypper` ...
* For Ubuntu:
  * `sudo apt update` loads newest package lists
  * `sudo apt upgrade` installs available upgrades
  * `sudo apt install` and `sudo apt remove` &mdash; guess what :)
  * `do-release-upgrade` for automated upgrade to new major release versions
  * Config files in `/etc/apt`
* New: "snaps" are universal packages &mdash; https://www.ubuntu.com/desktop/snappy

---

## Shutting Down and other System Level Stuff

* `sudo reboot` to &mdash; ahem &mdash; reboot
* `sudo shutdown` shuts done. Duh.

Some advanced items to check out:

* `lsblk` shows connected block devices (hard drives etc.)
* `lsusb` shows USB devices
* `dmesg` shows kernel messages
* `fdisk` partitions hard drives
* In `/var/log` you can find detailed system logs
* `/boot` has files for the `grub` boot loader, and other startup items
* Learn about the `/dev` and `/proc` directories for system-level insight

---

## Building a .NET Core App &mdash; Installing .NET Core

From https://www.microsoft.com/net/learn/get-started/linuxubuntu -

* Get Microsoft's package signature key (two lines):

```text
curl https://packages.microsoft.com/keys/microsoft.asc |
       gpg --dearmor > microsoft.gpg
sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
```

* Register Microsoft's .NET Core apt package source (one line):

```text
sudo sh -c 'echo "deb [arch=amd64]
  https://packages.microsoft.com/repos/microsoft-ubuntu-artful-prod
  artful main" > /etc/apt/sources.list.d/dotnetdev.list'
```

---

## Building a .NET Core app &mdash; Installing .NET Core (cont.)

This is what Microsoft shows on the web page:

```text
*sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-2.1.4
```

The highlighted line may be required in certain "limited functionality" environments, but not on normally installed workplace machines.

---

## Building a .NET Core app &mdash; Installing VS Code

From https://code.visualstudio.com/docs/setup/linux :

* Get Microsoft's package signature key &mdash; you have already done this
* Register the VS Code apt package source (one line):

```text
sudo sh -c 'echo "deb [arch=amd64]
  https://packages.microsoft.com/repos/vscode stable main" >
  /etc/apt/sources.list.d/vscode.list'
```

* And install:

```text
sudo apt update
sudo apt install code
```

---

## Creating a .NET Core MVC App

Simples!

```text
mkdir olisapp
cd olisapp
dotnet new mvc
dotnet run
```

---

## Deployment Considerations

* Physical deployment
  * `dotnet publish`
  * Copy to `/usr/local/APPNAME` &mdash; recommended location!
* Running the app in Kestrel is easy and fast
  * The standard template call `CreateDefaultBuilder` uses Kestrel
* However, Microsoft recommends against running Kestrel as a public front-end server
* Use a reverse proxy!
  * Recommendation: nginx
  * Apache or IIS (or others) also possible

- Plan: Configure Kestrel and nginx for automatic startup of the web app.

---

## Setting Up nginx

```text
sudo apt install nginx
cd /etc/nginx
sudo vi sites-available/demoapp
sudo ln -s sites-available/demoapp sites-enabled/
sudo nginx -s reload
```

demoapp config:

```text
server {
  listen 80;
  location / {
    proxy_pass http://localhost:5000;
  }
}
```

--

.overlay[.overlay-content[

# Watch Out

In the nginx default setup, there may be a server configuration listening on port 80 already. If so, you can deactivate it by removing the symbolic link:

```text
sudo rm /etc/nginx/sites-enabled/default
```

]]

--

.overlay[.overlay-content[

# Note that this Setup is not Complete!

Microsoft has full instructions for nginx (and others) here:

https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/linux-nginx?tabs=aspnetcore2x

]]

---

## Auto-Starting Kestrel

```text
sudo vi /etc/systemd/system/demoapp.service
sudo systemctl enable demoapp
sudo systemctl start demoapp
```

---

## Auto-Starting Kestrel &mdash; demoapp.service

```ini
[Unit]
Description=Demo App

[Service]
WorkingDirectory=PROJECTDIR
ExecStart=/usr/bin/dotnet PROJECTDIR/.../demoapp.dll
Restart=always
RestartSec=10
SyslogIdentifier=demoapp
User=www-data
Environment=DOTNET_PRINT_TELEMETRY_MESSAGE=false

[Install]
WantedBy=multi-user.target
```

--

.overlay[.overlay-content[

# There's More to Say

Like before, this setup is not the end of the story. Find Microsoft's full instructions here:

https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/linux-nginx?tabs=aspnetcore2x

]]

---

## Sources

* This presentation:

  * https://oliversturm.github.io/linux-101-for-dotnet-devs
  * PDF download: https://oliversturm.github.io/linux-101-for-dotnet-devs/slides.pdf

---

class: impact

# Thank You

Please feel free to contact me about the content anytime.

.title-oli[
Oliver Sturm &bull; @olivers &bull; oliver@oliversturm.com
]

.title-logo[
<img src="template/devexpress.png" id="devexpress" alt="DevExpress"><img src="template/mvp.png" id="mvp" alt="MVP">
]
