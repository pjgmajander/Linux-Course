# H1 Linux server course report ”Oma linux"

Tämä harjoitustyö on osa Haaga-Helia ammattikorkeakoulun kurssia ”Linux palvelimet”. 
Tehtävänannot löydät kurssin opettajan verkkosivustolta: https://terokarvinen.com/linux-palvelimet/

## Ympäristö, jossa harjoitukset on toteutettu:

Harjoitus on toteutettu kannettavalla koneella.

Malli: `Asus ZenBook UX325_UM325UA`

Prosessori: `AMD64 Family 23 Model 104 Stepping 1 AuthenticAMD ~1801 Mhz`

Prosessoriarkkitehtuuri: `x86-64`

Käyttöjärjestelmä: `Microsoft Windows 11 Home`

# Tehtävä X) 
##### Tiivistelmä Tero Karvisen materiaaleista.

-Hyvä harjoitusraportti on mahdollisimman täsmällinen, helppolukuinen ja toistettava. Se sisältää myös lähdeviittauksia tiedolle

-Myös kaikkien harhapolkujen on oltava toistettavissa raporttia seuratessa

-Mahdollisimman täsmällinen

-Menneessä aikamuodossa kirjoitettu

-Raportilla on järkevä rakenne, ja sen lukeminen on helppoa

-Raportissa ei saa sepittää, plagioida tai rikkoa muutenkaan lakia (esim. tekijänoikeuksia ja salassapitovelvollisuutta)

#### Tiivistelmä Gnu Softwaren materiaaleista

-Vapaa ohjelmisto tarkoittaa ohjelmistoa, jota käyttäjien on mahdollista suorittaa, kopioida, levittää, opiskella, muuttaa ja kehittää
-Neljä perusvapautta
  1. Vapaus suorittaa ohjelma mitä tahansa käyttötarkoitusta varten
  2. Vapaus opiskella ohjelmiston toimintalogiikkaa ja valjastaa se räätälöityyn käyttöön. Edellyttää avointa lähdekoodia.
  3. Vapaus jakaa alkuperäistä ohjelmistoa muiden käyttöön
  4. Vapaus jakaa itse modifioitua versiota ohjelmistosta muiden käyttöön. Tämäkin edellyttää avointa pääsyä lähdekoodiin.


# Tehtävä a) Linuxin asentaminen
##### "Asenna Linux virtuaalikoneeseen"

Päätin luoda virtuaalikoneen Vagrantin avulla, sillä en tarvitse graafista käyttöliittymää mihinkään. Vagrantin asennus täältä: https://developer.hashicorp.com/vagrant/install

Luotu projektille kansio "linux-server" komentorivin kautta.

![kuva](https://github.com/user-attachments/assets/30a9b53c-e0ce-43b3-a675-03b78c2b9de2)

Luotu kansioon vagrant-file, jossa virtuaalikone määritellään

![kuva](https://github.com/user-attachments/assets/cc3b151a-889b-4ef2-90f7-4b1309ca802b)

Muokattu vagrant-fileä notepadissa, selitykset kuvan alla

![kuva](https://github.com/user-attachments/assets/6e47254e-354b-4bbd-ab66-030caa0b3934)

Määritetty staattinen ip-osoite, ja uudelleenohjattu isäntäkoneen portti 1235 virtuaalikoneen http-porttiin 80. 
`skynet.vm.network "private_network", ip: "192.168.74.12"
 skynet.vm.network "forwarded_port", guest: 80, host: 1235`
(Tarkastin portin olevan vapaa kirjoittamalla isäntäkoneen komentoriviin: `netstat -ano | findstr 1235` eli etsin portin 1235 tilatietoja).

Määritetty virtuaalikoneelle host-name
`skynet.vm.hostname = "SKYNET"`

Määritetty jaettu kansio isäntäkoneen ja virtuaalikoneen välillä. Kyseiseen kansioon "vatican_archives" siirtämäni tiedostot näkyvät virtuaalikoneellani polussa /var/www/html.
`skynet.vm.synced_folder "./vatican_archives", "/var/www/html"`

Määritetty virtuaalikoneelle 1GB RAMia ja 4 prosessoria.

`skynet.vm.provider "virtualbox" do |vb|
  vb.memory = "1024"
  vb.cpus = 4`

Provisionoitu virtuaalikoneelle muutama sovellus, jotka asentuivat automaattisesti kun virtuaalikone käynnistettiin. (Nämä asennuskäskyt ovat sikäli idempotentteja, että ne aktivoituvat vain kun virtuaalikone käynnistetään ensimmäisen kerran. Toki `vagrant reload` komennolla ne voidaan suorittaa uudestaan.) Samassa yhteydessä päivitetty ensiksi Linuxin paketinhallintatyökalu apt-get. Asentamani sovellukset ovat cowsay, grep, curl, nano ja ufw.

`skynet.vm.provision "shell", inline: <<-SHELL
 apt-get update
 apt-get install -y cowsay grep curl nano ufw`


Muu muisti on dynaamisesti allokoitavaa 100Gb asti (Huom. tätä ei voi tarkistaa Virtualboxin käyttöliittymästä ennen kuin virtuaalikone on käynnistetty):

![kuva](https://github.com/user-attachments/assets/6f6bed37-228e-4aba-84c6-0fd6b560f655)

Luotu isäntäkoneen työpöydälle vagrantfilessä määritelty jaettu kansio "vatican_archives"

![kuva](https://github.com/user-attachments/assets/439f1acf-4c2f-4fc4-8d42-0267d108956b)

Käynnistetty vagrant

![kuva](https://github.com/user-attachments/assets/8fda289b-c465-4855-b880-03984ce370e3)

Tarkistettu, että oikea käyttöjärjestelmä asentui komennolla: `cat /etc/os-release`

![kuva](https://github.com/user-attachments/assets/897572d4-0ac1-431d-9a07-0c42a85410fc)

Virtuaalikone näkyy nyt myös Oracle VM VirtualBox Managerissa:

![kuva](https://github.com/user-attachments/assets/a3e07acb-955b-4ba2-b730-c55e4c20d307)


# Tehtävä k) Vapaaehtoinen bonus
##### "Suosikkiohjelmani Linuxilla. Tee ja raportoi jokin yksinkertainen toimenpide haluamallasi Linux-ohjelmalla."

Yksinkertaisin lempiohjelmani on cowsay. Esimerkiksi komennolla `cowsay hello world` tulostuu komentoriville lehmä, jonka puhekuplassa lukee "hello world". 

![kuva](https://github.com/user-attachments/assets/f180e3e7-fb31-4d39-8831-9d3ee3f24b10)


## Lähteet

Karvinen, T. 2006. Raportin kirjoittaminen, luettavissa: https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/

GNU Operating System. 2024. What is free software? luettavissa: https://www.gnu.org/philosophy/free-sw.html#four-freedoms
