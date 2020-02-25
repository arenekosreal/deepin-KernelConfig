# Linux Kernel Config for Deepin Linux
The config file for compiling kernel 5.x on deepin
## What is this?
Just a config file for compiling kernel 5.x on deepin ,a popular linux GNU version in China.
## What should I do?
Download the file named `.config` ,and put it in the root directory of your kernel source code, finally, start compiling normally.
## How to compile a Linux Kernel?
It is not easy for a beginner to try to compile a Linux Kernel. What I suggest is that you should at least know how to use Terminal. Then, do these things:  
- Download Kernel source tarball from [kernel.org](https://kernel.org)
- Extract Kernel source code files using an uncompress software
- Enter the directory where you extract source files, it should has these files:`Makefiles`,`COPYING`,`README` and so on.
- Download the `.config` file from this repository, put it in the directory I mentioned before.
- If you haven't compiled anything before, execute this command in Terminal: `sudo apt install build-essential libncurses5-dev fakeroot`, or ignore this.
- After done everything above successfully, execute `make deb-pkg LOCALVERSION=-custom KDEB_PKGVERSION=$(make kernelversion)-1` in Terminal and wait until it stop automatically. It will take a long time, I spent about 3 hours on it.
- Go to the parent directory and you may find some new files, which contains four `.deb` files, their name begin with 'linux-'.
- Copy or move these files to a new empty directory, execute `sudo dpkg -i *.deb` in that directory and wait until installed successfully. You may find some errors during installation, they doesn't matter, just go ahead.
- Restart, in the boot menu, choose the second option, you will find three new options contains word `custom`, choose the first one of these options.
- Wait until your system shows you login screen, login normally, in the terminal, execute `uname -a` and you will find your kernel was loaded successfully.  

**Note:**  
- Backup your files before installing kernel! It may break your system and you will spend more enegy on fixing it.
- If you want to uninstall this kernel, just remove them as they are normal software packages. Of course, you should reboot system to another kernel such as version 4.15 in your system.
- Forget about my poor English, it is a little inconvenient for a non-English speaker to write this.
