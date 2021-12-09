# Exercise 1 Solution

This is the solution I used to complete the exercise.

To find the IP-address of the target Metasploitable machine, we can use nmap scan. By using the __-sV__ variable, we also version scan it to find possible vulnerabilities. By using netmask /24 we can scan the whole 192.168.56.XXX address range, and as we know our own Kali's IP to be 192.168.56.102 (you can find it out by using the command __ip a__) and that the target machine is in the same network, the scan should find the target machine also.

> sudo nmap -sV 192.168.56.0/24

![1]

[1]:https://tonikerttula.files.wordpress.com/2021/11/image-67.png

Well it seems like 192.168.56.101 is our Metasploitable. We can also see all the open ports and services running on the ports here, to possibly find vulnerability that we can use tp get access to the machine.

Let's try to brute force our way into the machine. Typing __msfconsole__ into the console will open Metasploit, and typing __search brute force__ we can find modules, that can be used to brute force. However, there will be over one hundred results, so with a quick Google search I decided to use a tool called __ssh auxiliary module: ssh login__. So type into the console __search ssh_login__

![2]

[2]:https://tonikerttula.files.wordpress.com/2021/11/image-61.png

Using the command __info 0__ we can see info about the corresponding module. I can see, that we need to create a USERPASS_FILE, which includes an account username and password, separated by a space. The module will use this file to try to get shell connection to the target. I created a simple textfile, which includes all the services as username and password, also some random combinations that popped in my head in couple of seconds. (Msf is abbreviation for Metasploit Framework)

![3]

[3]:https://tonikerttula.files.wordpress.com/2021/11/image-62.png

You can make these lists by hand, and they might be better suited for specific targets that way, but you can also use ready made list found on the internet. Also Kali has preinstalled some of these lists, their default path is /usr/share/wordlists.

Let's get back to the msfconsole, and give the __search ssh_login__ command again.

![4]

[4]:https://tonikerttula.files.wordpress.com/2021/11/image-61.png?w=682

To choose the module
> use 0

![5]

[5]:https://tonikerttula.files.wordpress.com/2021/11/image-63.png

To set remote host, our target, as Metasploitable 2
> set rhost 192.168.56.101

![6]

[6]:https://tonikerttula.files.wordpress.com/2021/11/image-64.png

Set the USERPASS_FILE we made to be used in the brute force process
> set userpass_file /home/kali/userpass.txt

![7]

[7]:https://tonikerttula.files.wordpress.com/2021/11/image-65.png

Run the exploit
> run

![8]

[8]:https://tonikerttula.files.wordpress.com/2021/11/image-66.png

As we can see, we got 3 ssh connections trough the port 22. It also declares the correct credentials, so you can use them later.

Taktiikka: Impact
Tekniikka: Account Access Removal

Nyt on saatu pääsy sisään koneelle, niin käydään vaihtamassa salasana jossain palvelussa niin, että palvelun asianmukaiset käyttäjät eivät pääse enää kirjautumaan käyttäjätililleen.

Valitaan käyttäjätunnus msfadmin, admin nimi käyttäjätunnuksessa vaikuttaa tottakai lupaavalta, sen salasana näyttääkin olevan myös msfadmin. Otetaan ssh-yhteys koneeseen näillä tunnuksilla.
Ssh-yhteys otetaan antamalla konsoliin komento muodossa ssh käyttäjä@ip-osoite:

>ssh msfadmin@192.168.56.101

Salasana kysytään heti perään. Samalla komennolla sudo su päästään root-oikeuksiin, ja niissä salasana oli sama, eli msfadmin.

![9]

[9]:https://tonikerttula.files.wordpress.com/2021/11/image-79.png


Viimeiseksi jää muuttaa salasana. Vaihdetaan salasana vahvaksi salasanaksi, jotta muilla hyökkääjillä on mahdollisimman vaikea murtautua samaan koneeseen, ja samalla vaikeutetaan alkuperäisen käyttäjän salasanan palauttamista.

Generoin salasanan OpenSSL salasanageneraattorilla, ohjeet sen käyttöön löysin linkistä
https://vitux.com/debian_secure_password/


>openssl rand -base64 14

rand -funktio luo ”pseudorandomin” salasanan

-base64 -funktio luo siitä käyttäjäystävällisen, se käyttää vain merkkejä A-Z, a-z, 0-9 sekä + ja /

14 on salasanan pituus

![10]

[10]:https://tonikerttula.files.wordpress.com/2021/11/image-80.png

Salasana vaihdetaan passwd -komennolla.

![11]

[11]:https://tonikerttula.files.wordpress.com/2021/11/image-81.png

Nyt salasana on vaihdettu, alkuperäiseltä käyttäjältä on poistettu pääsy käyttäjälle!
