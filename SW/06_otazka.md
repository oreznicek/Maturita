# 6 - Objektové programování II
 - Zapouzdření, dědičnost, polymorfismus
 - přepsání a překrytí (virtual, override, new)
 - přetížení

## Zapouzdření
 - __encapsulation__
 - zabalení dat a metod a restrikce přístupu k nim
 - používá se pro skrytí dat ve třídě
 - `private` - ke členům třídy má přístup jen daná třída (nebo vnořné třídy)
 - `protected` - ke členům třídy mají přístup třídy, které z ní dědí
 - `internal` - přístup odkudkoli v daném sestavení (exe/knihovna)
 - `public` - ke členům třídy je přístup odkudkoli

## Dědičnost
 - __inheritance__
 - následník používá, rozšiřuje nebo modifikuje chování rodičovské třídy
 - **v C# lze mít pouze 1 rodiče**
 - konstruktory se nedědí, každá třída si musí definovat vlastní
   - spuštění původního pomocí `: base()`
 - podporuje **koncept znovupoužitelnosti**, méně redundantního kódu
 - ze třídy `sealed` nelze dědit

## Polymorfismus
 - podstatou polymorfismu je, že máme nějaké třídy
 - např. `Student` a `Teacher`
 - ty dědí od nějaké obecnější třídy `Person`
 - ke studentovi se můžeme chovat jako ke studentovi
 - nebo se k němu můžeme chovat jako k osobě, ale on nám stejně může říct konkrétnější věci o sobě

### Přepsání
 - `override`
 - přepíše metodu předchůdce
 - i když voláme z proměnné typu předchůdce, tak se zavolá přepsaná metoda z následníka
 - předchozí funkce musí být `abstract` nebo `virtual`
 - virtuální přepsat nemusíme, ale abstraktní ano

### Překrytí
 - `new`
 - používáme implementaci následníka místo implementace předchůdce
 - když voláme z předchůdce, zavolá se metoda předchůdce

## Přetížení
 - __overloading__
 - definování metody se stejným identifikátorem (jménem)
 - metoda se musí lišit v počtu nebo typu parametrů
