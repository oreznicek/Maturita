# 1 - Základní programové konstrukce

 - Proměnná
 - Datový typ
 - Reference
 - Hodnota
 - Program
 - Podprogram
 - Podmínky
 - Cykly
 - Operátory

## 1. Proměnná
 - proměnná je **symbolické jméno** pro nějakou informaci, která je uchovaná v paměti (RAM) při běhu programu
 - pomocí tohoto **symbolického jména** se můžeme na informaci ve svém kódu **odkazovat** nebo ji **měnit**
 ```C class="lineNo"
    int cislo; // Deklarace proměnné
    cislo = 5; // Inicializace proměnné
 ```
 - oba dva tyto kroky se dají napsat do jednoho řádku:
 ```C class="lineNo"
    int cislo = 5; // Deklarace + Inicializace
 ```

## 2. Datový typ
 - u proměnných musíme definovat tzv. datové typy
   - pokud tedy nejsme v dynamicky typovaném programovacím jazyce jako je např. Python
 - datový typ definuje význam hodnot, kterých může nabývat proměnná (nebo konstanta)
 - pro datové typy poté interpret nebo kompilátor provádí tzv. **typové kontroly**
   - zkontroluje např. jestli provádíte s typem povolenou operaci
   - příklad nepovolené operace může být inkrementace proměnné datového typu bool
   - **pokud se chceme typovým kontrolám vyhnout** - tak v jazyce C existuje pro to speciální datový typ **void**

### 2.1 Druhy datových typů
 1. Jednoduché datové typy
    - jednoduché (elemenární) datové typy jsou většinou přímo **zabudovány do jazyka**
    - jejich **skládáním** pak mohou vznikat **složitější typy**