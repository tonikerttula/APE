# Custom Excercise with Metasploitable 2 (editing in progress)

You'll need to set up Metasploitable 2 for this exercise, you can do so by following this [guide](https://github.com/tonikerttula/APE/blob/main/installs/metasploitable2installation.md)

We can use many different tactics when attacking Metasploitable 2. In this excercise, we are going to use from the Att&ck the following tactics and techniques:

1. Discovery: Network Sniffing
2. Reconnaissance: Active Scanning - Vulnerability Scanning
3. Credential Access: Brute Force - Credential Stuffing
4. Collection: Data from Local System
5. Exfiltration
6. Impact: Account Access Removal

Start up Kali and Metasploitable in the same network by making sure they are both set to Host-only adapter in the Network tab in the Virtual Box Manager Settings. Your task is to:

1. Discover IP-address for the target machine.
2. Find vulnerabilities in the Metasploitable machine, which you could use to get access. 
3. Get in the Machine
4. Find something interesting (for example /etc/shadow/)
5. Extract the finding
6. Remove the original user's access to the machine.

Taktiikka: Reconnassaince
Tekniikka: Active Scanning
Alatekniikka: Vulnerability Scanning

Tässä tekniikassa skannataan kohdetta potentiaalisten heikkouksien löytämiseksi esimerkiksi avoimista porteista ja vanhoista sovellusversioista, joissa saattaa olla haavoittuvuuksia.

Käytin Metasploitable 2 kohteena, sillä se oli jo valmiiksi asennettuna edellisen H2 läksyn resurssina. Skannasin kohteen käyttämällä sudo nmap -sV 192.168.56.0/24> komentoa, ja sain tietooni avoimet portit sekä portteja käyttävien sovelluksien versiot!

![1]

[1]:https://tonikerttula.files.wordpress.com/2021/11/image-67.png

Taktiikka: Credential Access
Tekniikka: Brute Force
Alatekniikka: Credential Stuffing

Kokeillaan nyt päästä sisään metasploitableen credential stuffingilla, eli käytetään valmiita salasana/käyttäjätunnus -yhdistelmiä ja koitetaan jos jokin niistä päästää sisään. Avasin Kalissa msfconsole-komennolla metasploitin ja search brute force komennolla etsin valmiita hyökkäyksiä. Valitettavasti resursseja löytyi 105 kappaletta, joten kokeilin Googlea. Ensimmäinen hakutulos suositteli käyttämään tämän nimistä: scanner ssh auxiliary module: ssh_login. Hain siis search ssh_login.

![2]

[2]:https://tonikerttula.files.wordpress.com/2021/11/image-61.png

Antamalla komennon info 0 nähdään tuon ensimmäisen moduulin info, jonka sisältä löytyy tieto, että pitäisi luoda USERPASS_FILE, joka sisältää käyttäjänimen ja salasanan välilyönnillä eroteltuna, jota moduuli sitten kokeilee. Luodaan siis tiedosto, jonne lisään jokaisen yllä porttiskannatun sovelluksen käyttäjätunnuksen ja salasanan, jossa molemmat kentät ovat palvelun nimi (tietenkin osa palveluista ei edes anna ottaa shell-yhteyttä, mutta menkööt harjoituksena). Lisäksi lisään user/user ja msfadmin/msfadmin kombinaatiot, sekä muutaman muun nopeasti päähän juolahtavan kombinaation.

![3]

[3]:https://tonikerttula.files.wordpress.com/2021/11/image-62.png

Näitä tiedostoja ei tarvitse kirjoittaa käsin, on olemassa valmiita kirjastoja, jossa on iso osa käytetyimmistä salasanoista, tai voi hankkia käsiinsä joltakin verkkosivulta vuotaneen käyttäjätunnus/salasana -tietokannan.

Seuraavaksi annetaan uudestaan search ssh_login -komento.

![4]

[4]:https://tonikerttula.files.wordpress.com/2021/11/image-61.png?w=682

use 0 -komennolla valitaan moduuli numero 0.

![5]

[5]:https://tonikerttula.files.wordpress.com/2021/11/image-63.png


set rhost 192.168.56.101 -komennolla asetetaan maaliksi metasploitable 2.

![6]

[6]:https://tonikerttula.files.wordpress.com/2021/11/image-64.png

set userpass_file /home/kali/userpass.txt -komennolla asetetaan käyttäjätunnus/salasana -kirjastoksi juuri luotu tekstitiedosto.

![7]

[7]:https://tonikerttula.files.wordpress.com/2021/11/image-65.png

seuraavaksi vain ajetaan komennolla run

![8]

[8]:https://tonikerttula.files.wordpress.com/2021/11/image-66.png

Kuten näkyy, portin 22 kautta (ssh) saatiin kolme sisäänpääsyä, ja shell yhteyksiä avattiin kolmin kappalein.

Periaatteessa vaihtamalla rhost komennon ip-osoitetta johonkin muuhun kohteeseen, ja käyttämällä mahdollisesti hieman laajempaa, ehkä jopa valmista esim. verkosta löytyvää käyttäjätunnus/salasana -kirjastoa tämän hyökkäyksen voisi toteuttaa muihinkin kohteisiin!
Muista kuitenkin, että muitten kuin omalla laitteella ja verkossa olevien omistamiesi ulkopuolisesta verkosta eristettyjen koneiden tunkeutumistestaus voi olla laitonta!

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
