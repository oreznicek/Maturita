# 9 - Návrhové vzory II
 - Návrhové vzory pro skrývaní implementace, optimalizace rozhraní

## Vzory pro skrývání implementace

### Proxy
 - Zástupce
 - umožňuje řídit přístup k objektu přes jiný zastupující objekt
 - **Remote proxy**
   - zastupuje objekt umístěný někde jinde
   - zařizuje serverovou komunikaci se vzdáleným objektem
   - měl by být připraven i na přerušení spojení (vyhodit výjimku)
 - **Virtual proxy**
   - zastupuje jiný objekt
   - vytvoření objektu nechává na poslední chvíli a chování objektu se předstírá
   - lazy loading obrázků z databáze
 - **Protection proxy**
   - zakrývá identitu zastupovaného objektu
   - nabízí jen část metod zastupovaného objektu
   - lze implementovat přístupová práva
 - **Smart reference**
   - doplnění objektu o další funkce 
   - virtuální zástupce je také smart reference → rozhoduje kdy přistoupí k originálnímu objektu a kdy načte hodnoty z cache

### Command
 - Příkaz
 - zapouzdření metody do objektu
 - **jako Command ve WPF**

### Iterátor
 - přístup k objektům uloženým v kolekci
   - možnost procházení (cyklem)
 - nemusíme znát jak funguje uvnitř, zvenku lze skrz něj interovat
 - např. implementace iterátoru pro binary search tree

### Template method
 - šablonová metoda
 - definuje kostru algoritmu uvnitř abstraktní třídy
 - rodičovská třída deklaruje jak by měl vypadat algoritmus
 - následníci tento algoritmus poté implementují

## Vzory pro optimalizaci rozhraní

### Adapter / Wrapper
 - převede zastaralé / nehodící se / chybné rozhraní třídy na rozhraní, které klient očekává
 - zabezpečuje spolupráci tříd a usnadňuje implementaci nových
 - může celou třídu zabalit do nové nebo z ní dědit

### Facade
 - Fasáda
 - zjednodušuje komunikaci mezi uživatelem a systémem
 - vytvoření jednotného rozhraní pro logickou skupinu tříd
 - zabalí komplikovaný subsystém do jednoduššího uceleného rozhraní

### Composite
 - Strom
 - doporučené řešení situace, kdy se pracuje se stromovou strukturou
 - jednoduché a z nich složené (kompozitní) objekty
 - např. binární strom
