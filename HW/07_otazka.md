# 7 - Sítě standardu IEEE 802.11
 - Přenosová trasa, přístup k médiu, IEEE 802.11/a/b/g/n/ac/ad/ax
 - AFHSS, DSSS, OFDM, QAM, MIMO, šířka pásma, kanály, přenosová rychlost
 - Beamforming, RU, BSS Coloring, TWT, MU-MIMO, OFDMA
 - AD-hoc, Wi-Fi Direct, infrastrukturní sítě, BSS, ESD, ESSID, MAC control
 - Zabezpečení WLAN - WEP, WPA, WPA2, WPA3, AAA, EAP, 802.1X, Radius

## Bezdrátová připojení
 - Přenášejí elektromagnetické signály pomocí rádiových frekvencí
 - Dnes už jeden z hlavních způsobů připojení k síti

### Omezení bezdrátových sítí
 - **Oblast pokrytí**
   - fungují dobře v otevřeném prostředí
   - místní terén a překážky mohou omezit efektivní pokrytí
 - **Rušení**
   - náchylná k rušení
   - např. běžnými zařízeními (telefon, mikrovlnka, ...)
 - **Sdílené médium**
   - bezdrátové médium je sdíleno všemi uživateli
   - mnoho uživatelů přistupujících k síti WLAN má za následek snížení šířky pásma pro každého z nich

### Bezdrátová média
 - **Wireless Access Point (AP)**
 - **Wireless NIC adapter**

## Typy bezdrátových sítí
 - **WPAN**
   - používá vysílače s nízkým výkonem pro síť s krátkým dosahem (6 - 9 metrů)
   - Bluetooth, ZigBee, Z-Wave (proprietární)
 - **WLAN**
   - používá vysílače pro pokrytí středně velké sítě
   - použití v domácnostech, kancelářích
 - ...

## IEEE 802.11 standardy

<table>
	<thead>
		<tr>
			<th>Generace</th>
			<th>IEEE standard</th>
			<th>Radiová frekvence</th>
			<th>Rychlost</th>
			<th>Modulace</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th></th>
			<td>802.11</td>
			<td>2.4 GHz</td>
			<td>2 Mb/s</td>
			<td></td>
		</tr>
		<tr>
			<th></th>
			<td>802.11a</td>
			<td>5 GHz</td>
			<td>54 Mb/s</td>
			<td>OFDM</td>
		</tr>
		<tr>
			<th></th>
			<td>802.11b</td>
			<td>2.4 GHz</td>
			<td>11 Mb/s</td>
			<td>DSSS</td>
		</tr>
		<tr>
			<th></th>
			<td>802.11g</td>
			<td>2.4 GHz</td>
			<td>54 Mb/s</td>
			<td>OFDM</td>
		</tr>
		<tr>
			<th>Wi-Fi 4</th>
			<td>802.11n</td>
			<td>2.4 a 5 GHz</td>
			<td>600 Mb/s</td>
			<td>MIMO OFDM</td>
		</tr>
		<tr>
			<th>Wi-Fi 5</th>
			<td>802.11ac</td>
			<td>5 GHz</td>
			<td>3,5 Gb/s</td>
			<td>MU-MIMO OFDM</td>
		</tr>
		<tr>
			<th>Wi-Fi 6</th>
			<td>802.11ax</td>
			<td>2.4 a 5 GHz</td>
			<td>9,6 Gb/s</td>
			<td>MU-MIMO OFDMA</td>
		</tr>
	</tbody>
</table>

 - Wi-Fi 6E je také založena na standardu 802.11ax a přidává podporu pro frekvenci 6GHz

## Rádiové frekvence
 - Všechna bezdrátová zařízení pracují v oblasti rádiových vln elektromagnetického spektra

Sítím WLAN jsou přidělen následující frekvenční pásma:

 1. 2.4 GHz (UHF) - 802.11/b/g/b/ax
 2. 5 GHz (SHF) - 802.11a/n/ac/ax

### Elektromagnetické spektrum

