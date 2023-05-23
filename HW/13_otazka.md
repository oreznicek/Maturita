# 13 - Problematika bezpečnosti počítačových sítí
 - Fyzická bezpečnost, sociální inženýrství, zranitelnost, exploit, hrozba
 - Podvržení adres, zesilovač, DoS, DDoS, Man in the Middle (MITM), průzkumné útoky
 - Malware trojský kůň, virus, červ, Botnet (zombie), ransomware
 - Zabezpečení přepínače (včetně port security) proti zranitelnostem (ARP flooding, DHCP snooping a starvation, VLAN, STP, CDP)
 - Zabezpečení koncových zařízení včetně bezdrátových

## Bezpečnostní hrozby
 - **vnitřní** (viry, worms, malware, DoS, DDoS, krádež identity)
 - **vnější** (ztráta nebo krádež zařízení, neúmyslné zneužití zařízení zaměstnanci)
 - nejbezpečnější je domeček co nemá dveře
 - dveře potřebujeme, ale představují zranitelnost
 - **zranitelnost** = dveře
 - **exploit** = využití zranitelnosti (klíč)
 - **threat** (hrozba) = hacker
 - **mitigate** = zmírnění hrozeb

### Cíle hrozeb
 - krádež informací
 - ztráta dat a manipulace s lidmi
 - krádež identity

### Ochrana
 - **fyzická** (zabezpečení samotného HW)
   - umístění (katastrofy)
   - lidské chyby
   - vandalismus
   - mříže, vrátnice
 - **softwarová**
   - antiviry, šifrování, hesla, firewally
 - **postupy a zásady**
   - bezpečnostní politika a její vynucování
   - standyrdy, procedury
   - odpovědnost pracovníků v kyberobraně
 - **provozní**
   - výchová pracovníků
   - školení
   - práce s poštou a weby
   - používání počítačů

## Sociální inženýrství
 - manipulace lidí za účelem provedení určité akce nebo získání určité informace
 - netechnické formy útoku
 - zaměřuje se na uživatele sítě
 - je využívání silné citové manipulace - strach, empatie

### Formy
 - **Phishing** - útočník zasílá falešné odkazy
 - **Whaling** - lov na velryby (vysoce postavené představitele firem)
 - **Vishing** - phishing pomocí hlasu
 - **Smishing** - phishing pomocí sms zpráv
 - **Scareware** - software snažící se uživatele donutit k instalaci škodlivého softwaru
 - **Vydávání se za technika**

## Typy síťových útoků
 - **DoS - Denial of Service**
   - přehlcení serveru požadavky - pád, nedostupnost pro ostatní uživatele
 - **MITM - Man in the Middle**
   - útočník odposlouchává komunikaci mezi dvěma konci 
   - přesměrovává síťový provoz
   - útočník může získat citlivá data nebo se za někoho vydávat
   - většinou infekce ARP cache (tváří se jako brána)
 - **DDoS - Distribute DoS**
   - DoS z více počítačů
 - **Amplification attack** (zesilovač)
   - útočník zasílá requesty se zdrojovou adresou oběti
   - server posílá oběti velké množství odpovědí

## Typy malwaru
 - škodlivý software
 - virus, červ, trojan, ransomware, spyware, adware, ...

### Počítačový virus
 - **množí se**
 - vkládá svůj kód do spustitelných souborů, dokumentů, ...
 - replikuje se, potřebuje hostitele
 - zabírá místo na disku, snižuje výkon

### Adware
 - není nijak škodlivý
 - může být velmi otravný
 - zobrazuje uživateli nechtěné reklamy a autor malwaru může mít z reklam příjem

### Spyware
 - Malware se záměrem shromažďování (citlivých) informací o osobě nebo společnosti
 - shromážděná data pak odesílá autorovi škodlivého kódu
 - není snadné určit přesnou hranici, co je v pořádků a co už je spyware (cookies, cílená reklama, ...)

### Červ
 - Rozesílá kopie sebe sama na jiné počítače, nejčastěji po síti
 - Oproti viru nepotřebuje hostitelský software
 - Zatěžuje počítačovou síť
 - Může se v něm vyskytovat kód navíc (nesloužící přímo pro jeho replikaci)

### Botnet
 - síť infikovaných počítačů na internetu řízená centrálně z jednoho místa (počítač útočníka)
 - infikované počítače se nazývají zombies
 - útočník může využít zombies pro rozesílání spamů nebo pro DDoS útok

### Ransomware
 - Zablokování a zašifrování dat oběti a znemožnění přístupu k PC, dokud není zaplaceno výkupné
 - Vyhrožování, že budou zveřejněna citlivá data
 - Placení výkupného často v kryptoměnách kvůli složitějšímu dohledání pachatele
 - Nejčastěji se do PC dostane formou trojského koně, může se ale jednai o červa

### Trojský kůň
 - Legitimní program ke kterému je přibalen malware

## Průzkumné útoky
 - cílem je získat nějakou představu o síti, na kterou chci zaútočit a to pomocí různých metod
 - packet sniffing, ping sweeps, port scanning, phishing, social engineering, ...
 - nmap

## Zabezpečení síťových prvků

### ARP Flooding
 - Spam ARP Request na gateway, aby si nevšimla ARP spoofingu

### ARP Spoofing
 - Spam ARP Replay - IP adresa gateway, ale MAC adresa threat actor
 - Pro koncové zařízení se threat actor stane gateway - MITM

### MAC Flooding
 - Zaplavení MAC adresami, snaha vyčerpat paměť přepínače (CAM tabulka)
 - Odesílání velkého množství rámců s unikátními zdrojovými MAC adresami
 - Snaha útočníka, aby se legitimní MAC adresy dostaly pryč z CAM tabulky a rámce pro ně byly rozeslány

## Zabezpečení koncových zařízení
 - **antivirus** - ESET, Windows Defender, Avast, Kaspersky
 - **firewall**
