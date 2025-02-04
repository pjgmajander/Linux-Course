
# H3 Linux server course report ”Hello Web Server"

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

- IP-pohjainen virtuaalipalvelin (virtual host) tarkoittaa verkkopalvelimen konfiguraatiota, jossa useita verkkosivustoja tai sovelluksia isännöidään samalla palvelimella, mutta jokaisella sivustolla on oma IP-osoite (Apache)
- Nimipohjaisilla virtuaalipalvelimilla sama ip-osoite voi johtaa useille eri verkkosivuille (Apache)
- DNS-nimipalvelinta voidaan simuloida polussa /etc/hosts (Karvinen)

# Tehtävä a) Localhost
##### "Testaa, että weppipalvelimesi vastaa localhost-osoitteesta. Asenna Apache-weppipalvelin, jos se ei ole jo asennettuna.

Weppipalvelin vastaa. Huom, olen poistanut Apachen oletussivun /var/www/html/index.html 

![kuva](https://github.com/user-attachments/assets/bf356e42-6c4f-4a43-901c-42ea4a9289b8)


# Tehtävä b) Log
##### "Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit (eli selitä yksityiskohtaisesti jokainen kohta ja numero, etsi tarvittaessa lähteitä)."

Etsin lokietiedostot komennolla ``sudo tail /var/log/apache2/access.log``
Virhelokin löytäisi samalla komennolla tiedostosta error.log

![kuva](https://github.com/user-attachments/assets/6dbb598c-b15a-480c-95cf-71480c0591d4)

Alussa näkyvä IP-osoite 10.0.2.2 on Vagrantin ja VirtualBoxin käyttämä erityinen osoite, joka viittaa isäntäkoneeseen virtuaalikoneen perspektiivistä. Tämän jälkeen näkyvät kaksi viivaa indikoivat, että käyttäjänimeä ei ole. 
Seuraava ``31/Jan/2025:05:39:43 +0000`` kertoo, milloin pyyntö on tehty. Tässä tapauksessa pyyntö on tehty 31. tammikuuta 2025 kello 05:39:43 UTC-aikavyöhykkeessä. Seuraavaksi näkyy GET-pyyntö, joka on tehty palvelimelle. Esimerkiksi tapauksessa 
``"GET /favicon.ico HTTP/1.1"`` asiakas pyytää /favicon.ico-tiedostoa käyttäen HTTP/1.1 -protokollaa. Tämän jälkeen näkyy numerosarja 404, joka tarkoittaa ettei resurssia löytynyt. Numerosarja 200 puolestaan tarkoittaa sitä, että resurssi löydettiin. Ensimmäistä numerosarjaa seuraava toinen numerosarja, esimerkiksi 489 tarkoittaa tavumäärää, jolla palvelin vastasi GET-pyyntöön. "http://localhost:1235/" viittaa URL-osoitteeseen, josta pyyntö tehtiin. Tässä näkyy, että tein isäntäkoneella pyynnön localhost-osoitteen porttiin 1235, jonka olen määrittänyt vagrantfilen port-forwarding säännöissä ohjaamaan isäntäkoneen portin 1235 virtuaalikoneen porttiin 80. Lisätietoja tästä löydät tämän repon ensimmäisestä linux-raportista. 
Viimeisessä tekstilitanjassa näkyy tieto siitä, että millä käyttöjärjestelmällä ja selaimella pyyntö lähetettiin.

# Tehtävä c) Name Based Virtual Host
##### "Tee uusi name based virtual host. Sivun tulee näkyä suoraan palvelimen etusivulla http://localhost/. Sivua pitää pystyä muokkaamaan normaalina käyttäjänä, ilman sudoa. Tee uusi, laita vanhat pois päältä. Uusi sivu on hattu.example.com, ja tämän pitää näkyä: asetustiedoston nimessä, asetustiedoston ServerName-muuttujassa sekä etusivun sisällössä (esim title, h1 tai p)."

![kuva](https://github.com/user-attachments/assets/1b58603f-06c7-41f8-8506-cf52f5c1a370)

![kuva](https://github.com/user-attachments/assets/306a1534-f50b-4923-9cc7-d32ed2a038c7)

![kuva](https://github.com/user-attachments/assets/7542620f-98fa-4cdc-a31c-93a921f41d65)

Muokattu konfiguraatiotiedosta komennolla ``sudoedit /etc/apache2/sites-available/hattu.example.com.conf``

![kuva](https://github.com/user-attachments/assets/a146a666-b99d-43ee-b190-a9791bae919a)

Tämän jälkeen simuloitu nimipalvelinta isäntäkoneen hosts-tiedoston kautta. Avattu ensin isäntäkoneen notepad admin-oikeuksilla, ja tämän jälkeen avattu siihen hosts-tiedosto, joka löytyi
seuraavasta polusta: C:\Windows\System32\drivers\etc\hosts
Lisätty tiedostoon juuri äsken virtuaalikoneeseen konfiguroitu osoite.

![kuva](https://github.com/user-attachments/assets/f77c5e6f-1e3e-429d-be52-b251d6cf5560)

Yhdistetty isäntäkoneella osoitteeseen hattu.example.com, mutta kohdattu 403-forbidden virheilmoitus. 

![kuva](https://github.com/user-attachments/assets/2bd2397b-be47-4d9d-9a2d-551f1b54bf99)

Tarkastettu apachen error.log
"client denied by server configuration" virheilmoituksesta päätelty, että konfiguraatiotiedostossa on jotain häikkää

![kuva](https://github.com/user-attachments/assets/3ceefb9e-15d5-4df3-b51c-ff1170fe470d)

Havaittu kirjoitusvirhe konfiguraatiotiedostossa

![kuva](https://github.com/user-attachments/assets/20815a9e-ceb7-4339-8410-a99223b0b7eb)

Korjattuani virheen, sain yhteyden viimein muodostettua

![kuva](https://github.com/user-attachments/assets/057b7f66-2d1d-45eb-9e9d-a025fc0b3483)


# Tehtävä e) HTML5
##### "Tee validi HTML5 sivu."

![kuva](https://github.com/user-attachments/assets/3219fd43-fadc-4952-b613-8870c719cf8b)

![kuva](https://github.com/user-attachments/assets/4fb4bd92-5996-4489-ac0b-55879b710d64)

![kuva](https://github.com/user-attachments/assets/27c3d47f-8f69-4f31-ae23-2ea6f8aa0f64)



# Tehtävä f) Curl
##### "Anna esimerkit 'curl -I' ja 'curl' -komennoista. Selitä 'curl -I' muutamasta näyttämästä otsakkeesta (response header), mitä ne tarkoittavat."

# Tehtävä o) 
##### "Vapaaehtoinen, vaikea: Laita sama tietokone vastaamaan kahdellla eri sivulla kahdesta eri nimestä. Eli kaksi weppisiteä samalla koneelle, esim. foo.example.com ja bar.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla."


## Lähteet

The Apache Software Foundation. 2023. Apache HTTP Server Version 2.4 Documentation. Luettavissa: https://httpd.apache.org/docs/2.4/vhosts/name-based.html 

Karvinen, T. 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
