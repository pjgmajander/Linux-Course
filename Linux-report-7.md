


# H7 Linux server course report ”Almost there"

Tämä harjoitustyö on osa Haaga-Helia ammattikorkeakoulun kurssia ”Linux palvelimet”. 
Tehtävänannot löydät kurssin opettajan verkkosivustolta: https://terokarvinen.com/linux-palvelimet/

## Ympäristö, jossa harjoitukset on toteutettu:

Harjoitus on toteutettu kannettavalla koneella.

Malli: `Asus ZenBook UX325_UM325UA`

Prosessori: `AMD64 Family 23 Model 104 Stepping 1 AuthenticAMD ~1801 Mhz`

Prosessoriarkkitehtuuri: `x86-64`

Käyttöjärjestelmä: `Microsoft Windows 11 Home`


# Tehtävä a) Hello World! (again..)
##### Kirjoita ja aja "Hei maailma" kolmella kielellä.

Ensialkuun tarkistin, että ovatko valitsemani kielet Python, C & Java esiasennettuina. Vain Python löytyi virtuaalikoneestani ennakkoon.

![kuva](https://github.com/user-attachments/assets/28abb3db-6ed1-414b-9806-287c90f5e3ca)

Seuraavaksi päivitin paketinhallinnan ``sudo apt-get update`` ja ryhdyin asentamaan puuttuvia ohjelmointikieliä.

![kuva](https://github.com/user-attachments/assets/71d54693-4de5-4a53-8cbb-43bbddd3bf8a)

Loin polkuun /home/deepseeker/ kansion Hello World -skriptejä varten: ``mkdir hw``

#### Py3

Ensiksi loin kansioon helpoimman eli Python -skriptin: ``nano hw.py``

Skriptin sisällöksi kirjoitin vain yhden rivin ``print("Hello World!")``

![kuva](https://github.com/user-attachments/assets/8f31017e-6d64-49c6-aab2-76312edd6d86)

Tässä lopputulos:

![kuva](https://github.com/user-attachments/assets/4886b0a7-938d-4f0b-8949-b15293e599fd)

#### Java

Seuraavaksi oli vuorossa hivenen vaikeampi kieli eli Java: ``nano HloWrld.java``

![kuva](https://github.com/user-attachments/assets/8b59956d-3584-4d22-ba96-48bb7098b0f0)

Ennen skriptin eli lähdekoodin suorittamista se on käännettävä Java-kääntäjän (javac) avulla bittikoodiksi, jota tietokone ymmärtää. Tämä toteutetaan komennolla ``javac LuokanNimi.java``
Komennon suorittamisen jälkeen hakemistoon ilmestyi bittikooditiedosto "HloWrld.class". Tarkastin uteliaisuudesta sen sisällön cat-komennon avulla.

![kuva](https://github.com/user-attachments/assets/4d3454d1-6e6b-4fd3-8295-9b5a4cc20456)

Skriptin suorittaminen tuotti halutun tuloksen:

![kuva](https://github.com/user-attachments/assets/07f4413b-9413-4229-b50b-cb8bf40313a6)

Tässä vielä ylimääräinen demonstraatio virhetilanteesta, jossa lähdekoodia ei ole käännetty Java-komentotulkille luettavaan muotoon (eli poistin aiemman bittikooditiedoston "HloWrld.class")

![kuva](https://github.com/user-attachments/assets/75f66949-1518-4c38-9791-abe874226ad6)

#### C

Kirsikkana kakun päälle loin monimutkaisimmalla tuntemallani kielellä hieman monimutkaisemman skriptin: 

![kuva](https://github.com/user-attachments/assets/55b84178-c351-43ab-9fea-3368853086a9)

Seuraavaksi aivan samalla tavalla kuin Javan kanssa, lähdekoodi tulee kääntää komentotulkille ymmärrettävään muotoon. Tämä tapahtuu komennolla ``gcc LuokanNimi.c -o HaluamasiNimiOhjelmalle`` (GCC = Gnu Compiler for C)
Tutkin myös bittikoodia cat-komennolla vain todetakseni, että se on huomattavasi kryptisemmän näköinen kuin aiemmassa esimerkissäni Javan kanssa.

![kuva](https://github.com/user-attachments/assets/31df39ea-b49e-4f5e-a3ca-44332535d4e8)

Tässä lopputulos:

![kuva](https://github.com/user-attachments/assets/b48e44b7-4474-469d-82cf-be1e9703accb)

(Käännös: "Hei kaikki! Opiskelen kiinaa, koska tahtoisin lentää Pekingiin! Näkemiin!")

# Tehtävä b) New command
##### Laita Linuxiin uusi, itse tekemäsi komento niin, että kaikki käyttäjät voivat ajaa sitä.

# Tehtävä c) Lab
##### Ratkaise vanha arvioitava laboratorioharjoitus soveltuvin osin.


## Lähteet

Let's Encrypt. 2024. How It Works. Luettavissa: https://letsencrypt.org/how-it-works/

Lange, N. 2024. Lego: Obtain a Certificate: Using an existing, running web server. Luettavissa;

The Apache Software Foundation. 2025. Apache HTTP Server Version 2.4 [Official] Documentation: SSL/TLS Strong Encryption: How-To: Basic Configuration Example. Luettavissa: https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample 

Metsola, S. https://www.satumetsola.com/ 

