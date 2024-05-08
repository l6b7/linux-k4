# My system backup and arch linux installer

main features

arch linux
I use it because it's suprisingly stable especially if you avoid python (but it's python's own fault)
arch user repository has pre compiled programs that rarely are in a form of binaries in other distros


dwm
this is what runs on top of graphical server
that actually manages application windows as well as status bar
status bar is extended with dwmblocks for interactive clickable
modules / indicators such as internet traffic, volume, time date and more


dmenu
application launcher that also servers as a launcher for custom menus
I usually use it to launch custom scripts eg exit menu (reboot shutdown...)
or to quickly manage multiple display (duplicate screen, extend screens...)

st zsh
st is a terminal emulator that only has the bare minimum that you would want
from a emulator
zsh is where the magic happens like auto-complete or syntax highlighting

lf
is a terminal file manager that again has almost no basic functionality
whatsoever out of the box yet it's easy to patch and configure to work
better than any graphical one which how fluid it is to move through dirs
because the program doesn't make it hard for you to program your own
functionality I can use scripts and basic shell commands to get exactly what I want.
One of the examples might be archivising and compressing files / directories can be done with 2 buttons
as well and decompressing / unarchivising them automatically with programs fit to it
(unrar will take care of .rar files and bzip2 zip files respectively)

mpv 
mpv is my media player of choice
Since I couldn't find any good audio player and image viewer i just patched it
to have the bare minimum of what I would need for such application.
The point being is that whenever I want to edit such files I already have programs
that are more powerfull than enough to do so but I wouldn't want to use them
for a basic preview whenever I browse these files in my file manager.

vim
vim or it's fork neovim is my text editor of choice for when I want to edit 
code in a programming language I have no interest in learning
I won't talk much about this I will just say that an easy access to regular expression
whenever editting basic text files and plethera of commands it offers.
It just works slightly worse than ide but it's functionality isn't tied to 
a programming language.

The occuring theme of my setup is that everything plays with each other well
as well as everything being simple and small enough that I can either
develop a feature that I need or look for another program when the problem
is beyond my skills.

If anyone would want to use this setup I recommend starting from config file
that is used by the installer and env_vars in config/zsh as there are used to
quickly change system env variables

anything else as always in linux should be in config files
so starting with another gnu/linux distribution and using my config for eq mpv
is a good way to not be overwhelmed
This being said replacing core programs that I use should also be easy and shouldn't break anything

The last but not least is the topic of keyboard shortcuts
tiling window managers relly a lot on keyboard shortcuts because
they try to limit on how often you would require the use of the mouse
and most of my programs have intuitive shortcuts again usually stored in config files

