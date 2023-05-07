# 2 - Algoritmus, algoritmická složitost

 - algoritmus, algoritmická složitost
 - rekurze, náhodnost

## Algoritmus 
 - algoritmus je konečná posloupnost instrukcí, která se obvykle používá k řešení nějakého specifického problému

### Požadavky na algoritmus
 - **Elementárnost**
   - skládá se z konečného počtu jednoduchých (elementárních) kroků
 - **Konečnost**
   - pro každý jednotlivý vstup se musí skládat z konečného počtu kroků
 - **Obecnost**
   - neřešení jeden konkrétní problém, ale obecnou třídu problémů
 - **Determinovanost**
   - pro stejný vstup pokaždé vygeneruje stejný výstup
 - **Vstup a Výstup**
   - pro množinu vstupních dat nám vrátí nějaký výstup

### Zápis algoritmu

Algoritmus je součástí procesu **návrhu**, proto se pro jeho reprezentaci obvykle nepoužívá konkrétní syntax.

 1. vývojový diagram, blokové schéma, ...
 2. matematický zápis 
 3. pseudokód

## Asymptotická složitost

 - potřebujeme zjistit jak je algoritmus efektivní
   - pro následné porovnání s jinými algoritmy
 - změřit čas běhu programu nedává smysl → každý stroj je jinak výkonný

### Časová složitost (Operační)

= určuje množství výpočetního času potřebného k vyřešení algoritmu v závislosti na velikosti vstupních dat

 - **důležité:** výpočetní čas vyjadřuje počet operací

#### P versus NP problém
 - Pokud se dá řešení problému snadno zkontrolovat z hlediska správnosti, musí být i problém snad řešitelný?

### Paměťová složitost

= určuje množství paměťového prostoru potřebného k vyřešení algoritmu v závislosti na velikosti vstupních dat

 - pro různé vstupy o stejné velikosti se může doba běhu algoritmu lišit
   - proto obvykle bereme v potaz **nejhorší možný případ**
 - zapisuje se pomocí "**Big O notation**"

<table>
	<thead>
		<tr>
			<th>Notace</th>
			<th>Název</th>
			<th>Příklad algoritmu</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>O(1)</td>
			<td>konstantní</td>
			<td>Skok na prvek v poli dle indexu</td>
		</tr>
		<tr>
			<td>O(n)</td>
			<td>linearní</td>
			<td>Hledání prvku v neseřazeném poli</td>
		</tr>
		<tr>
			<td>O(log n)</td>
			<td>logaritmická</td>
			<td>Binární vyhledávání</td>
		</tr>
		<tr>
			<td>O(n<sup>2</sup>)</td>
			<td>kvadratická</td>
			<td>bubble sort, selection sort</td>
		</tr>
		<tr>
			<td>O(n<sup>3</sup>)</td>
			<td>kubická</td>
			<td>Násobení matic o n×n prvcích</td>
		</tr>
		<tr>
			<td>O(n!)</td>
			<td>faktoriálová</td>
			<td>problém obchodního cestujícího hrubou silou</td>
		</tr>
	</tbody>
</table>

## Rekurze
 = rekurze je stav, kdy je určitý objekt v nějakém smyslu součástí sebe samého
 - v informatice → opakované **vnořené volání** stejného **podprogramu**
 - součástí rekurzivní funkce je **ukončující podmínka**, která určuje, kdy se má vnořování zastavit
 - pokud není ukončující podmínka → může nastat nekonečná rekurze → **stack overflow**

### Výhody/nevýhody
 - \+ usnanění zápisu
 - \+ čitelnost kódu
 - \- náročnost na paměť a procesor

### Dělení rekurze
 - **Přímá**
   - podprogram volá přímo sám sebe
 - **Nepřímá**
   - vzájemné volání podprogramů vytvoří "kruh"
   - ve funkci A se volá funkce B a ve funkci B se volá opět A
 - **Linerání rekurze**
   - podprogram volám sám sebe pouze jednou
 - **Stromová rekurze**
   - podprogram volá sám sebe vícekrát
 
### Příklady

Fibonacciho posloupnost

```C
int fibonacci(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;

    return fibonacci(n-1) + fibonacci(n-2);
}
```

Faktoriál

```C
int factorial(int n) {
    if (n == 0)
        return 1;
    return n * factorial(n-1);
}
```

Quicksort, ...

## Náhodnost
 - využívá se, když potřebujeme určitou míru nepředvídatelnosti
 - nedeterministický proces
 - použití
   - hazardní hry (gambling)
   - kryptografie (volba klíče)

### Pravá náhodná čísla
 - náhodnost získaná pomocí **fyzikální/hardwarové** metody
 - **Metody generování**
   - měření šumu, vstupu od uživatele (pohyb myši)

### Pseudonáhodná čísla
 - algoritmy vytvářející dlouhé řetězce čísel, která jsou **zdánlivě náhodná** 
 - později se sekvence **opakují**
 - např. metoda prostředku čtverce (navrženo Von Neumannem)
