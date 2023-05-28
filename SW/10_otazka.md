# 10 - Paralelní programování
 - Asynchronní a paralelní programování

## Asynchronní programování
 - asynchronní volání neblokují chod aplikace
 - **použití** - aby nezamrzlo UI při načítání dat z databáze

### Async, await
 - klíčová slova, která usnadňují vytváření asynchronního kódu
 - kompilátor řeší asynchronní spouštění za nás → my se můžeme soustředit na vytváření programu
 - `await` - proveď asynchronně, ale počkej na výsledek
 - `async` - modifikátor, který specifikuje, že daná metoda (nebo lambda výraz) je prováděna asynchronně

### System.Threading.Tasks
 - `Task` - představuje asynchronní operaci
 - spuští se asynchronně na threadu z ThreadPoolu
 - ale všechno může běžet pouze na jedno logickém procesoru

## Paralelní programování
 - rozdělíme úlohu do několika podúloh
 - každou podúlohu poté spustíme v samostatném vlákně
 - aby se úloha dala paralelizovat, tak musí být jednotlivé částí vzájemně nezávislé
   - paralelní řazení → předchází rozdělení podle pivota
   - každá část se tak může nezávisle seřadit a dohromady bude pole seřazeno
 
### System.Threading
 - knihovna, která umožňuje vytvářet a manipulovat s jednotlivými vlákny
 - `Thread`
   - `new Thread(new ThreadStart(Worker))` - vytvoříme nové vlákno
   - `.Start()` - spustíme úlohu v novém vlákně
   - `.Sleep()` - zastaví vlákno na určený čas
   - `.Join()` - čekáme než se úloha v jiném vlákně dokončí

#### System.Threading.Task.Parallel
 - `Parallel.For(odkud, kam, metoda);`
 - `Parallel.ForEach(myEnumerable, (obj) => {});` 
