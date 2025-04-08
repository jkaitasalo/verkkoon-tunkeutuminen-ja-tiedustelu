# [h2](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#:~:text=k%C3%A4ytt%C3%A4j%C3%A4%20k%C3%A4ytt%C3%A4%C3%A4%3F%20(spoiler)-,h2,-%3A%20Lempiv%C3%A4ri%3A%20violetti): Lempiväri: violetti


#### x) Lue ja vastaa lyhyesti kysymyksiin. Tässä alakohdassa x ei tällä kertaa tarvitse lukea artikkeleita kokonaan, ei tarvitse tiivistää niitä, eikä tehdä testejä koneella.

- Selitä tuskan pyramidin idea 1-2 virkkeellä. Bianco 2013: [Pyramid of Pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html). (Katso eritoten pyramidin kuvaa.)
  - Pyramidi esittää eri indikaattoreita, joilla voidaan havaita tunkeutujan toimintaa
  - Jokainen askel ylemmäs on hyökkääjälle haitallisempi, sillä niitä on hankalampi hyökkääjän muuttaa

- Selitä timanttimallin (Diamond Model) idea 1-2 virkkeellä. Tekijä esittelee sen aika juhlallisesti, voit myös etsiä yksinkertaisempia artikkeleita [hakukoneella](https://duckduckgo.com/?t=ftsa&q=diamond+model+attacker+capability+infrastructure&ia=web) tai kelata suoraan timantin kuvaan. Caltagirone et al 2013: [Diamond Model](https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf)
  - Keskittyy tapahtuneen hyökkäksen analysointiin ja tarkasteluun, jotta voidaan päästä hyökkäyksen askelten jäljille.
  - Timantin neljä kulmaa ovat yhteydessä toisiinsa, siten että voidaan avata mahdollisia polkuja hyökkäyksen takana.
  - Kulmien väliset osuudet auttavat täyttämään tyhjiä aukkoja hallussa olevassa tiedossa ja tehostaa näin hyökkäyksen tutkimusta.

#### a) Apache log. Asenna Apache-weppipalvelin paikalliselle virtuaalikoneellesi. Surffaa palvelimellesi salaamattomalla HTTP-yhteydellä, http://localhost . Etsi omaa sivulataustasi vastaava lokirivi. Analysoi yksi tällainen lokirivi, eli selitä sen kaikki kohdat. (Jos Apache ei ole kovin tuttu, voit tätä tehtävää varten vain asentaa sen ja testata oletusweppisivulla. Eli ei tarvitse tehdä omia kotisvuja tms.)

- Asensin Teron ohjeiden mukaisesti Apache-webbipalvelimen ilman ongelmia.
- Surffasin HTTP-yhteydellä `http://localhost` ja logasin apachella tuon liikenteen.

![image](https://github.com/user-attachments/assets/738f1a74-a5cc-4f8a-a255-f5216ee70e07)

- ChatGPT avustuksella ensimmäinen rivi:
  - IP osoite 127.0.0.1, eli localhost
  - Aika
  - GET pyyntö kotisivusta
  - Statuskoodi 200 (ok)
  - 3380 on pyynnön koko 3380 tavua
  - Käyttäjän tiedot Mozilla/5.0 Linuxilla


#### b) Nmapped. Porttiskannaa oma weppipalvelimesi käyttäen localhost-osoitetta ja 'nmap -A' päällä. Selitä tulokset. (Pelkkä http-portti 80/tcp riittää)

- Tulokset `nmap -A 127.0.0.1` -komennon ajosta:

![image](https://github.com/user-attachments/assets/5c40584b-f544-4e12-9e06-cc159a87884c)

- Tuloksista voidaan nähdä, että portti 80/tcp on auki ja siellä pyörii Apache webbipalvelin 2.4.63 Debian


#### c) Skriptit. Mitkä skriptit olivat automaattisesti päällä, kun käytit "-A" parametria? (Näkyy avoimien porttinumeroiden alta, http-blah, http-blöh...).

- Jonkinlaisia tunnistavia skriptejä ainakin
- Kuvankaappauksessa näkyy:
  - Device Type: general purpose
  - Running: Linux 2.6.X|5.X
  - Käyttöjärjestelmän tietoja, sekä lopuksi verkon etäisyys (tässä 0 hops)

#### d) Jäljet lokissa. Etsi weppipalvelimen lokeista jäljet porttiskannauksesta (NSE eli Nmap Scripting Engine -skripteistä skannauksessa). Löydätkö sanan "nmap" isolla tai pienellä? Selitä osumat. Millaisilla hauilla tai säännöillä voisit tunnistaa porttiskannauksen jostain muusta lokista, jos se on niin laaja, että et pysty lukemaan itse kaikkia rivejä?



#### e) Wire sharking. Sieppaa verkkoliikenne porttiskannatessa Wiresharkilla. Huomaa, että localhost käyttää "Loopback adapter" eli "lo". Tallenna pcap. Etsi kohdat, joilla on sana "nmap" ja kommentoi niitä. Jokaisen paketin jokaista kohtaa ei tarvitse analysoida, yleisempi tarkastelu riittää.



#### f) Net grep. Sieppaa verkkoliikenne 'ngrep' komennolla ja näytä kohdat, joissa on sana "nmap".



#### g) Agentti. Vaihda nmap:n user-agent niin, että se näyttää tavalliselta weppiselaimelta.



#### h) Pienemmät jäljet. Porttiskannaa weppipalvelimesi uudelleen localhost-osoitteella. Tarkastele sekä Apachen lokia että siepattua verkkoliikennettä. Mikä on muuttunut, kun vaihdoit user-agent:n? Löytyykö lokista edelleen tekstijono "nmap"?



## Lähteet:

- https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/
- https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html
- https://duckduckgo.com/?t=ftsa&q=diamond+model+attacker+capability+infrastructure&ia=web
- https://www.threatintel.academy/wp-content/uploads/2020/07/diamond-model.pdf
- https://attack.mitre.org/
- https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf
- https://chatgpt.com/
- 
