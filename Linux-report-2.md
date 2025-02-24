# H2 Linux server course report ”Komentaja Pingviini"

Tämä harjoitustyö on osa Haaga-Helia ammattikorkeakoulun kurssia ”Linux palvelimet”. 
Tehtävänannot löydät kurssin opettajan verkkosivustolta: https://terokarvinen.com/linux-palvelimet/

## Ympäristö, jossa harjoitukset on toteutettu:

Harjoitus on toteutettu kannettavalla koneella.

Malli: `Asus ZenBook UX325_UM325UA`

Prosessori: `AMD64 Family 23 Model 104 Stepping 1 AuthenticAMD ~1801 Mhz`

Prosessoriarkkitehtuuri: `x86-64`

Käyttöjärjestelmä: `Microsoft Windows 11 Home`

# Tehtävä X) Tiivistelmä Tero Karvisen materiaaleista.  
##### (Muutama ranskalainen viiva riittää. Tässä alakohdassa ei tarvitse tehdä testejä tietokoneella. Lisää jokin oma kysymys, idea tai huomio)

- Linuxia hallitaan erilaisilla komennoilla komentorivissä
- Linuxin käyttäjän olisi hyvä ymmärtää ero relatiivisen ja absoluuttisen hakemistopolun välillä
- Komennot alkavat taalamerkin '$' jälkeen

# Tehtävä a) Micro
##### "Asenna Microeditori"

Ensin tarkistettu onko micro asennettu komennolla ``which micro``
Sitten päivitetty pakettivarasto ``sudo apt-get update``
Sitten asennettu micro komennolla ``sudo apt-get install micro -y``

