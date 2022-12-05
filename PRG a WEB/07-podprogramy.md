# 7 - Podprogramy
podprogramy, funkce, delegáty, lambda operátory

asynchronní funkce, yield return, Task, ?

## 1. Podprogram
 - Podprogram je blok kódu, který obsahuje řadu příkazů. Ty se spustí zavoláním podprogramu.
 - Podprogram může mít **parametry**, které určují, s jakými daty má pracovat
 - Může také vracet návratovou hodnotu
 - V některých jazycích se podprogramy rozlišují na **funkce** a **procedury** podle toho jestli vrací hodnotu nebo ne
 - V objektovém programování se podprogramy tříd nazývají **metody**
 - Používání procedur je důležitým nástrojem **strukturovaného programování** a umožňuje zavádět do programů vyšší míru **abstrakce**

### 1.1 Důvody použití
Proč bychom měli rozdělovat program na podprogramy?
 - rozklad složitých problémů na jednodušší
 - odstranění opakování kódu v programu 
   - šetříme paměť programu
 - vytvořením modulu nebo knihovny -> můžeme použít v jiných programech 
   - vyhneme se repetetivnímu kódu
 - odstínění detailů implementrace od konkrétního použití funkce 
   - nemusím vědět jak funkce funguje uvnitř
   - můj názor: napíšu volání funkce a nechám na pozdější implementaci

### 1.2 Zásobníková paměť
 - Vnitřní implementace podprogramů se realizuje pomocí zásobníku
 - Zásobník jako takový je složená datová struktura typu **LIFO** (Last In First Out)
 - Každá procedura vytvoří nový vstup, který se nazývá **zásobníkový rámec**
 - Při vrácení se z podprogramu instrukcí **RETURN** je rámec ze zásobníku odstraněn a tím se vytvoří místo pro další podprogramy
 - Každý rámec obsahuje data k odpovídajícímu volání podprogramu
   - vstupní parametry
   - lokální proměnné
   - návratová adresa

#### 1.2.1 Stack pointer
 - Zásobník je obvykle souvislá oblast paměti a stack pointer (SP neboli **ukazatel na vrchol zásobníku**) může být zvolen jako nejnižší nebo nejvyšší adresa v této oblasti
 - Takže voláním více podprogramů se může adresa SP buď zvětšovat nebo zmenšovat
 - Spíše se asi používá, že SP je nejvyšší adresa, takže voláním podprogramu se adresa SP zmenšuje 

Zásobník je tedy jeden z nejdřívějších způsobů automatického managování paměti.
Jednou z jeho dalších velkých výhod je, že umožňuje rekurzivní volání.

## 2. Funkce
 - Nebo bych měl říct spíš **metody**?
   - metody jsou funkce deklarované uvnitř tříd
   - a jelikož v jazyce C# nemůžeme funkci deklarovat vně třídy, tak tam jsou pouze metody
 - Můžeme ale definovat tzv. **lokální funkce** (2.2)
 - Metody jsou deklarovány ve **třídě**, **struktuře** nebo **rozhraní**
 - Hlavním vstupním bodem každé C# aplikace je metoda "Main"
   - od verze C# 9 se nemusí explicitně zahrnout, místo toho je jeden soubor **nejvyšší úrovně**
   - může však existovat pouze jeden! Jinak C# vyhodí následující error:
     - CS8802 Pouze jedna jednotka kompilace může mít příkazy nejvyšší úrovně.

### 2.1 Syntax metody
V jazyce C# se všechny tyto části společně nazývají podpis metody (deklarace)
 - úroveň přístupu (private, public, protected, internal, file)
 - volitelné modifikátory (abstract, sealed, virtual, static, override)
 - návratová hodnota (object, void)
 - název metody
 - parametry metody

#### 2.1.1 Přístup k metodě
 - Volání metody objektu se dělá přidáním tečky, názvu metody a jednoduchých závorek
 - Přesně v tomto pořadí

 ```C#
internal class Hello
{
	public void Print()
	{
		Console.WriteLine("Hello World!");
	}
}

// Následně v Main metodě
Hello obj = new Hello();
obj.Print();
 ```

#### 2.1.2 Předání parametrů
 - podle hodnoty - vytvoří se kopie proměnné v metodě
 - podle odkazu - předání přístupu k proměnné dané metodě

 ```C#
void Increment(ref int value)
{
	value++;
}

int number = 5;
Increment(ref number);

Console.WriteLine(number);
// Output:
// 6
 ```

#### 2.1.3 Proměnný seznam parametrů
 - Můžeme definovat parametr **params**, který přijímá proměnlivý počet argumentů
 - Typ parametru musí být jednorozměrné pole
 - Po klíčovém slově params nejsou povoleny žádné další parametry

 ```C#
void UseParams(params object[] list)
{
	for (int i = 0; i < list.Length; i++)
	{
		Console.Write(list[i] + " ");
	}
	Console.WriteLine();
}

UseParams(1, 'a', "test"); // jednotlivé parametry oddělené čárkou
UseParams(); // prázdý seznam parametrů

object[] arr = { 'b', 6, "hello" };
UseParams(arr); // předání pole argumentů
// Output:
// 1 a test
// 
// b 6 hello
 ```

#### 2.1.4 Parametry vs Argumenty
 - Parametry se definují při deklaraci metody
 - Argumenty jsou konkrétní hodnoty pro jednotlivé parametry
 - Název argumentu nemusí být stejný jako název parametru
 - Datové typy argumentu a parametru ale musí být kompatibilní

 ```C#
int Sum(int x, int y) // x a y jsou parametry
{
	return x + y;
}

int cislo1 = 5, cislo2 = 8;
int sum = Sum(cislo1, cislo2); // cislo1 a cislo2 jsou argumenty

Console.WriteLine(sum);
 ```

