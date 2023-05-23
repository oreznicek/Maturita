# 12 - Směrování, směrovací tabulky, směrovací protokoly
 - Směrovací tabulky, záznamy, statické směrování, dynamické směrovací protokoly (RIP, RIPv2, RIPng, EIGRP, OSPF, BGP)
 - směrovací protokoly postavené na principu vzdáleného vektoru (distance-vektor) v porovnání s link-state
 - Výhody a nevýhody statického směrování oproti dynamickému směrování
 - Příklad vytvoření směrovacích tabulek staticky a pomocí směrovacího protokolu (např. RIP)

## Směrování
 - L3 vrstva OSI/ISO (síťová)
 - určuje, kam se má packet dostat
 - router posílá pakety do cizí sítě
 - pro přesun z naší sítě do jiné potřebujeme **router**
   - přesouvá pakety mezi sítěmi
   - router ovšem taky vidí pouze sítě do kterých patří
 - tento problém řeší **směrování**
   - data, která nemůžeme doručit přímo, doručíme někomu jinému
 - **směrování = proces hledání nejlepší cesty pro data, která nelze doručit přímo přes síť**
 
## Směrovací tabulky
 - routing table
 - udržuje informace o přímo připojených sítích, dále staticky a dynamicky naučené routy
 - každý záznam obsahuje:
   - adresu cílové sítě + masku
   - nexthop - odchozí interface
   - metrika (výhodnost cesty)
     - čím menší tím lepší
	 - počíta s počtem hopů, rychlostí, stabilitou a zatížeností
 - router v tabulce postupně hledá shodu s nejvýhodnější cestou

## Statické vs dynamické směrování
 1. **statické**
    - ručně přidané
    - méně výpočetně náročné
 2. **dynamické**
    - automaticky přidané záznamy
	- router se učí cestu k sítím, které nezná
	  - u dynamického směrování nemusí administrátor znát topologii sítě
	  - jednodušší konfigurace
	  - jakékoliv změny se okamžitě šíří díky směrovacím protokolům

## Dynamické směrovací protokoly

### Link-state protokoly
 - **vhodné pro větší sítě**
 - router zjišťuje, zda má v síti další routery a testuje jejich dostupnost
 - poté routery informuje o jejich sousedech
   - každý router ví o všech ostatních
 - takto **zmapuje celou síť**
 - podle toho pro paket určuje nejlepší cestu 
 - pro rozlehlejší sítě nutno rozdělit na části kvůli zatěžování sítě
 - **metrika** → záleží na mnoha faktorech (šířka pásma, odezva)
 - **OSPF**

### Distance-vector protokoly
 - **vhodné pro menší sítě**
 - routery neznají strukturu sítě, pouze své nejbližší sousedy
 - vyměňují si kompletní kopii směrovacích tabulek
 - routery periodicky vysílají a díky grafovému algoritmu vypočítají vzdálenost ostatních uzlů
 - vzniká riziko zacyklení
 - **metrika** → počítá se podle počtu hopů
 - **RIP**

### RIP
 - Routing Information Protocol
 - **distance-vector** protokol
 - nejjednodušší protokol s jednoduchou konfigurací
 - malé sítě (max. 15 skoků)
 - hloupá metrika
 - první verze (**RIP**) posílal směrovací tabulky broadcastem, což zatěžovalo síť
 - druhé verze (**RIPv2**) posílá směrovací tabulky multicastem, navíc umí pracovat s podsítěmi a maskami sítě (CIDR)
 - nejnovější verze (**RIPng**) má podporu IPv6 a umožňuje provádět lepší autentizace

### OSPF
 - Open Shortest Path Find
 - **link-state** protokol
 - provádí změny v tabulace na základě změn v síti
 - velké sítě
 - je velmi paměťově náročný

 o **hybridní** protokol
### EIGRP
 - Enhanced Interior Gateway Routing Protocol
 - **hybridní** protokol
 - pravidelně kontroluje, zda je trasa k dispozici
 - místo směrovací tabulky posílá změny topologie
 - podpora pro CIDR a proměnnou délku podsítí
 - MD5 autentizace

### BGP
 - Border Gateway Protocol
 - **distance-vector** protokol
 - používají ho providěři (ISP)
 - směrovací tabulky obsahují stovky tisíc záznamů
 - vyměňují pouze informace o změnách, nikoliv celé tabulky
