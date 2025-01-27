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

(Muutama ranskalainen viiva riittää. Tässä alakohdassa ei tarvitse tehdä testejä tietokoneella. Lisää jokin oma kysymys, idea tai huomio)

    Karvinen 2020: Command line basics revisited (nämä komennot ja hakemistot kannattaa myös opiskella ulkoa ja harjoitella automaatiotasolle)

# Tehtävä a) Micro
##### "Asenna Microeditori"

Ensin tarkistettu onko micro asennettu komennolla ``which micro``
Sitten päivitetty pakettivarasto ``sudo apt-get update``
Sitten asennettu micro komennolla ``sudo apt-get install micro -y``

![kuva](https://github.com/user-attachments/assets/b404eb04-8e84-45d3-97a6-416acb8505b9)



# Tehtävä b) Apt
##### ""
 Asenna kolme itsellesi uutta komentoriviohjelmaa. Kokeile kutakin ohjelmaa sen pääasiallisessa käyttötarkoituksessa. Ota ruutukaappaus. 
 Kaikki terminaaliohjelmat kelpaavat, TUI (text user interface) ja CLI (command line interface). Osaatko tehdä apt-get komennon, joka asentaa nämä kolme ohjelmaa kerralla?

 # Tehtävä c) FHS
##### "Asenna Linux virtuaalikoneeseen"
Esittele kansiot, jotka on listattu "Command Line Basics Revisited" kappaleessa "Important directories". Näytä kuvaava esimerkki kunkin tärkeän kansion sisältämästä tiedostosta tai kansiosta. Jos kyseessä on tiedosto, näytä siitä kuvaava esimerkkirivi. Työskentele komentokehotteessa ja näytä komennot, joilla etsit esimerkit.

# Tehtävä d) The friendly M
##### "Asenna Linux virtuaalikoneeseen"
Näytä 2-3 kuvaavaa esimerkkiä grep-komennon käytöstä. Ohjeita löytyy 'man grep' ja tietysti verkosta.

# Tehtävä e) Pipe
##### "Näytä esimerkki putkista (pipes, "|")."


# Tehtävä f) Pipe
##### "Näytä esimerkki putkista (pipes, "|")."
Listaa testaamasi koneen rauta (‘sudo lshw -short -sanitize’). Asenna lshw tarvittaessa. Selitä ja analysoi listaus.

g) Vapaaehtoinen: Valitse muutama rivi lokeista. Tulkitse ja analysoi.

h) Vapaaehtoinen: Asenna jokin plugin micro-editorille ja kokeile sitä. Vaikkapa palettero, cheat tai runit.


## Lähteet

Karvinen, T. 2006. Raportin kirjoittaminen, luettavissa: https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/

GNU Operating System. 2024. What is free software? luettavissa: https://www.gnu.org/philosophy/free-sw.html#four-freedoms
