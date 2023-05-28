# 20 - Sériová rozhraní mcu
 - Popis sériových sběrnic USART, RS422/485, SPI/Microwire, i2C, 1Wire, CAN
 - Popis sériového portu Atmel AVR

## USART
 - **TX** - transmitter
 - **RX** - receiver
 - transmitter začne vysílat kdykoli chce
 - před začátkem komunikace se musíme ujistit, že TX a RX mají stejná nastavení
   - přenosová rychlost (9600 baud/s)
   - velikost dat, které budeme posílat (8 bits)
   - jak vypadá start a stop bit
 - když se nic neděje je tam 1 
   - start bit → sestupná hrana
   - stop bit → náběžná hrana
 - 1/9600 = 104 mikrosekund
 - start bit ... 104 ... půjdeme do půlky prvního bitu (52) ... přečteme první bit
 - potom se posouváme o 104 mikrosekund až do konce a přečteme všechny bity
 - jakmile máme všechny bity čekáme na stop bit → náběžná hrana

### Charakteristiky
 - **rychlost** - 100 kb/s
 - **vzdálenost** - 100 m
 - **napěťové úrovně**: +-12/5/15 V
 - **řízení komunikace** - P2P
 - 

## I<sup>2</sup>C
 - **sériová synchronní sběrnice**
 - byla vyvinuta společností Phillips
 - **SDA** - data
 - **SCL** - hodiny

### Charakteristiky
 - **rychlost** - 3,4 Mb/s
 - **vzdálenost** - 1 m
 - **napěťové úrovně**: 3-5 V
 - **řízení komunikace** - multi-master (MM)
 - **duplexita** - half duplex
 - **zabezpečení** - nemá

## SPI

