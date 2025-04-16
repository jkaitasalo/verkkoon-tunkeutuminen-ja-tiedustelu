## [h3](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#:~:text=grep%20%2Dir%20%22tero%22-,h3,-Aaltoja%20harjaamassa) Aaltoja harjaamassa.md

#### x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

- Hubacek 2019: [Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs](https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s) (Video, alkaen 3:19 ja päättyen 7:40. Yhteensä noin 4 min.)
  - Henkilö käynnistää Spectrum Analyzer ohjelman kuuntelemaan taajuutta, jonka jälkeen painaa kaukosäätimen nappeja.
  - Ohjelma nappaa säätimen lähettämän taajuuden.
  - Syystä X ei kannata valita signaalin korkeinta/keskikohtaa.
  - Error Tolerance ja Bit Length säätämällä voi hienosäätää, jos signaali ei kohtaa lähetyksen bitteihin.
  - Demoludation vaiheessa jos kuvaaja kohtaa signaalia, kaikki ok.
- Cornelius 2022: [Decode 433.92 MHz weather station data](https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html)
  - rtl_433 käytetään signaalin purkuun
  - kopioitu sivulta:

>The sensor sends 36 bits 12 times, the packets are ppm modulated (distance coding) with a pulse of ~500 us followed by a short gap of ~1000 us for a 0 bit or a long ~2000 us gap for a 1 bit, the sync gap is ~4000 us.
>
>The data is grouped in 9 nibbles:
>
>[id0] [id1] [flags] [temp0] [temp1] [temp2] [const] [humi0] [humi1]
>
>- The 8-bit id changes when the battery is changed in the sensor.
>- flags are 4 bits B 0 C C, where B is the battery status: 1=OK, 0=LOW
>- and CC is the channel: 0=CH1, 1=CH2, 2=CH3
>- temp is 12 bit signed scaled by 10
>- const is always 1111 (0x0F)
>- humidity is 8 bits

  - Signaalin tarkastelu:
    - Spectrum Analyzer (File menu)
    - SDR device, receiving frequency, gain. odota signaalia
    - RTL-SDR laitteen todellinen "gain" on jaettu 10 URH:ssa 80 = 8dB
    - Luo projektikansio, jonne kaikki tallentuu
    - Vastaanoton taajuutta kannattaa säätää hieman sivuun siitä mitä Analyzer antoi, noin 20 - 100 kHz
    - Signaalin tallennuksessa on tärkeää kaapata vähintään 2 signaalin "burst":ia
    - Signaalin amplitude tulisi olla väh. 2x noise amplitudesta
    - 
   


#### a) WebSDR. Etäkäytä WebSDR-ohjelmaradiota, joka on kaukana sinusta ja kuuntele radioliikennettä. Radioliikenne tulee siepata niin, että radiovastaanotin on joko eri maassa tai vähintään 400 km paikasta, jossa teet tätä tehtävää. Käytä esimerkkinä julkista, suurelle yleisölle tarkoitettua viestiä, esimerkiksi yleisradiolähetystä. Kerro löytämäsi taajuus, aallonpituus ja modulaatio. Kuvaile askeleet ja ota ruutukaappaus. (Tehtävässä ei saa ilmaista sellaisen viestin sisältöä tai olemassaoloa, joka ei ole tarkoitettu julkiseksi. Voit sen sijaan kuvailla, miten sait julkisen radiolähetyksen kuulumaan kaiuttimistasi. Julkisten, esimerkiksi yleisradiolähetysten sisältöä saa tietysti kuvailla.)


#### b) rtl_433. Asenna rtl_433 automaattista analyysia varten. Kokeile, että voit ajaa sitä. './rtl_433' vastaa "rtl_433 version 25.02 branch..."


#### c) Automaattinen analyysi. Mitä tässä näytteessä tapahtuu? Mitä tunnisteita (id yms) löydät? Converted_433.92M_2000k.cs8. Analysoi näyte 'rtl_433' ohjelmalla.


#### d) Too compex 16? Olet nauhoittanut näytteen 'urh' -ohjelmalla .complex16s-muodossa. Muunna näyte rtl_433-yhteensopivaan muotoon ja analysoi se. Näyte Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s


#### e) Ultimate. Asenna URH, the Ultimate Radio Hacker.


##### Tarkastele näytettä 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s. Siinä Nexan pistorasian kaukosäätimen valon 1 ON -nappia on painettu kolmesti. Käytä Ultimate Radio Hacker 'urh' -ohjelmaa.


#### f) Yleiskuva. Kuvaile näytettä yleisesti: kuinka pitkä, millä taajuudella, milloin nauhoitettu? Miltä näyte silmämääräisesti näyttää?


#### g) Bittistä. Demoduloi signaali niin, että saat raakabittejä. Mikä on oikea modulaatio? Miten pitkä yksi raakabitti on ajassa? Kuvaile tätä aikaa vertaamalla sitä johonkin. (Monissa singaaleissa on line encoding, eli lopullisia bittejä varten näitä "raakabittejä" on vielä käsiteltävä)








## Lähteet:

- https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/
- https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s
- https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html
- 
