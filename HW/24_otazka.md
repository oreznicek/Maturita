# 24 - Zařízení pro ukládání dat
 - Pevné disky (HDD, SSD), optická média (CD, DVD, BlueRay)
 - Rozhraní PATA, SATA, SCSI, SAS, M. 2.

## HDD
 - Hard Disk Drive
 - **nevolatilní**
 - pro čtení a ukládání dat se využívá magnetické indukce
 - různé technologie pro zápis dat s cílem zvýšení hustoty dat

Jak funguje

 - **plotna**
 - **rameno**
 - **čtecí / zapisovací hlava**
 - **stopa** (kruh)
 - **sektor** (část kruhu)

### Organizace dat
 - **PMR**
   - Kolmý magnetický záznam
   - 3x větší hustota
 - **HAMR**
   - laserová dioda, která zahřívá materiál
   - díky zahřátí lze zapisovat do menších oblastí

### RAID
 - **RAID 0**
   - půlka dat na jednom a půlka na druhém disku
   - zvyšuje výkon
 - **RAID 1**
   - zrcadlí data na víc disků
   - zvyšuje bezpečnost
 - **RAID 5**
   - 3 nebo více disků
   - data jsou rozdělena mezi disky s paritním bitem
   - pokud selže 1 disk, data lze obnovit
   - zvyšuje bezpečnost i výkon
 - **RAID 6** 
   - podobný RAID 5
   - vyšší úroveň ochrany dat (dva paritní bity)
 - **RAID 10**
   - data jsou nejprve zrcadlena na 2 disky (RAID 1)
   - potom jsou rozdělena mezi více disků (RAID 0)

## SSD
 - Solid-state drive
 - **nevolatilní** úložiště
 - založen na soustavě **flash pamětí**
 - komunikuje přes stejná rozhraní jako HDD (**SATA**, PATA)
 - **absence mechanických částí**
   - méně náchylné k poškození

### Ukládání dat
 - paměťové buňky
 - **SLC** - nejrychlejší způsob uložení dat
 - **MLC**

## Optická média
 - zápis a čtení dat pomocí laseru

### CD
 - Compact Disc
 - 1 strana
 - 800 MB
 - verze - ROM, R (jednorázový zápis), RW (přepisovatelný)

### DVD
 - oboustranný zápis
 - vyšší kapacita oproti CD
   - 4,7 GB - 1 vrstva
   - 17 GB - 2 vrstvy

### BlueRay
 - Využívá laser s modrým zabarvením (nižší vlnová délka)
 - Ještě vyšší kapacita
   - 25 GB - 1 vrstva
   - 50 GB - 2 vrstvy

## Rozhraní

### SATA
 - Serial ATA
 - rychlost až 6 Gb/s (SATA 3)
 - stolní počítače

### PATA
 - Parallel ATA
 - dnes se již nepoužívá

### SAS
 - Serial Attached SCSI
 - rychlost až 22 Gb/s
 - pracovní stanice a servery

### SCSI
 - Pro servery
 - Small Computer System Interface
 - Paralelní sběrnice
 - Použité při RAID

### NVMe
 - Non-Volatile Memory Express
 - nahrazuje řadiče disku (SATA)
 - připojení k procesoru přímo pomocí PCIe
   - rychlé čtení a zápis
 
### NVMe M. 2.
 - Fyzicky menší disky oproti SATA diskům
 - Připojení do M. 2. slotu
 - možná verze pro SATA 
 - velmi vysoká rychlost čtení/zápis

