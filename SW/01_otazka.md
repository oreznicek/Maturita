# 1 - Základní programové konstrukce

 - Proměnná, Datový typ, Reference, Hodnota
 - Program, Podprogram
 - Podmínky, Cykly, Operátory

## 1. Proměnná
 - Proměnná je **symbolické jméno** pro nějakou informaci, která je uchovaná v paměti (RAM) při běhu programu
 - Pomocí tohoto **symbolického jména** se můžeme na informaci ve svém kódu **odkazovat** nebo ji **měnit**
 - Proměnnou deklarujeme specifikováním **datového typu** a názvu proměnné
 ```C
    int cislo; // Deklarace proměnné
    cislo = 5; // Inicializace proměnné
 ```
 - Oba dva tyto kroky se dají napsat do jednoho řádku:
 ```C
    int cislo = 5; // Deklarace + Inicializace
 ```
### 1.1 Alokace paměti
 - Proměnnou můžeme přidat na vrchol **zásobníku** (stack)
 - V takovém případě je paměť automaticky uvolněna, po skončení **scopu** (blok kódu, kde je proměnná validní), ve kterém byla deklarována. (Mluvíme o lokální proměnné)
 - **Scope** nám pomáhá předejít kolizím jmen u proměnných
 - Proměnné s neznámou velikostí při běhu programu se ukládají na **haldu** (heap)
 - Proměnná poté představuje **referenci** na místo v paměti, kde je uložená její hodnota
   - týká se to např. datového typu **string** (což je vlastne pole znaků)
   - pole je ve skutečnosti ukazatel na první prvek v daném poli
 - Rozdíl mezi zásobníkem a haldou je, že na haldu se musí paměť dynamicky alokovat a dealokovat

 <div align="center">
 	<img width="50%" alt="Heap and Stack memory" src="./img/stack_heap_memory.gif" />
 </div>

## 2. Datový typ
 - U proměnných musíme definovat tzv. datové typy 
   - pokud tedy nejsme v dynamicky typovaném programovacím jazyce jako je např. Python
 - Datový typ určuje hodnoty nebo rozsah hodnot, kterých může nabývat proměnná (nebo konstanta)
 - Pro datové typy poté interpret nebo kompilátor provádí tzv. **typové kontroly**
   - zkontroluje např. jestli provádíte s typem povolenou operaci
   - příklad nepovolené operace může být inkrementace proměnné datového typu bool
   - **pokud se chceme typovým kontrolám vyhnout** - tak v jazyce C existuje pro to speciální datový typ **void**
### 2.1 Druhy datových typů
 1. Jednoduché datové typy
    - jednoduché (elemenární) datové typy jsou většinou přímo **zabudovány do jazyka**
    - jejich **skládáním** pak mohou vznikat **složitější typy**

## 3. Reference
 - Reference umožňuje nepřímý přístup k určitým datům
 - Přístup k datům, na které reference odkazuje nazýváme **dereferencí**
 - Reference je uvnitř vlastně **pointer** (ukazatel), ale pro nás se bude chovat jako normální proměnná
   - reference před námi vlastně schová veškerou funkcionalitu ukazatelů
 - Reference nám tedy umožnuje přístup k nějaké proměnné pod jiným identifikátorem
 - Typicky nebudeme vytvářet referenci pro jednoduché datové typy jako je integer, ale pro typy složené, které jsou uloženy na haldě (třídy, pole)
 - Pokud budeme tedy pole předávat do nějaké funkce, tak je efektivnější ho předat jako referenci, než znovu jeho obsah kopírovat

```C#
void DivideByTwo(ref int n) {
    n = n / 2;
}

int number = 6;

DivideByTwo(ref number);

Console.WriteLine(number);
// Output:
// 3
```

## 4. Hodnota
 - Hodnota se v programování vždycky nachází za nějakou proměnnou nebo referencí
 - její obsah tak musí odpovídat datovému typu

