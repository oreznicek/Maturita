# 22 - Základní desky
 - Základní deska (čipová sada, bios)
 - interní sběrnice (PCI, PCIe)
 - externí sběrnice (usb, firewire)

## Základní deska
 - hlavní část počítače
 - propojuje komponenty, dává jim napájení

### Formáty základních desek
 - nejčastější je formát ATX
 - dále jsou kompaktnější varianty
 - custom u notebooků 

<img src="./img/mb_formats.jpeg" />

## Části MB
 - CPU Soket
   - PGA - piny na CPU
   - LGA - piny na desce
 - sloty na RAM
   - DIMM
   - je několik typů DIMM a ty do sebe vzájemně nepasují (liší se počtem pinů)
 - Čipset (severní, jižní)
 - Interní sběrnice
   - PCI
   - PCI express
   - SATA
 - Externí sběrnice
   - PS/2
   - USB
   - Thunderbolt
   - Firewire
 - BIOS/UEFI

### Čipset

Řídí tok dat mezi procesorem, pamětí a periferiemi.

 - **Northbridge**
   - Má na starosti rychlejší periferie
   - Dnes je součástí CPU (integrovaný)
   - CPU
   - RAM
   - Sběrnice PCIe
 - **Southbridge**
   - má na starosti pomalejší periferie
   - s CPU komunikuje přes Northbridge
   - LPC sběrnice
     - ROM paměť s BIOSem
	 - Super I/O (PS/2)
   - Sběrnice PCI
   - Sběrnice SATA, RAID, USB, Ethernet

### BIOS
 - Basic Input Output System
 - uložen v paměti (EEPROM) přímo na základní desce
 - provádí POST (power on self test)
 - následně startuje operační systém
 - nastavení v CMOS čipu
 - je uložen v ROM nebo EEPROM

### UEFI
 - Unified Extensible Firmware Interface
 - nástupce BIOSu
 - obsahuje GUI

### Interní sběrnice
 - **SATA**
   - pro připojení disků
 - **PCI**
   - paralelní
   - v dnešní době se moc nepoužívá
   - předchůdce PCIe
 - **PCI express**
   - full-duplex sériová linka
   - přenos dat na základě paketů
   - bitová šířka 1-16
   - **použití** - připojení přídavných karet
     - grafická, zvuková, síťová
 
### Externí sběrnice
 - **PS/2**
   - připojení klávesnice/myš
   - nepoužívá se
 - **USB**
   - Universal Serial Bus
   - univerzální rozhraní
   - USB 2.0, 3.0, 4
   - **použití** - připojení klávesnice/myš, flash disk, sluchátka
 - **Thunderbolt**
   - 40 Gb/s
   - USB-C konektor
   - **použití** - připojení monitorů, napájení, přenos dat (klávesnice)
 - **Firewire**
   - předchůdce thunderboltu
   - od Applu
   - **použití** - jen na přenos dat