![kuva](https://github.com/user-attachments/assets/b404eb04-8e84-45d3-97a6-416acb8505b9)

Kokeiltu uudestaan ja oli asentunut

![kuva](https://github.com/user-attachments/assets/24f5993d-ad5a-4d68-abdf-617069f025d1)

# Tehtävä b) Apt
##### ""
 Asenna kolme itsellesi uutta komentoriviohjelmaa. Kokeile kutakin ohjelmaa sen pääasiallisessa käyttötarkoituksessa. Ota ruutukaappaus. 
 Kaikki terminaaliohjelmat kelpaavat, TUI (text user interface) ja CLI (command line interface). Osaatko tehdä apt-get komennon, joka asentaa nämä kolme ohjelmaa kerralla?

 Asennettu kolme ohjelmaa (Neofetch, Lolcat ja Tree) komennolla ``sudo apt-get install -y lolcat tree neofetch``

 ![kuva](https://github.com/user-attachments/assets/aef5f9cb-716e-42d3-a8f2-04ad69f09cd6)

 Lolcat värjää tekstiä.
 Tässä esimerkki lolcatin hyödyntämisestä komennolla ``for i in {1..50} do echo "[haluamasi viesti tähän]" | lolcat; done`` 
 Komento tulostaa komentoriviin määrittelemäni viestin 50 iteraation ajan, ja lolcat muuntaa tulosteen kirjaviin väreihin.

 ![kuva](https://github.com/user-attachments/assets/91e23653-8dfd-49a4-a7ad-a2103003bbcc)

Tree näyttää nykyisen hakemistorakenteen jokseenkin graafisessa muodossa

![kuva](https://github.com/user-attachments/assets/fd542aa4-44db-4703-a785-3d0ec7fb813f)

Neofetch näyttää järjestelmätietoja kauniissa paketissa (huom, värjätty lolcatilla)

![kuva](https://github.com/user-attachments/assets/11950fb5-7f9d-4602-ab65-17be1d303610)



 # Tehtävä c) FHS
##### "Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories"."
Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.

## /

Tarkistettu ensin nykyinen sijainti ``pwd``
Tulosteen mukaan sijainti oli käyttäjän kotihakemisto, josta siirrytty juurihakemistoon komennolla ``cd /``
Tarkistettu jälleen nykyinen hakemisto, ja se oli muuttunut juurihakemistoksi. 

Juurihakemisto on kaikkien hakemistojen äiti. Kaikki muu sisältyy siihen. 

![kuva](https://github.com/user-attachments/assets/eadf1542-876c-489f-b605-9e447c69e82f)

## /home/

Seuraavaksi siirrytty kotihakemistoon. Tähän hakemistoon listautuu kaikkien käyttäjien uniikit hakemistot. Kuvakaappauksesta voi kenties päätellä, että omassa järjestelmässäni on vain yksi käyttäjä "vagrant".

![kuva](https://github.com/user-attachments/assets/f1d61621-5fa1-409a-9c47-68161803e33b)

## /home/user/

Seuraavaksi siirrytty vagrantin hakemistoon, josta tämän tehtävän aloitinkin. 
Käyttäjän hakemistossa minulla on vain yksi viikonpäivät -kansio, joka sisältää 7 kansiota * 3 tekstitiedostoa, jotka loin luentotehtävänä. Tämän raportin tehtävässä b esittelen Tree komentoa, ja silloin tämä hakemistorakenne on paremmin nähtävillä.

![kuva](https://github.com/user-attachments/assets/2e7df877-bd88-4c8e-b7a3-4868d124783e)

## /etc/

Seuraavaksi siirrytty etc -hakemistoon, joka sisältää järjestelmäasetukset ihmiselle luettavassa muodossa.
Esimerkiksi kuvakaappauksessa ympyröityyn group -konfiguraatiotiedostoon voidaan kirjoittaa ryhmäpolitiikkoja. Tässä esimerkkikonfiguraatio: ``sudo:salasana1234:007:vagrant,user2``, missä '007' -ID:llä merkitty käyttäjäryhmä saa pääkäyttäjän oikeudet (sudo). Ryhmään kuuluvat käyttäjät vagrant sekä user2, ja ryhmä on suojattu vahvalla salasanalla.  

![kuva](https://github.com/user-attachments/assets/4d08d70e-c249-4c98-974e-ecee8aa08ef6)


## /media/

Media -hakemistossa näkyy ulkoiset tallennusvälineet kuten esimerkiksi SSD-kovalevy tai USB-muistitikku. 
Minulla siellä ei näy mitään, koska en ole liittänyt ulkoista mediaa.

## /var/log/

Tässä hakemistossa on kaikki järjestelmän lokitiedot.


# Tehtävä d) The friendly M
##### "Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta."

Luotu ensiksi kaunis esimerkkitiedosto

![kuva](https://github.com/user-attachments/assets/a54075db-1429-4794-8e86-ebb46e92f9d8)

Komennolla grep "cha" cha.txt tulostetaan kaikki sellaiset cha.txt -tiedoston rivit, joissa esiintyy sana "cha":

![kuva](https://github.com/user-attachments/assets/83ffdc33-f754-473c-836a-e25dd76d61de)

Komennolla voidaan etsiä sellaisia rivejä, joissa esiintyy jokin tietty merkkijono. Lipun -i avulla osumissa ei välitetä siitä, onko merkki kirjoitettu isolla vai pienellä ja --color avulla osumat värikoodataan luettavuuden parantamiseksi. Nyt käytin *.txt komennossa, ja sen avulla tulostuu kaikkien .txt -tiedostojen sisältä löytyneet osumat.

![kuva](https://github.com/user-attachments/assets/6f9d51f5-0178-4401-b159-825ba6e8ec6d)


# Tehtävä e) Pipe
##### "Näytä esimerkki putkista (pipes, "|")."

Putkien avulla komentoja voidaan putkittaa. Olen käyttänyt putkea myös aiemmissa tämän raportin tehtävissä.
Tässä ensimmäisessä esimerkissä tulostan figlet-komennolla tekstin suurina ASCII-taide -kirjaimina, ja putken jälkeen tulevalla osalla ``lolcat`` tuloste värjäytyy. 

![kuva](https://github.com/user-attachments/assets/4c0925dc-8335-4f58-865d-4a5918324215)

Tämä toinen esimerkki on komennosta ``cmatrix | lolcat``.
Cmatrix tulostaa komentoriville Matrix-elokuvasarjasta tutun animaation, jossa merkkijonot putoavat alas. Putken jälkeen lisäämäni lolcat värjää jälleen tulosteen.

![kuva](https://github.com/user-attachments/assets/991c96b8-437c-4f00-8f9e-878dc8b257d0)


# Tehtävä f) Rauta
##### "Listaa testaamasi koneen rauta (‘sudo lshw -short -sanitize’). Asenna lshw tarvittaessa. Selitä ja analysoi listaus."

Päivitettyäni pakettivaraston ``sudo apt-get update`` asensin ohjelman lshw ``sudo apt-get install lshw -y``

Suoritin tehtävänannon komennon, jolla komentoriviin tulostui järjestelmätietoja. 

![kuva](https://github.com/user-attachments/assets/b2c1c660-0c64-4b79-8fe9-06f4c3087e54)

## Lähteet

Karvinen, T. 2009. Command Line Basics, luettavissa: https://terokarvinen.com/2009/command-line-basics-4/ 

