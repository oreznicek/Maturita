# 4 - Referenční model OSI/ISO a síťové prvky
 - Protokol, rozhraní, popis a funkce jenotlivých vrstev, PDU, zapouzdřování, porovnání s modelem TCP/IP, průchod dat přes síťové prvky, kategorie přepínačů pro jednotlivé vrstvy, nástroje pro zachycování dat v síti, testování a oprava problémů v síti
 - Popis standardního chování opakovače, mostu, přepínače, směrovače, L3 switche, firewallu

## Model OSI/ISO
 - Open System Interconnection
 - International Organization for Standardization
 - Model reprezentuje nějaké operace, které provádíme v síti.
 - OSI model popisuje, co je třeba udělat na konkrétní vrstvě, ale už nám neříká, jak bychom toho měli dosáhnout.
 - Taky popisuje interakci každé vrstvy s její horní a dolní sousedící vrstvou.
 - Změna na konkrétní vrstvě by neměla ovlivnit ostatní vrstvy

<table>
	<thead>
		<tr>
			<th>Číslo</th>
			<th>OSI Model</th>
			<th>PDU</th>
			<th>TCP/IP Protocol Suite</th>
			<th>TCP/IP Model</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>7</td>
			<td>Aplikační</td>
			<td rowspan="3">Data</td>
			<td rowspan="3">HTTP, DNS, DHCP, FTP</td>
			<td rowspan="3">Aplikační</td>
		</tr>
		<tr>
			<td>6</td>
			<td>Prezentační</td>
		</tr>
		<tr>
			<td>5</td>
			<td>Relační (Session)</td>
		</tr>
		<tr>
			<td>4</td>
			<td>Transportní</td>
			<td>TCP Segment / UDP Datagram</td>
			<td>TCP, UDP</td>
			<td>Transportní</td>
		</tr>
		<tr>
			<td>3</td>
			<td>Síťová</td>
			<td>Packet</td>
			<td>IPv4, IPv6, ICMPv4, ICMPv6</td>
			<td>Internet</td>
		</tr>
		<tr>
			<td>2</td>
			<td>Spojová</td>
			<td>Frame (rámec)</td>
			<td rowspan="2">Ethernet, WLAN, SONET, SDH</td>
			<td rowspan="2">Vrstva síťového přístupu</td>
		</tr>
		<tr>
			<td>1</td>
			<td>Fyzická</td>
			<td>Bits</td>
		</tr>
	</tbody>
</table>

V aplikační vrstvě máme jenom data a postupným sestoupením vrstvami dolů se přibalí všechny potřebné informace pro odeslání dat do sítě. Tento proces se nazývá **enkapsulace**.

Vrstvami nahoru se zase všechny zbytečné informace zahodí a zůstanou pouze data. Tento proces se nazývá **de-enkapsulace**.

## 1. Fyzická vrstva
 - Fyzická vrstva je zodpovědná za fyzický přenos dat po síti
 - Poskytuje prostředky pro odeslání a přijetí dat přes **fyzické médium**
 - Převádí bity na signál
   - elektrický, optický
 - Definuje elektrické a mechanické vlastnosti rozhraní
 - **Elektrické vlastnosti**
   - napěťové úrovně, modulace, rychlosti
 - **Mechanické vlastnosti**
   - tvar, velikost, zapojení konektorů

### Síťové prvky
 - **Modem**
   - "modulátor demodulátor"
   - přenost digitálních dat pomocí analogové přenosové trasy
 - **Repeater** (opakovač signálu)
 - **Hub** (rozbočovač)
   - chová se jako opakovač na více portů
   - veškerá data, která přijdou na jeden z portů zkopíruje na všechny ostatní

## 2. Spojová vrstva (Data link)
 - Zajišťuje komunikaci mezi dvěma nebo více uzly propojenými tímtéž datovým spojem
   - Může se jednat o dvoubodovou komunikaci (sériová linka)
   - Nebo mnohabodovou komunikaci (Ethernet)

### Logical Link Control (LLC)
 - přidává do rámce informaci o network layer protokolu
 - umožňuje, aby se v jedné síti mohlo používát několik síťových protokolů
   - IPv4, IPv6, AppleTalk
 - funguje jako rozhraní mezi síťovou vrstvou a MAC podvrstvou
 - IEEE 802.2

### Media Access Control (MAC)
 - je odpovědná za enkapsulaci dat a media access control
   - media access control určuje způsob přenosu dat přes nějaké médium (např. kabel)
 - přidává zdrojovou a cílovou MAC adresu do rámce
 - přidává trailer do rámce (pro detekci chyb)

Media Access Control je něco jako policy, která zajišťuje aby nedošlo ke kolizi a usnadnil se přenos datových paketů mezi koncovými zařízeními

