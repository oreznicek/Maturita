# 6 - Spolehlivá síť - STP, Etherchannel, FHRP

 - Problém vytváření záložních cest, redundantní sítě
 - Redundance na vrstvě L2, protokol STP (druhy), smyčky, broadcastová bouře, STA, priorita, výpočet 
 - Agregace linky, Etherchannel, protokoly, výhody, konfigurace (switch cisco)
 - Virtuální výchozí brána, redundance směrovače, protokoly, nastavení FHRP (router cisco)

## Problém vytváření záložních cest
 - Více cest na L2 → smyčky → STP
 - Více cest na L3 → použijeme routy
 - Více default gateway → FHRP

## Redundantní sítě

## STP
 - Spanning Tree Protocol
 - zabraňuje vzniku smyček **blokováním portů**
 - **smyčka** = 3 a více switchů tvoří dohromady kruh
 - zajišťuje redundanci v případě poruchy

### Broadcastová bouře
 - abnormálně velký počet broadcastů, který může přetížit celou síť
 - může vzniknout v případě smyčky na L2

### STA
 - Spanning Tree Algorithm
 - 
