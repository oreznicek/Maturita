# 4 - Referenční model OSI/ISO a síťové prvky

Model reprezentuje nějaké operace, které provádíme v síti.

OSI model popisuje, co je třeba udělat na konkrétní vrstvě, ale už nám neříká, jak bychom toho měli dosáhnout.

Taky popisuje interakci každé vrstvy s její horní a dolní sousedící vrstvou.

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
 - Fyzická vrstva je zodpovědná za fyzický přenost dat po síti
 - Poskytuje prostředky pro odeslání a přijetí dat přes **fyzické médium**
 - Převádí bity na signál
   - elektrický, optický
 - Definuje elektrické a mechanické vlastnosti rozhraní
 - **Elektrické vlastnosti**
   - napěťové úrovně, modulace, rychlosti
 - **Mechanické vlastnosti**
   - tvar, velikost, zapojení konektorů

### 1.1 Síťové prvky
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
 - Dělí se na dvě podvrstvy
   - Logical Link Control (LLC)
   - Media Access Control (MAC)

### 2.1 Logical Link Control (LLC)
 - přidává do rámce informaci o network layer protokolu

### 2.2 Media Access Control (MAC)
 - je odpovědná za enkapsulaci dat a řízení přístupu k médiím
 - přidává zdrojovou a cílovou fyzickou adresu do rámce
 - přidává trailer do rámce (detekce chyb přenosu)

Media Access Control je něco jako policy, která zajišťuje aby nedošlo ke kolizi a usnadnil se přenos datových paketů mezi koncovými zařízeními

#### 2.2.1 MAC Metody
 - **CSMA/CA** - Carrier sense multiple access with collision avoidance
 - **CSMA/CD** - Carrier sense multiple access with collision detection

## 3. Síťová vrstva
 - Identifikuje a adresuje jednotlivé počítače v síti pomocí logických adres (např. IP adres)
 - Zajišťuje trasování datových paketů mezi počítači v síti, tedy volbu nejlepší cesty pro přenos dat