## 5. Program
 - posloupnost instrukcí, kterou realizuje typicky CPU
 - dříve se zapisoval pomocí **strojových instrukcí** (assembler)
 - dnes pomocí **programovacích jazyků**
   - kompilované
     - zdrojový kód je přeložen do strojového kódu a následně do spustitelného souboru
   - interpretované
     - je vykonáván interpreterem
	 - interpreter je sám o sobě program (pomalejší)
 - zdrojový kód je forma programu čitelná člověkem

### 5.1 Co se děje, když spustíme program
 1. Spustitelný soubor je vyžádán ke spuštění
 2. Operační systém ho načte do paměti a spustí proces
 3. Jakmile se CPU přepne na tento proces tak může:
    - načíst instrukci (fetch)
	- dekódovat instrukci (decode)
	- provést instrukci (execute)

Procesů běží na úrovni operačního systému víc. Jsou řazeny podle priority a následně v tomto pořadí spouštěny.

## 6. Podprogram
 - blok kódu, který obsahuje řadu příkazů
 - ty se spustí tzv. **voláním podprogramu**

### 6.1 Použití
 - rozklad složitých problémů na jednodušší
 - odstranění opakování kódu
   - šetříme paměť programu
 - odstínění detailů implementace od konkrétního použití funkce
   - nemusím vědět jak funkce funguje uvnitř

## 7. Podmínky (podmíněné větvení)
 - příkazy, které větví program (rozhodují se) na základě vstupní podmínky

**if** / **else if** / **else**

```C#
string name = "Pepa";

if (name == "Martin") {
   Console.WriteLine("Ahoj Martine!");
}
else if (name == "Marek") {
   Console.WriteLine("Dobrý den, pane učiteli.");
}
else {
   Console.WriteLine("Tebe neznám.");
}
// Output:
// Tebe neznám.
```

**switch** / **case**

```C#
enum Day {
   Monday = 0,
   Tuesday,
   Wednesday
}

Day today = Day.Tuesday;

switch (today) {
    case Day.Monday:
        Console.WriteLine("Pondělí");
        break;
    case Day.Tuesday:
        Console.WriteLine("Úterý");
        break;
    case Day.Wednesday:
        Console.WriteLine("Středa");
        break;
}
// Output:
// Úterý
```

## 8. Cykly
 - opakují nějakou část kódu

Cyklus s podmínkou na začátku.

```C#
while (false) {
    Console.WriteLine("Coding is nice");
}
// Output:
// 
```

Cyklus s podmínkou na konci. Jednou proběhne, než se poprvé zkontroluje podmínka.

```C#
do {
    Console.WriteLine("Coding is nice");
}
while (false);
// Output
// Coding is nice
```

Cyklus s pevným počtem opakování.

```C#
for (int i = 0; i < 5; i++) {
    Console.Write($"{i} ");
}
Console.Write("\n");
// Output:
// 0 1 2 3 4
```

## 9. Operátory
 - **Aritmetické**
   - sčítání (x + y)
   - odčítání (x - y)
   - násobení (x \* y)
   - dělení (x / y)
   - modulo (x % y)
   - inkrementace (x++) 
   - dekrementace (x--)
 - **Srovnávací (relační)**
   - větší než (>)
   - menší než (<)
   - větší nebo rovno (>=)
   - menší nebo rovno (<=)
   - rovno (==)
 - **Logické**
   - A zároveň (&&)
   - Nebo (||)
   - Negace (!)
 - **Bitové**
   - AND (&)
   - OR (|)
   - XOR (^)
   - Negace (~)
   - Shift left (<<)
   - Shift right (>>)
 - **Přiřazení**
   - proměnná = hodnota
   - Kombinace dalších operátorů s = (+=, &=, ...)
 - **Ternární operátor**
   - (podminka) ? (if blok) : (else blok)
 - **Lamda operátor**
   - používá se k vytvoření anonymní funkce
   - (parameters) => { (body) }
 - **Postfix**
   - indexování ([i])
   - inc, dec
   - member access (.)
   - pointer member access (->)
   - čárka operátor