#### 2.1.5 Pojmenované argumenty
 - Pojmenované argumenty neobsahují porovnání pořadí argumentů s pořadím parametrů
 - Pokud si tedy nepamatujete pořadí parametrů, ale znáte jejich názvy, můžete argumenty odeslat v libovolném pořadí

 ```C#
void PrintOrderDetails(string sellerName, int orderNum, string productName)
{
	Console.WriteLine($"Seller: {sellerName}, Order #: {orderNum}, Product: {productName}");
}

PrintOrderDetails("Gift Shop", 31, "Red Mug");
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
 ```

#### 2.1.6 Volitelné argumenty

 ```C#
void ExampleMethod(int required, string optionalstr = "default string", int optionalint = 10);

//ExampleMethod(3, ,4);
ExampleMethod(3, optionalint: 4);
 ```

#### 2.1.7 Vrácené hodnoty
 ```C#
return [návratová hodnota];
return; // když je návratový typ void
 ```

 Pokud je **void** návratový typ, **return** příkaz bez hodnoty je stále užitečný k zastavení provádění metody.

### 2.2 Lokální funkce
 - Můžeme ale definovat tzv. lokální (místní) funkce
 - Ty jsou vnořené do jiného člena a pouze z něj mohou být volány
 - Lokální funkce můžeme deklarovat a volat z:
   - Metody, zejména metody iterátoru a asynchronní metody
   - Konstruktory
   - Přístupové objekty vlastností
   - Přistupové objekty událostí
   - Anonymní metody
   - Výrazy lambda
   - Finalizační metody
   - Další místní funkce

### 2.3 Asynchronní metody

blank

### 2.4 Iterátory

blank

## 3. Delegáty
 - Delegát je něco jako pointer na funkci
 - Když vytvoříte instanci delegátu, můžete jí přidružit s jakoukoli metodou s kompatibilním podpisem a návratovým typem
   - danou metodu můžete zavolat prostřednictvím instance delegátu
 - Delegáty se používají pro předávání metod jako argumentů jiným metodám
 - Delegátu můžeme přiřadit jakoukoli metodu (i z jakékoli přístupné třídy nebo struktury) odpovídající typu delegátu
 - Takže můžeme programově změnit volání metod nebo připojit nový kód do existujících tříd
 - Díky možnosti odkazovat na metodu jako parametr jsou delegáty ideální pro definování metod zpětného volání (**callback**)

### 3.1 Vlastnosti delegátů
 - Jsou podobné ukazatelům funkcí v jazyce C++
 - Umožňují předávání metod jako parametrů
 - Lze použít pro definování metod zpětného volání (callback)
 - Delegáty lze zřetězit (je možné volat větší počet metod v rámci jedné události)
 - Metody nemusí přesně odpovídat typu delegáta
 - Výrazy lambda jsou stručnější způsob psaní vložených bloků kódu

#### 3.1.1 Zřetězení delegátů

Řetězení delegátů se realizuje pomocí operátorů + a -.

Je potřeba říct, že pokud delegát používá referenční parametry, odkaz se předává postupně každé ze tří metod a všechny změny podle jedné metody jsou viditelné pro další metodu.

Když některá z metod vyvolá výjimku, která není zachycena v metodě, je tato výjimka předána volajícímu delegáta a nejsou volány žádně další metody v seznamu volání.

 ```C#
// namespace _07_podprogramy
internal delegate void Del(string message);

internal class MethodClass
{
	public void Print1(string message)
	{
		Console.WriteLine("1 - " + message);
	}

	public void Print2(string s)
	{
		Console.WriteLine("2 - " + s);
	}
}

// V Program.cs
MethodClass obj = new MethodClass();

void PrintMethod(string retezec)
{
	Console.WriteLine("3 - " + retezec);
}

Del d1 = obj.Print1;
Del d2 = obj.Print2;
Del d3 = PrintMethod;

Del allTogether = d1 + d2 + d3;
allTogether -= d2;
allTogether("Hello World");

Console.WriteLine();

foreach (var item in allTogether.GetInvocationList())
{
	Console.WriteLine(item.Method);
}
 ```

## 4. Anonymní funkce
 - Anonymní funkce je blok kódu, který nemá identifikátor
 - Obvykle se používá pro předávání do jiných funkcí 
 - Někdy se jí také říká **arrow function**
 - Anonymní funkce poskytují techniku jak předat blok kódu jako parametr delegátu

## 5. Lambda operátor
 - používá se k vytvoření anonymní funkce 

 ```C#
(vstupni_parametry) => výraz // Výraz lambda

(vstupni_parametry) => { příkaz1; příkaz2; ... příkazN; } // Příkaz lambda
  ```

 - Výrazová lambda vrátí výsledek výrazu uvedeného za šipkou
 - Příkaz lambda je podobný, ale můžeme napsat víc příkazů

Výrazy lambda můžete použít např. při psaní LINQ

 ```C#
int[] numbers = { 2, 3, 4, 5 };
var squaredNumbers = numbers.Select(x => x * x);
Console.WriteLine(string.Join(" ", squaredNumbers));
// Output:
// 4 9 16 25
 ```
Výraz lambda, který má jeden parametr a vrací hodnotu se dá převést na delegáta typu Func<T, TResult>

 ```C#
Func<int, int> square = x => x * x;
Console.WriteLine(square(5));
// Output:
// 25
 ```

Ale výraz lambda, který má dva parametry a nevrací žádnou hodnotu, nelze převést na delegáta Action<T1, T2>
