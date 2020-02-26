# Linux Kernel Config for Deepin Linux
The config file for compiling kernel 5.x on deepin
## What is this?
Just a config file for compiling kernel 5.x on deepin ,a popular linux GNU version in China.
## What should I do?
Download the file named `.config` in this repository, and put it in the root directory of your kernel source code, finally, start compiling normally.
## How to compile a Linux Kernel?
It is not easy for a beginner to try to compile a Linux Kernel. What I suggest is that you should at least know how to use Terminal. Then, do these things:  
- Prepare at least 25 GB space for compiling source code.
- Download Kernel source tarball from [kernel.org](https://kernel.org).
- Extract Kernel source code files using an uncompress software.
- Enter the directory where you extract source files, it should contain these files:`Makefiles`,`COPYING`,`README` and so on. It is also the root directory of kernel source code.
- Download the `.config` file from this repository, put it in the directory I mentioned before.
- Execute this command in Terminal: `sudo apt install build-essential libncurses5-dev fakeroot`.
- After done everything above successfully, execute `make deb-pkg LOCALVERSION=-custom KDEB_PKGVERSION=$(make kernelversion)-1` in Terminal and wait until it stop automatically and return to terminal prompt. It will take a long time, I spent about 3 hours on it.
- Go to the parent directory of the source code's root directory, and you may find some new files, which contains four `.deb` files, their name begin with 'linux-', two compressed files in `.gz` format, and three text files.
- Copy or move these `.deb` files to a new empty directory, execute `sudo dpkg -i *.deb` in that directory and wait until installed successfully. You may find some errors during installation, don't worry, just go ahead.
- Restart, in the boot menu, choose the second option, you will find three new options contains word `custom`, choose the first one of these options (no `systemd` or `recovery` in it name).
- Wait until your system shows you login screen, login normally, execute `uname -a` in the terminal and you will find your new kernel was loaded successfully.  
## I don't want to compile a custom kernel, but I want to try any new features of a new kernel, what should I do?
Go to ubuntu ppa source ([here](https://kernel.ubuntu.com/~kernel-ppa/mainline/)), download kernel which you need, install these `.deb` files you have downloaded and restart system, then, you can find new kernel in boot menu like you install your custom version from here. For most people, I suggest choosing the 'generic' kernel version. You can google `the difference between lowlatency and generic` to find more.

**Note:**  
- Backup your files before installing kernel!!! It may break your system and you will spend more enegy on fixing it.
- If you want to uninstall this kernel, just remove them as normal software packages. Of course, before removing, you should reboot system to another kernel such as kernel version 4.15 in your original system.
- Forget about my poor English, it is a little inconvenient for a non-English speaker to write this file.