![Elektromagnetické spektrum](./img/elektromagneticke_spektrum.png)

## Access Point (AP)
 - převádí protokol **IEEE 802.11** na **802.3**

Existují dva druhy AP:

 1. **Autonomní AP**
    - používají se, když potřebujeme pouze pár AP
	- vyžadují nezávislou konfiguraci
	- např. Home Router
 2. **Controller-based AP** (CAP)
    - když potřebujeme mnoho AP
	- LAP - Lightweight AP
	- ke komunikace s řadičem WLC používají LWAPP protokol
	- pomocí řadiče se konfigurují jednotlivá AP

## Antény
 - **Všesměrová anténa** (Omnidirectional)
   - 360 stupňové pokrytí
   - ideální v domech, otevřených kancelářích, konferenčích místnostech a venkovních prostorách
 - **Směrová anténa** (Directional)
   - zaměřuje signál v daném směru
   - signál je silný pouze v tomto jedno směru
   - např. **Yagi** a **parabola**
 - **MIMO antény**
   - využívá více antén ke zvýšení **šířky pásma**
   - lze použít až 8 vysílacích a 8 přijímacích antén
   - využívá se u 802.11n/ac/ax

## 802.11 Režimy bezdrátové topologie

### Ad hoc
 - bezdrátové připojení dvou zařízení způsobem **peer-to-peer** (P2P)
 - příkladem jsou bezdrátoví klienti, kteří k sobě přistupují pomocí **Bluetooth**
 - označuje se jako **IBSS** - independent basic service set

### Infrastructure mode
 - v tomto režimu se bezdrátoví klienti propojují prostřednictvím **wireless routeru** nebo **access pointu (AP)**
 - AP se připojují pomocí kabelového distribučního systému např. **Ethernet**

### Tethering
 - varianta topologie **ad hoc**
 - vytvoření osobního hotspotu pomocí telefonu nebo tabletu
 - ostatní zařízení poté pomocí P2P připojení získají přístup k internetu

## BSS a ESS
 - **Basic Service Set (BSS)**
   - skládá se z jednoho AP, který propojuje všechny bezdrátové klienty
   - klienti mohou mezi sebou komunikovat jen v rámci **Basic Service Area (BSA)**
   - k jednoznačné identifikaci AP se používá MAC adresa - **Basec Service Set Identifier (BSSID)**
   - **BSSID** je vždy spojen pouze s jedním AP

<div align="center">
	<img src="./img/basic_service_set.png" width="70%" alt="BSS" />
</div>

 - **Extended Service Set (ESS)**
   - ESS je spojení více BSS prostřednictvím distribučního systému
   - ESS je identifikován **SSID** a každý BSS je identifikován **BSSID**
   - V rámci jedné ESS tak spolu můžou komunikovat bezdrátoví klienti z různých BSA

<div align="center">
	<img src="./img/extended_service_set.png" width="70%" alt="ESS" />
</div>

## Passive and Active discover mode

### Passive

<div align="center">
	<img src="./img/passive_discover_mode.png" width="70%" />
</div>

### Active

<div align="center">
	<img src="./img/active_discover_mode.png" width="70%" />
</div>

## Šířka pásma
 - Šířka pásma je obecně množství dat, které mohou proudit přes médium za daný čas
 - V bezdrátových sítích je to **rozsah frekvencí**, které jsou k dispozici pro přenos signálu
 - Větší šířka pásma znamená větší přenosovou rychlost a větší kapacitu pro přenos dat

<div align="center">
	<img src="./img/bandwidth.svg" width="50%" />
</div>

## Kanály
 - jsou určené pro rozdělení šířky pásma na menší kousky
 - ty jsou použity pro komunikaci mezi zařízeními
 - pokud je poptávka po určitém kanálu příliš vysoká, může dojít k jeho přesycení

### Nasycení frekvenčního kanálu

