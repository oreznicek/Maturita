# 3 - Síťový operační systém - Linux
 - Výběr operačního systému (vhodné distribuce Linux)
 - Instalace operačního systému, připojení uživatelů
 - Druhy souborových systémů používaných v současných verzích OS
 - Koncepce souborového systému, stromová struktura, druhy souborů
 - Práva a oprávnění, nastavení oprávnění pro soubory (rwx), databáze uživatelů a hesel, Změna vlastníka a oprávnění

## Výběr distribuce
 - **Platforma**
   - Desktop (Ubuntu, Arch, Mint)
   - Server (Red Hat, Ubuntu Server)
   - Telefon (Android)
   - Superpočítač
 - **Hardwarové požadavky**
   - minimální
   - paměť RAM
   - frekvence procesoru
 - **Softwarová podpora**
   - záleží co chceme používat za software
   - usecase

### Rozdíly distribucí
 - doplňující software
 - package manager
 - grafická nadstavba (GUI)
   - GNOME
   - Xfce

## Instalace
 - ISO soubor → Rufus → vytvoření bootovacího zařízení (flash)

## Soubory
 - souborové systémy - ext4, btrfs
   - Windows je nativně nepodporuje
   - naopak Linux dokáže číst NTFS a exFAT
 - ext
   - extended filesystem
   - nejnovější ext4
   - nejstarší ext1 (1992)

### Adresářová struktura
 - FHS - Filesystem Hierarchy Standard
 - **/** - Kořenový adresář (root)
   - vše se nachází v tomto adresáři
   - může připomínat C:\
 - **/bin** - binaries
   - základní spustitelné soubory
   - nezbytné (zaručují chod systému)
 - **/boot** - soubory potřebné ke spuštění systému (zavaděč)
 - **/dev** - devices
   - Hardwarová zařízení 
   - abstrakce vstupních a výstupních zařízení
 - **/etc**
   - konfigurační soubory systémů a služeb, čitelná forma
 - **/home**
   - domovské adresáře všech uživatelů
   - Podobné C:\Users
   - V terminálu se k němu přistupuje pomocí ~
 - **/lib** - důležité sdílené knihovny pro chod binárních souborů v /bin a /sbin
 - **/root** - domácí adresář administrátora
 - **/usr**
   - aplikace a soubory používané běžnými uživateli

### Druhy souborů
 - **soubor (-)** - jméno + atributy
   - přípona souboru pouze usnadňuje práci uživatelům, ale soubor je definován svým obsahem
 - **adresář (d)**
   - speciální typ souboru 
   - jehož obsahem jsou jména souborů
 - **odkaz**
   - symbolický (l)
   - pevný (-)
 - **roura** (pipe)
   - umožňuje komunikaci mezi dvěma procesy (musí být jedna na čtení a jedna na zápis)
 - **soket**
   - umožňuje komunikace mezi dvěma procesy
   - i po síti
   - oproti rouře umožňuje komunikaci oběma směry

## Oprávnění a práva
 - permissions and rights
 - **read (r)**, **write (w)**, **execute (x)**
 - přikaz **chmod**
 - rwx rwx rwx
 - 421 421 421
 - 665 = rw-rw-r-x
 - **umask** - upravuje výchozí oprávnění
   - default hodnot - 0002

## Vlastnictví
 - Vlatsníkem souboru je
   - ten kdo ho vytvořil
   - ten kdo převzal vlastnictví
 - příkaz **chown**
   - změna vlastníka

## Databáze uživatelů a hesel
 - **passwd \<jmeno-uzivatele\>** - změnit heslo
   - root může změnit heslo bez znalosti aktuálního hesla
 - Soubor **/etc/passwd** obsahuje informace o uživatelích
 - Hesla jsou zašifrována v **/etc/shadow**
 - příkaz **id**
   - ukazuje UID uživatele, GID primární skupiny a GID skupin, v nichž je uživatel členem
