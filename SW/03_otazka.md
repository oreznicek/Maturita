# 3 - Strukturované datové typy
 - Strukturované datové typy, objekt, pole, kolekce, generické kolekce
 - třída, struktura (rozdíly)

## Složený datový typ
 - datové typy skládající se z několika komponent (členů)
 - **homogenní** - komponenty jsou stejného typu
 - **heterogenní** - komponenty jsou různého typu

## Třída + Struktura

### Proč vznikly?
 - abychom přidružili k sobě data a funkce

### Třída
 - **referenční datový typ**
   - proměnná odkazuje na instanci uloženou na **heapu**
   - proměnná se tedy uchovává **pointer** (**stack**)
 - podporuje dědičnost
   - s tím zároveň keywords jako `protected`
 - atributy jsou defaultně `private`

### Struktura
 - **hodnotový datový typ**
   - proměnná typu struktury obsahuje její instanci (**stack**)
 - je implicitně `sealed` → nepodporuje dědičnost
 - atributy jsou defaultně `private`
 - může mít kostruktor, atributy, metody, vlastnosti

```C#

Vec2 point = new Vec2(5, 4);
Console.WriteLine(point);
Console.WriteLine(point.X);
// Output:
// (5, 4)
// 5

struct Vec2
{
    public Vec2(int x, int y)
    {
        X = x;
        Y = y;
    }

    public int X { get; set; }
    public int Y { get; set; }

    public override string ToString() => $"({X}, {Y})";
}

```

### Objekt
 - místo v paměti, kde máme uloženou **instanci třídy/struktury**
 - v programu můžeme vytvářet více objektů od stejné třídy/struktury
 - může být uložen v proměnné/kolekci

## ArrayLike

### Pole
 - posloupnost prvků stejného datového typu 
 - má **konečný počet prvků** (neměnný)
 - je uloženo v souvislé oblasti paměti
 - k jednotlivým prvkům se přistupuje přes **index**
 - homogenní datový typ
   - může být i heterogenní → `object[]`
 - můžeme vytvářet **vícerozměrná pole**

### Kolekce
 - datové struktury, které rozšiřují funkcionalitu pole
 - vnitřně jsou **implementována jako pole**
 - useful, když potřebujeme spravovat skupinu objektů
 - mají **proměnný počet prvků**
 - `ArrayList` - dynamické pole (měnící se velikost)
 - `Hashtable`
 - `Queue` - FIFO
 - `Stack` - LIFO

### Generické kolekce
 - generický typ slouží jako zástupce pro budoucí datový typ
 - datový typ se specifikuje ve chvíli vytvoření instance
 - `List<T>` - generický ArrayList
 - `Queue<T>` - generická Queue
 - `Stack<T>` - generický Stack

