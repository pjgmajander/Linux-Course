


# H5 Linux server course report ”Named"

Tämä harjoitustyö on osa Haaga-Helia ammattikorkeakoulun kurssia ”Linux palvelimet”. 
Tehtävänannot löydät kurssin opettajan verkkosivustolta: https://terokarvinen.com/linux-palvelimet/

## Ympäristö, jossa harjoitukset on toteutettu:

Harjoitus on toteutettu kannettavalla koneella.

Malli: `Asus ZenBook UX325_UM325UA`

Prosessori: `AMD64 Family 23 Model 104 Stepping 1 AuthenticAMD ~1801 Mhz`

Prosessoriarkkitehtuuri: `x86-64`

Käyttöjärjestelmä: `Microsoft Windows 11 Home`


# Tehtävä x) Tiivistelmä
##### Lue ja tiivistä. Tiivistelmäksi riittää muutama ranskalainen viiva per artikkeli. (Tässä alakohdassa ei tarvitse tehdä testejä tietokoneella)




# Tehtävä b) A-rating.
##### Testaa oma sivusi TLS jollain yleisellä laadunvarmistustyökalulla, esim. SSLLabs (Käytä vain tavanomaisia tarkistustyökaluja, ei tunkeutumistestausta eikä siihen liittyviä työkaluja)

En valitettavasti voi toteuttaa tätä tehtävää omalla sivullani, sillä Vagrantin ja hosts-tiedoston avulla simuloitu verkkosivusto ei ole näkyvillä julkisessa internetissä. Tämän takia toteutan tehtävän tutkimalla kokeellisen suomalaisen nykytaiteilijan (Satu Metsola) sivustoja. Sivustot on luotu Squarespacella, ja oletan jo valmiiksi laadun olevan verrattain korkea. Tässä tulokset kun osoitteen satumetsola.com syöttää ssllabssin työkaluun:

![kuva](https://github.com/user-attachments/assets/8b0d37f0-6489-455a-91d9-4d7be7a3b7a7)

Selitys raportin eri osista:

```Overall Rating: A+```
Tämä tarkoittaa sitä, että kokonaisarvosana on korkein mahdollinen. Sivuston sertifikaattien konfiguraatio on siis todella turvallinen.
Palvelin tukee TLS:n versiota 1.3, joka on protokollan uusin ja turvallisin versio. 

```This site works only in browsers with SNI support```

Tämä tarkoittaa sitä, että verkkosivusto käyttää Server Name Indication (SNI) -teknologiaa, joka mahdollistaa useiden SSL-sertifikaattien käytön samassa IP-osoitteessa. Mahdollisena käyttäjäkokemusta heikentävänä seikkana on se, että vanhemmat selaimet, jotka eivät tue SNI:tä, eivät voi muodostaa yhteyttä verkkosivustoon.

# Tehtävä c) Weppilomake
##### Tee weppilomake, jossa on käyttäjätunnus ja salasana. Käytä salaamatonta http-yhteyttä. Sieppaa liikennettä (esim. Wireshark, ngrep). Mitä havaitset? Mitä vaikutuksia tällä on tietoturvaan?

![kuva](https://github.com/user-attachments/assets/da7f464e-90d1-4056-b689-8ed1854794ad)


![kuva](https://github.com/user-attachments/assets/6d12cd52-e5f0-47a5-af42-e2447006def8)

Päivitetty pakettivarasto ``sudo apt-get update``
Sitten asennettu ngrep eli linuxin wireshark 

![kuva](https://github.com/user-attachments/assets/5e45f371-53eb-446c-a714-e0ee69a57c42)

![kuva](https://github.com/user-attachments/assets/91318fbb-03c9-42d0-a6ad-911f37f7a1cd)

![kuva](https://github.com/user-attachments/assets/95475848-d97e-48cb-9f64-bc281b33f087)


## Lähteet

Let's Encrypt. 2024. How It Works. Luettavissa: https://letsencrypt.org/how-it-works/

N, Lange. 2024. Lego: Obtain a Certificate: Using an existing, running web server. Luettavissa;

The Apache Software Foundation. 2025. Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example. Luettavissa: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample 

