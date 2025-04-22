## [h4](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#:~:text=2025%3A%20h3%20Aaltoja%20harjaamassa-,h4,-h5) NFC ja RFID

#### 1. Tarkastele käytössäsi olevia RFID tuotteita, mieti miten hyvin olet suojautunut RFID urkinnalta?

Ensimmäinen mieleen juolahtava asia on luottokortin etäluenta/kloonaus. Itselläni on käytössä "moderni" minimalistinen RFID skannauksen estävä lompakko Ridgeltä. Olen itse testannut tuota toimivuutta puhelimen kanssa ja se kyllä toimii niin kuin on mainostettu. Ajattelen että tämä on yksi "parhaita" tapoja suojautua, sillä se ei juuri mitään vaadi, kuin oikeanlaisen lompakon, ottaen huomioon kuinka tärkeä osa (vielä) jokapäiväistä elämäämme pankki- yms. kortit ovat.

![image](https://github.com/user-attachments/assets/f1524b5c-bd08-4f7a-b1bf-15eec8aae136)

Toinen päivittäisessä käytössä oleva tuote on omat kotiavaimet. En oikein tiedä miten niiden suhteen voisin suojautua urkinnalta.. 

![image](https://github.com/user-attachments/assets/cc76c341-30a8-49f1-8b54-998177198a6f)

Puhelimesta löytyy NFC ominaisuus, en tiedä voiko sitä kautta kuinka hyvin hyökätä, mutta varmuuden välttämiseksi pidän sillä hetkellä tarpeettomia toimintoja (ml. bluetooth ja Wifi) aina pois päältä. Tuossa nyt mieleen juolahtavat, joita löytyy. Tunnilla mainittiin mm. lemmikkien sirut, tägit, jotkut langattomat laitteet, mutta noita ei itseltä löydy.



#### 2. Tutustu APDU komentojen rakenteeseen (voit käyttää tekoälyä tutustumiseen)

- "Application Protocol Data Unit"
- Ovat osa ISO/IEC 7816-4 standardia
- Älykorttien (ja lukijoiden?) välistä kommunikaatiota
- Alla tekoälyn tuottama APDU komentorakenne, esimerkkikomento ja sen selitys:

| Byte           | Name          | Description                                               |
|----------------|---------------|-----------------------------------------------------------|
| 1              | CLA           | Class byte — defines the type of command and protocol.    |
| 2              | INS           | Instruction byte — specifies the command to be executed.  |
| 3              | P1            | Parameter 1 — often used for command-specific options.    |
| 4              | P2            | Parameter 2 — more options, often for addressing.         |
| 5 (optional)   | Lc            | Length of Command Data — tells how many data bytes follow.|
| ...            | Data (optional)| The actual payload (if any) sent to the card.             |
| Last           | Le (optional) | Expected length of the response data from the card.       |

> `00 A4 04 00 07 A0 00 00 00 03 10 10 00`

| Byte(s) | Value               | Description                           |
|---------|----------------------|---------------------------------------|
| CLA     | 00                   | ISO 7816-4 compliant.                 |
| INS     | A4                   | SELECT command.                      |
| P1      | 04                   | Select by name.                      |
| P2      | 00                   | First or only occurrence.            |
| Lc      | 07                   | 7 bytes of data follow.              |
| Data    | A0 00 00 00 03 10 10 | AID (Application Identifier).        |
| Le      | 00 (optional)        | Expect maximum length of response.   |

- Kortti vastaa vain kahdella tavulla:

| Field    | Description                                |
|----------|--------------------------------------------|
| Data     | (Optional) Response payload from the card.|
| SW1-SW2  | Status words (2 bytes). Indicates success or error. |



#### 3. Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit. (Vinkki, useimmat liittyvät henkilökortteihin)

##### Hackers Found a Way to Open Any of 3 Million Hotel Keycard Locks in Seconds






### Bonus: Tunnilla saadun kortin tutkiminen

Kortille mahtuu 492 tavua dataa. Linkki tunnilla tehdylle digitaaliselle "käyntikortti" sivustolle vie 22 tavua muistia. Eri tietotyyppien kirjoittaminen kortille tapahtuu NFC Tools sovelluksen kanssa todella näppärästi, sillä siinä on valmiiksi monia vaihtoehtoja esim. puhelinnumero, URL-linkki, yhteystieto, tiedosto, viesti yms. En ole varma miten tuota usean tallennetun tiedon ominaisuutta voisi hyödyntää, sillä ainakin oma puhelimeni lukee vain paikalle 1 tallennetun tiedon, oli se sitten URL, puh.no. tai joku muu. Sovelluksen ilmaisversiossa pitää kirjoittaa jokainen tieto aina uusiksi listalle, jos niitä haluaa siirrellä ja niitä on paljon. Sovelluksen Pro versio ilmeisesti mahdollistaisi tietojen tallennuksen profiilina, jolloin niitä olisi ehkä helpompi hallita.




## Lähteet:

- Ridge Wallet, [kotisivujen verkkokauppa](https://ridgewallet.eu/products/titanium-burnt)
- iLOQ älyavaimet, [kotisivut](https://www.iloq.com/fi/avaimet/)
- Wired.com, [Hackers Found a Way to Open Any of 3 Million Hotel Keycard Locks in Seconds](https://www.wired.com/story/saflok-hotel-lock-unsaflok-hack-technique/)
- NFC Tools, [applikaatio androidille](https://www.wakdev.com/en/apps/nfc-tools-android.html)
- ChatGPT
