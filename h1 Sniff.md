## [h1](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#:~:text=Page%20Using%20Github-,h1,-Sniff) Sniff


#### x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

1. Karvinen 2025: [Wireshark - Getting Started](https://terokarvinen.com/wireshark-getting-started/)
- työkalu "sniffaukseen" ja analysointiin
- seuraavaksi asennusohjeet
- käyttöliittymästä valitaan mitä halutaan haistella
  - "any" haistelee kaiken liikenteen, joten sillä on helppo haistella "jotain"
- hyvä käytäntö on haistella vain vähän kerrallaan, ettei joudu käymään kerralla paljon läpi
- sniffauksen tulokset voi tallentaa, tästä luodaan tiedosto.pcap
  - luotu kaappaus voidaan analysoida samalla tavalla kuin "normaali" sniffaus
- kaapatusta datasta nähdään statistiikkaa "Statistics" mm.
  - Endpoints
  - I/O Graphs
  - Procol hierarchy
- dataa voi myös suodattaa erilaisilla filtereillä mm.
  - dns
  - tls
  - http
  - tcp.port == 443
  - ip.addr == 192.168.122.7


2. Karvinen 2025: [Network Interface Names on Linux](https://terokarvinen.com/network-interface-linux/)
- 123
- 123


#### a) Linux. Asenna Debian tai Kali Linux virtuaalikoneeseen. (Tätä alakohtaa ei poikkeuksellisesti tarvitse raportoida, jos sinulla ei ole mitään ongelmia. Jos on mitään haasteita, tee täsmällinen raportti)

Päätin asentaa Kalin VirtualBoxiin, sillä siinä on valmiina paljon ominaisuuksia, joiden uskon olevan hyödyllisiä kurssilla. Asennuksen yhteydessä ei ilmennyt ongelmia.


#### b) Ei voi kalastaa. Osoita, että pystyt katkaisemaan ja palauttamaan virtuaalikoneen Internet-yhteyden.


#### c) Wireshark. Asenna Wireshark. Sieppaa liikennettä Wiresharkilla. (Vain omaa liikennettäsi. Voit käyttää tähän esimerkiksi virtuaalikonetta).


#### d) Oikeesti TCP/IP. Osoita TCP/IP-mallin neljä kerrosta yhdestä siepatusta paketista. Voit selityksen tueksi laatikoida ne ruutukaappauksesta.


#### e) Mitäs tuli surffattua? Avaa [surfing-secure.pcap](https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/surfing-secure.pcap). Tutustu siihen pintapuolisesti ja kuvaile, millainen kaappaus on kyseessä. Tässä siis vain lyhyesti ja yleisellä tasolla. Voit esimerkiksi vilkaista, montako konetta näkyy, mitä protokollia pistää silmään. Määrästä voit arvioida esimerkiksi pakettien lukumäärää, kaappauksen kokoa ja kestoa.
