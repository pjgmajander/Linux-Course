
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

- IP-pohjainen virtuaalipalvelin (virtual host) tarkoittaa verkkopalvelimen konfiguraatiota, jossa useita verkkosivustoja tai sovelluksia isännöidään samalla palvelimella, mutta jokaisella sivustolla on oma IP-osoite.
- Nimipohjaisilla virtuaalipalvelimilla sama ip-osoite voi johtaa useille eri verkkosivuille. 

# Tehtävä a) Localhost
##### "Testaa, että weppipalvelimesi vastaa localhost-osoitteesta. Asenna Apache-weppipalvelin, jos se ei ole jo asennettuna.

Weppipalvelin vastaa. Huom, olen poistanut Apachen oletussivun /var/www/html/index.html 

![kuva](https://github.com/user-attachments/assets/bf356e42-6c4f-4a43-901c-42ea4a9289b8)


# Tehtävä b) Log
##### "Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit (eli selitä yksityiskohtaisesti jokainen kohta ja numero, etsi tarvittaessa lähteitä)."


# Tehtävä c) 
##### "Tee uusi name based virtual host. Sivun tulee näkyä suoraan palvelimen etusivulla http://localhost/. Sivua pitää pystyä muokkaamaan normaalina käyttäjänä, ilman sudoa. Tee uusi, laita vanhat pois päältä. Uusi sivu on hattu.example.com, ja tämän pitää näkyä: asetustiedoston nimessä, asetustiedoston ServerName-muuttujassa sekä etusivun sisällössä (esim title, h1 tai p)."

# Tehtävä e) HTML5
##### "Tee validi HTML5 sivu."

# Tehtävä f) 
##### "Anna esimerkit 'curl -I' ja 'curl' -komennoista. Selitä 'curl -I' muutamasta näyttämästä otsakkeesta (response header), mitä ne tarkoittavat."

# Tehtävä o) 
##### "Vapaaehtoinen, vaikea: Laita sama tietokone vastaamaan kahdellla eri sivulla kahdesta eri nimestä. Eli kaksi weppisiteä samalla koneelle, esim. foo.example.com ja bar.example.com. Voit simuloida nimipalvelun toimintaa hosts-tiedoston avulla."


## Lähteet

The Apache Software Foundation. 2023. Apache HTTP Server Version 2.4 Documentation. Luettavissa: https://httpd.apache.org/docs/2.4/vhosts/name-based.html 
Karvinen, T. 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