#### MAC Metody
 - **CSMA/CA** - Carrier sense multiple access with collision avoidance
   - WLAN - bezdrát
 - **CSMA/CD** - Carrier sense multiple access with collision detection
   - LAN - drát

### Síťové prvky
 - **Bridge** (most)
   - snižuje velikost kolizní domény
   - umí číst a zapisovat MAC adresy (CAM tabulka)
   - odešle packet do druhé části síťě jen když se tam nachází příjemce
     - týká se jen unicastu
	 - multicast a brodcast pošle bez omezení
 - **Switch** (přepínač)
   - CAM tabulka (spojuje MAC adresy se zdrojovými porty)
   - **Způsoby přeposílání rámců**
     - **store and forward**
	   - zkontroluje CRC → pošle dál
	 - **cut through**
	   - zjistí cílovou MAC → pošle dál 
	   - nekontroluje CRC (nezahazuje vadné framy)
	   - spoléhá se na kontrolu chyb ve vyšší vrstvě

 - **Acess Point (AP)**
   - převádí standard 802.11 na 802.3
   - umožňuje přístup do síťe bezdrátovým zařízením

## 3. Síťová vrstva
 - Identifikuje a adresuje jednotlivé počítače v síti pomocí logických adres (např. IP adres)
 - přidává zdrojovou a cílovou logickou (IP) adresu do PDU
 - Směrování
   - komunikace může probíhat mezi různými sítěmi
   - volba nejlepší cesty pro přenos dat

### Protokoly
 - **IPv4**
 - **IPv6**
 - **AppleTalk**

### Charakteristika IP
 - low overhead protokol
 - poskytuje jen funkce potřebné k doručení ze zdroje k cíli
 - **connectionless**
   - není navázáno žádné spojení před odesláním paketů
   - (posíláme dopis bez oznámení)
 - **best effort**
   - není zaručeno doručení (nespolehlivé)
   - pakety tak můžou dorazit poškozené, v jiném pořadí nebo vůbec
 - **media independent** - není závislé na médiu

### Síťové prvky
 - **Router** (směrovač)
   - směruje pakety na základě
     - přímo připojených sítí
	 - static route
	 - dynamic route (OSPF)
 - **L3 switch**
   - multilayer switch
   - umí vše co switch L2 (pamatuje MAC adresy, VLAN, ...)
   - umí pracovat jako router
   - pracuje rychleji než router

## 4. Transportní vrstva
 - přidává **čísla portu**
 - rozděluje data na **segmenty**
 - zajišťuje výměnu dat mezi aplikacemi z vrstvy L7

### Protokoly
 - **TCP**
   - **spolehlivé** doručení dat
   - žádná data nesmí chybět
   - **flow control**
     - aby nedošlo k zahlcení přijímací strany
   - **aplikace:**
     - HTTP (nemůže chybět kus stránky)
 - **UDP**
   - **plynulé** doručení dat
   - některá data mohou chybět
   - **aplikace:** (kde je důležitá latence)
     - streamovaná data (video)
	 - gaming
	 - průmyslové sítě

### Čísla portů
 - **Cílový port** → podle aplikace na serveru (80 - HTTP).
 - **Zdrojový port** → generovaný OS klienta (51324)

<br/>

 - **Well-known** (0-1023)
   - přiděleny nejpoužívanějším aplikacím
   - FTP, HTTP, DNS, DHCP, ...
 - **Registered** (1024-49151)
   - registruje je IANA
   - Quake, VPN, RDP
 - **Private, dynamic** (49152-65535)
   - většinou zdrojové porty klientů 

### Síťové prvky
 - **Firewall**
   - blokuje data (segmenty, pakety, rámce)
   - je buď **softwarový** → Windows FW
   - nebo **hardwarový**
   - funkce:
     - filtrování paketů
	 - filtrování konkrétních aplikací (čísel portů)
	 - URL filtrování (zabraňuje přístupu na specifické stránky)

## 5. Relační vrstva
 - zakládá, udržuje a synchronizuje relaci (session)
 - obnovuje spojení i v případě fatálního výpadku (hardware)
 - když spojení nelze obnovit, tak session vrstva zajistí, že se nic nestalo
 - session tedy buď úspěšně přenese data nebo všechno zahodí, ale nic mezi tím

## 6. Prezentační vrstva
 - **kódování** (formátování)
   - reprezentace dat (do takového formátu, aby je příjemce dokázal přečíst)
 - **kryptování** (šifrování)
 - **komprese**

## 7. Aplikační vrstva
 - je nejblíže koncovému uživateli
 - na aplikační vrstvu přichází už pouze **data**
 - poskytuje protokoly pro různé **síťové aplikace**
 - tyto protokoly slouží k **výměně dat mezi programy** běžícími na zdrojovém a cílovém hostiteli

## Nástroje pro zachycování dat v síti
 - WireShark
