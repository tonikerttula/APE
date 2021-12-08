# Installing Metasploitable 2

Metasploitable 2 is purposefully vulnerable machine for practicing breaking into machines. Download it from the link: https://sourceforge.net/projects/metasploitable/

Unzip the zip-file. Now go to Virtual Box Manager and click "New". Choose the following settings, the location for the machine folder you can choose freely.

![1]

Select for memory size at least 1024MB, click Next. For hard disk, choose existing file and choose the file you just downloaded and unzipped

![2]

Now click Create. Congratulations, you have succesfully installed Metasploitable 2. 

Now in the Virtual Box Manager select the Metasploitable 2 machine, click "Settings" and in the "Network" tab select "Attached to:" and select "Host-only adapter" from the dropdown menu. Now you have it running in the Virtual Box internal network. If you have Kali also in the same setting, you can now ping and probe the Metasploitable 2 from the Kali machine!

Metasploitable login: msfadmin and password: msfadmin 







[1]: https://i.gyazo.com/3cb1d782d89439250196b9f9bf2465bd.png
[2]: https://i.gyazo.com/f1bcc50f3c6cef35abdc11bebb680e3f.png
