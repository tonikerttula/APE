# Hiding Linux Processes

Hiding your processes can be useful for trying to evade detection! It can be done with various tools, but I am remounting /proc filesystem with kernel hardening __hidepid__. This hides the processes from commands such as __ps__, __htop__ and __pgrep__ among others.

Hidepid options work as follows:

![](https://i.gyazo.com/0666075fd503c566787829744ddba6b6.png)

Let's check the current processes running in Kali:

>ps aux

![](https://i.gyazo.com/5f0f60604c4cb183f26b36d863a76a62.png)

Next let's use the following mount command:

> sudo mount -o remount,rw,nosuid,nodev,noexec,relatime,hidepid=2 /proc

Next we need to edit /etc/fstab file

> sudo nano /etc/fstab

Just paste the following line in the file

> proc    /proc    proc    defaults,nosuid,nodev,noexec,relatime,hidepid=2     0     0

Great! Now let's log in as a new user. I created a new user named qwerty

> sudo useradd qwerty

Let's try to see if we see any processes as qwerty:

> ps aux

![](https://i.gyazo.com/32492bae9d6c280aa48a0a37e79ff9c8.png)

The processes that are not owned by the user are hidden!
