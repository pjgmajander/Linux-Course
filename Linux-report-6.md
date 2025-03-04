


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

#### Let's Encrypt:

   - Let's Encryptin ja ACME -protokollan tarkoituksena on mahdollistaa sellaisen HTTPS-palvelimen rakentaminen, joka hakee automaattisesti selaimen luottaman sertifikaatin.
     
   - Let's Encrypt CA tunnistaa palvelimen ylläpitäjän julkisen avaimen perusteella, ja lähettää palvelimelle tehtävän (DNS-tietueen tai HTTP-resurssin luominen).
     
   - Palvelin saa Let's Encryptiltä myös Nonce-nimisen satunnaisen luvun, jonka palvelin allekirjoittaa omalla yksityisellä avaimellaan.

#### Lange (Lego): 

   - Lego työkalun avulla voidaan hankkia ja hallita TLS-sertifikaatteja.
     
   - Olemassaoleva verkkopalvelin, joka kuuntelee porttia 80, voi suorittaa Let's Encryptin haasteen tällä komennolla: ``lego --accept-tos --email you@example.com --http --http.webroot /path/to/webroot --domains example.com run``

#### Apache:

   - Apache verkkopalvelimen SSL-asetukset voidaan määrittää minimikriteereillä lataamalla ensin SSL-moduulin komennolla: ``LoadModule ssl_module modules/mod_ssl.so``
     
   - Tämän jälkeen Apache käsketään kuuntelemaan porttia 443 komennolla: ``Listen 443``

   - Lopuksi Apachen konfiguraatiotiedostoon lisätään seuraavat ohjeet:
     
``<VirtualHost *:443>
    ServerName www.example.com
    SSLEngine on
    SSLCertificateFile "/path/to/www.example.com.cert"
    SSLCertificateKeyFile "/path/to/www.example.com.key"
</VirtualHost>``

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

Ensimmäiseksi loin yksinkertaisen kirjautumislomakkeen.

![kuva](https://github.com/user-attachments/assets/da7f464e-90d1-4056-b689-8ed1854794ad)

Lomake näyttää selaimessa tältä:

![kuva](https://github.com/user-attachments/assets/6d12cd52-e5f0-47a5-af42-e2447006def8)

Päivitetty pakettivarasto komennolla: ``sudo apt-get update``
Tämän jälkeen asensin ngrep -työkalun, jolla voidaan kuunnella verkkoliikennettä. ``sudo apt-get -y install ngrep``

Aloitin liikenteen kuuntelun komennolla: ``sudo ngrep -d any -W byline port 80``
"-d any" antaa lisäohjeen kuunnella kaikkia verkkoliitäntöjä ja "-W byline" kirjoittaa siepatun liikenteen rivi kerrallaan komentoriville. Sieppaus on rajoitettu vain portin 80 liikenteelle. 

![kuva](https://github.com/user-attachments/assets/5e45f371-53eb-446c-a714-e0ee69a57c42)

Syöttäessäni tunnuksia, selaimeni varoitti minua siitä, että yhteys ei ole salattu. 

![kuva](https://github.com/user-attachments/assets/91318fbb-03c9-42d0-a6ad-911f37f7a1cd)

Syötettyäni erilaisia tunnuksia, löysin ne kaikki komentoriviltä siepatun verkkoliikenteen joukosta. Salasana näkyy selkokielisenä tekstinä.

![kuva](https://github.com/user-attachments/assets/95475848-d97e-48cb-9f64-bc281b33f087)

Toisin sanoen tämä osoittaa sen, että http-liikennettä voidaan lukea selkokielisenä. Tämä altistaa sivuston man in the middle -verkkohyökkäyksille, jossa hyökkääjä kaappaa salaamattoman liikenteen itselleen ngrepin, wiresharkin tai muun vastaavan työkalun avulla. Ei hyvä.


## Lähteet

Let's Encrypt. 2024. How It Works. Luettavissa: https://letsencrypt.org/how-it-works/

N, Lange. 2024. Lego: Obtain a Certificate: Using an existing, running web server. Luettavissa;

The Apache Software Foundation. 2025. Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example. Luettavissa: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample 

S. Metsola. https://www.satumetsola.com/ 
