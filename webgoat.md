# Installing Webgoat in Kali

This installation guide is identical to what I did to set up WebGoat in my environment, and it follows excellent guide by Tero Karvinen found [here](https://terokarvinen.com/2020/install-webgoat-web-pentest-practice-target/). 


First start up your Kali Linux, if you haven't set up one yet you can find instructions for it [here](https://github.com/tonikerttula/APE/blob/main/Kali.md).

Open your terminal and type in (or copy-paste from here) the following command:

> sudo apt-get -y install openjdk-11-jre ufw

This command installs Java and a firewall. You can enable the firewall by running the following command:

> sudo ufw enable

Next you'll need to download WebGoat, it is done by the following command:

> wget https://github.com/WebGoat/WebGoat/releases/download/v8.0.0.M26/webgoat-server-8.0.0.M26.jar

And after download is done, you run the package by the following command:

> java -jar webgoat-server-8.0.0.M26.jar

Now try opening the WebGoat, open your browser and type in the following URL (note that the word "WebGoat" is case sensitive):

- localhost:8080/WebGoat 

![1]

Congratulations! Now create an account and start doing the excercises!

If you want to be safe and unplug your Virtual Machine from the internet (which you should always do if you are not sure how the application interacts with your network, if it creates vulnerabilities for your system or it might access something outside of the target) go to your Virtual Box Manager and select Settings for your Virtual Machine, in the Network tab choose Host-only Adapter (or Not Attached). You can test the internet access by trying to connect to any website with your browser.

![2]

![3]

[1]: https://i.gyazo.com/07df13afaf0b66c167a47b35b89ce8bb.png
[2]: https://i.gyazo.com/8335464ea8a59a1fff10a31cbe57e41e.png
[3]: https://i.gyazo.com/d504c0de0d2faf9f8e19aed69c4ef2f9.png
