

# H5 Linux server course report ”Named"

Tämä harjoitustyö on osa Haaga-Helia ammattikorkeakoulun kurssia ”Linux palvelimet”. 
Tehtävänannot löydät kurssin opettajan verkkosivustolta: https://terokarvinen.com/linux-palvelimet/

## Ympäristö, jossa harjoitukset on toteutettu:

Harjoitus on toteutettu kannettavalla koneella.

Malli: `Asus ZenBook UX325_UM325UA`

Prosessori: `AMD64 Family 23 Model 104 Stepping 1 AuthenticAMD ~1801 Mhz`

Prosessoriarkkitehtuuri: `x86-64`

Käyttöjärjestelmä: `Microsoft Windows 11 Home`


# Tehtävä a) Nimi 
##### Laita julkinen nimi osoittamaan omaan koneeseesi. (Siis vastaava kuin terokarvinen.com. Nimen saattaa saada myös ilmaiseksi Github Education -paketilla. Suosittelen hankkimaan oikean nimen, mutta jos välttämättä haluat, voit myös simuloida nimen toimintaa paikallisesti hosts-tiedoston avulla.)

Aloittaessani työskentelyn huomasin, että olin unohtanut sammuttaa Vagrant -virtuaalikoneeni. Muistiini juolahti, että tämä saattaa sotkea järjestelmän kellonajan, joten tarkistin sen heti komennolla ``date``

Kellonaika oli kuin olikin väärässä:

![kuva](https://github.com/user-attachments/assets/ea7681f5-73aa-4096-ba98-4bb541af748c)

Päivitin siis ensitöikseni järjestelmän kellonajan komennolla ``sudo date [MMDDhhmmYYYY]``

![kuva](https://github.com/user-attachments/assets/693fcd74-6e43-4147-a91a-f034f5352d3c)

Seuraavaksi loin deepseeker -käyttäjälle uuden hakemistopolun verkkosivua varten:

![kuva](https://github.com/user-attachments/assets/f9623ea6-a5cb-4225-82b7-4a2153416f26)

Luotu konfiguraatiotiedosto

![kuva](https://github.com/user-attachments/assets/b44888d1-e5b1-4ec6-9803-81c495ffe2b8)

Hosts

![kuva](https://github.com/user-attachments/assets/a45de7b4-2440-4546-b10e-a703398693d4)

Enabloitu sivu ja uudelleenkäynnistetty apache2-demoni

![kuva](https://github.com/user-attachments/assets/3f53016c-f9b1-4827-ae88-83194abce7da)

Sivua ei löytynyt

![kuva](https://github.com/user-attachments/assets/863fbef1-91e5-4068-83c0-7af1165511e6)

Raportista 3 oppineena kävin tarkastamassa suoraan conf -tiedoston, ja siellä olikin jälleen kirjoitusvirhe 

![kuva](https://github.com/user-attachments/assets/2b9eb7dd-b9a9-4066-bdc0-3d92f424242b)

Nyt tulikin uusi virheilmoitus

![kuva](https://github.com/user-attachments/assets/4f92d96f-6cfb-485a-b178-a338b3668a89)

Korjattu T. Karvisen ohjeilla

![kuva](https://github.com/user-attachments/assets/2df87119-562d-4c23-8694-2c7a3a55de6b)


# Tehtävä b) Based
##### Laita Name Based Virtual Host näkymään uudessa nimessäsi. Kotisvuja pitää pystyä muokkaamaan ilman pääkäyttäjän oikeuksia.

# Tehtävä c) Kotisivu
##### Tee vähintään kolmen erillisen alasivun (esim. index.html, blog.html, projects.html) kotisivu ja kopioi se näkymään palvelimellesi. Sivujen muokkaamisen pitää onnistua ilman pääkäyttäjän oikeuksia, niiden kopioiminen pääkäyttäjänä testisivun paikalle ei käy. Kotisivujen ei tarvitse olla hienoja, mutta niiden tulee olla validia HTML:ää ja linkittää toisiinsa.

####Index.html

![kuva](https://github.com/user-attachments/assets/2647c2e4-153e-4e42-9933-d40a535a6277)


####Apply.html

![kuva](https://github.com/user-attachments/assets/a0a3702c-178b-4049-9c43-0f94293e3d98)

####History.html

![kuva](https://github.com/user-attachments/assets/f13b5501-ea74-4a70-b113-c4b3087c1c52)



# Tehtävä d) Alidomain
##### Tee kaksi uutta alidomainia, jotka osoittava omaan koneeseesi. Esimerkiksi palvelu on example.com -> linuxkurssi.example.com. Alidomainit ovat tyypillisesti ilmaisia, kun sinulla on päädomain (example.com). Tässä tehtävässä riittää, että alidomainit avaavat saman sivun kuin päädomain. (Vapaaehtoinen bonus: Tee toinen alidomain A-tietueella ja toinen CNAME-tietueella. Vapaaehtoinen bonus: tee alidomainiin oma erillinen name based virtual host.)

# Tehtävä e) DNS
##### Tutki jonkin nimen DNS-tietoja 'host' ja 'dig' -komennoilla. Käytä kumpaakin komentoa kaikkiin nimiin ja vertaa tuloksia. Katso man-sivulta, miten komennot toimivat - esimerkiksi miten 'dig' näyttää kaikki kentät. Analysoi tulokset, keskity nimipalvelimelta tulleisiin kenttiin (dig näyttää paljon muutakin tietoa). Etsi tarvittaessa uusia lähteitä haastaviin kohtiin. Sähköpostin todentamiseen liittyvät SPF ja DMARC -tietojen yksityiskohdat on jätetty vapaaehtoiseksi lisätehtäväksi. Tutkittavat nimet:

##### Oma domain-nimesi. Vertaa tuloksia nimen vuokraajan (namecheap.com, name.com...) weppiliittymässä näkyviin asetuksiin.

##### Jonkin pikkuyrityksen, kerhon tai yksittäisen henkilön weppisivut. (Ei kuitenkaan kurssikaverin tällä viikolla vuokrattua nimeä).

##### Jonkin suuren ja kaikkien tunteman palvelun tiedot.

## Lähteet


