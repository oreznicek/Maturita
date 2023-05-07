# 2 - Aplikační vrstva TCP/IP (DHCP, NAT, DNS)

 - Sítě P2P a klient-server (pro porovnání), aplikace P2P a klient-server (model)
 - WEB server, protokoly, porty, zabezpečení
 - email, protokoly, popis cesty od zdroje k cíli
 - komunikace s DHCP serverem, obsah zprávy DHCP serveru, DHCP Relay
 - Koncepce NAT, důvody a výhody použití NAT, port forwarding, druhy NAT
 - Doménové jméno FQDN, systém DNS - kořenové servery, TLD, SLD, autoritativní odpověď
 - FTP, SMB, NFS, telnet, TFTP, SSH, NTP

## Aplikační vrstva TCP/IP
 - Aplikační vrstva je nejblíže koncovému uživateli
 - Na aplikační vrstvu nám už přichází pouze **data**
 - Poskytuje nám protokoly pro různé aplikace
 - Tyto protokoly slouží k **výměně dat mezi programy** běžícími na zdrojovém a cílovém hostiteli

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
	</tbody>
</table>

### Prezentační vrstva
 - kódování
 - kryptování
 - komprese

### Relační vrstva (session)
 - navazuje, udržuje a synchronizuje session
 - obnovuje spojení i v případě fatálního výpadku (hardware)
 - když spojení nelze obnovit, tak session vrstva zajistí, že se nic nestalo
 - session tedy buď úspěšně přenese data nebo všechno zahodí, ale nic mezi tím

## Druhy aplikací

### Klient-server
 - klient zpravidla navazuje spojení
 - žádá nějaká data od serveru
 - na serveru jsou tedy uchovávána data
 - čím více uživatelů, tím pomalejší přístup (zatížení serveru)
 - přístup na **email**, **web**

### Peer-to-peer (P2P)
 - síť, ve které spolu komunikují přímo jednotliví klienti
 - bez použití dedikovaného serveru
 - každé připojené zařízení se chová jako klient i server
 - oproti klient-server se méně přetěžuje, méně náchylná vůči výpadkům
 - **kryptoměny**, **torrenty**