Byla vytvořena řada technik pro zlepšení bezdrátové komunikace a zmírnění nasycení.

 - **Direct Sequence Spread Spectrum (DSSS)**
   - modulační technika určená k **rozprostření signálu** ve větším frekvenčním pásmu
   - správně nakonfigurovaný přijímač dokáže modulaci DSSS obrátit a zrekonstruovat původní signál
   - modulaci používají zařízení v **802.11b**, aby se vyhnula rušení

<div align="center">
	<img src="./img/DSSS.png" width="60%" />
</div>

 - **Frequency-Hopping Spread Spectrum (FHSS)**
   - probíhá pomocí metod rozprostřeného spektra
   - přenáší radiové signály **přepínáním** nosného signálu **mezi mnoha frekvenčními kanály**
   - odesílatel i přijímač musí být synchronizováni (aby věděli na který kanál mají přejít)
   - tento proces přeskakování umožňuje efektivnější využití kanálů a snižuje jejich přetížení
   - FHSS byl použit u standardu **802.11**
   - používají ho také **vysílačky** a **Bluetooth**

<div align="center">
	<img src="./img/FHSS.png" width="60%" />
</div>

 - **Orthogonal Frequency-Division Multiplexing (OFDM)**
   - jedná se o podmnožinu multiplexování kmitočtovým dělením, kdy jeden kanál využívá více dílčích kanálů na sousedních frekvencích
   - dílčí kanály jsou vůči sobě přesně ortogonální, což umožňuje, aby se dílčí kanály překrývaly bez vzájemného rušení
   - používá se v **802.11a/g/n/ac**
   - nový systém **802.11ax** používá variantu OFDM - **OFDMA**

<div align="center">
	<img src="./img/OFDM.png" width="60%" />
</div>

## Zabezpečení WLAN
 - pro zabezpečení se dá použít **SSID cloaking** nebo **filtrování MAC adres**
 - nejlepším způsobem zabezpečení WLAN je však použití **ověřování** (authentication) a **šifrování** (encryption)

### Metody ověřování

Jsou dva základní druhy ověřování:

 1. **Open**
    - každý bezdrátoví klient se může snadno připojit (bez hesla)
	- měl by se používat pouze v situacích, kdy není třeba dbát na bezpečnost
	- používá se např. v kavárnách, hotelech, obchodních centerch, ...
 2. **Shared key** (Ověřování pomocí sdíleného klíče) 
    - poskytuje mechanismy jako WEP, WPA, WPA2 a WPA3 pro šifrování dat mezi AP a klientem
	- heslo musí být předem sdíleno mezi oběma stranami, aby se mohly připojit

<div align="center">
	<img src="./img/overovaci_metody_WLAN.png" width="70%" />
</div>

#### Metody ověřování pomocí sdíleného klíče
 - **WEP** (Wired Equivalent Privacy)
   - původní metoda šifrování ze standardu 802.11
   - využívá šifru **RC4** se statickým klíčem
   - klíč se při výměně paketů nikdy nemění, což usnadňuje hackerské útoky
   - **WEP by se tak už nikdy neměl používat**
 - **WPA** (Wi-Fi Protected Access)
   - používá silnější šifrovací algoritmus **TKIP** (Temporal Key Integrity Protocol)
   - TKIP mění klíč pro každý paket (obtížnější na hackování)
 - **WPA2**
   - současný průmyslový standard pro zabezpečení WLAN
   - k šifrování používá standard **AES** (Advanced Encryption Standard)
 - **WPA3**
   - nová generace zabezpečení Wi-Fi
   - vyžaduje používání **PMF** (Protected Managment Frames)
   - zařízení s WPA3 ještě nejsou dostupná

#### Ověřovací metody WPA2
 - **Personal**
   - určeno pro domácí nebo malé kancelářské sítě
   - uživatelé se ověřují pomocí **PSK**
   - není vyžadován žádný ověřovací server
 - **Enterprise**
   - určeno pro podnikové sítě
   - vyžaduje ověřovací server **RADIUS** (AAA)
   - uživatelé se musí ověřit pomocí standardu **802.1X**, který používá **EAP** (Extensible Authentication Protocol) 
