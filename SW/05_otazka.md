# 5 - Objektové programování I
 - Strukturované a objektové programování, objekt, třída, základní objektové vlastnosti
 - Třídy abstraktní, zapouzdřené a rozhraní

## Strukturované a objektové programování

 = paradigmata (styly programování)


__Strukturované__

 - Využívá bloků (`{}`), podmínek (`if`/`else`), cyklů (`for`/`while`), podprogramů ad. namísto skoků
 - __příklad__ - C, Pascal

__Objektové__:

- Obsahuje praktiky ze strukturovaného paradigmatu (podmínky/cykly)
- spojuje dohromady data a funkce (metody), které s nimi pracují
 - __příklad__ - C#, Java

## Třída + Struktura


### Třída
 - __referenční datový typ__
   - proměná odkazuje na instanci uloženou na __heapu__
   - proměnná tedy uchovává __pointer__ (__stack__)
 - podporuje dědičnost
   - s tím zároveň keywords jako `protected`
 - atributy jsou defaultně `private`

### Struktura
 - **hodnotový datový typ**
   - proměnná typu struktury obsahuje její instanci (**stack**)
 - je implicitně `sealed` → nepodporuje dědičnost
 - atributy jsou defaultně `private`
 - může mít kostruktor, atributy, metody, vlastnosti

## Základní objektové vlastnosti
 - přidružují k sobě data a funkce (metody), které s nimi pracují
 - jsou vzorem pro vytváření objektů

## Objekt
 - instance
 - místo v alokované v paměti, které uchovává třídu/strukturu
 - v programu můžeme vytvářet více objektů od stejné třídy/struktury
 - může být uložen v proměnné/kolekci

## Druhy tříd

### Abstraktní
 - `abstract`
 - nelze z ní vytvářet instance 
 - její jediné využití je, aby z ní dědila jiná třída

### Zapouzdřené
 - `sealed`
 - nelze z ní dále dědit
 - nemůže mít tedy žádného následníka

## Rozhraní
 - `interface`
 - definuje chování, které máme implementovat v nějaké třídě
 - podobné abstraktní třídě
   - nemůže však vytvářet defaultní implementaci metod
 - třída může implementovat __více rozhraní současně__, ale může __dědit pouze od jedné třídy__

