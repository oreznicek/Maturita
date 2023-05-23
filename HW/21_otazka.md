# 21 - Procesory
 - Struktura současných procesorů (x86/64)
 - Techniky optimalizace provádění instrukcí
 - Snižování spotřeby
 - Rozšířené instrukční sady

## CPU
 - Samotné jádro (ALU)
 - Řadíč (Control unit)
   - Stará se o řízení a koordinaci celého systému
 - Registry
 - Vyrovnávací paměť (cache)
   - L3 největší a nejpomalejší paměť → společná pro všechny jádra
   - L2 rychlejší a menší než L3
   - L1 nejmenší, ale nejrychlejší a je rozdělena na instrukce a data

### Části ALU
 - L1 Cache
 - Pipelining
 - Branch predictor (předvídání skoků)
 - Integer a Float jednotky

## Struktura současných procesorů
 - Moderní x86-64 procesory používají upravenou Harvardskou a Von Neumannovu architekturu jelikož je L1 Cache rozdělena na data a instrukce

## Optimalizace provádění instrukcí

### CISC
 - Měl usnadnit práci programátorů
 - složitější instrukce = assembler se dal používat skoro jako HLL
 - **Problémy:**
   - Volání a návrat z podprogramu (musí se zapomenout rozpracované instrukce z fronty instrukcí (pipeline))
 - Díky tomu vzniklo - **predikce skoků**, **vybalování smyček**

### RISC
 - jednoduché instrukce
 - velké množství pracovních registrů (operace se provádí s těmito registry)
 - **Problémy:**
   - Volání a návrat z podprogramů ... **prediktory skoků**

### Zvýšení výpočetního výkonu procesorů
 - zmenšování velikosti tranzistorů a spojů mezi nimi
 - snižování napájecího napětí
 - zvyšování taktovací frekvence
 - rozšíření bitové šířky (8/16/32/64 bit)
 - zvýšení počtu pracovních registrů
 - pipelining - zřetězení instrukcí
   - současně se provádí více instrukcí
   - každá instrukce se nachází v jiné fázi zpracování

### Skalární architektura
 - umožňuje procesoru v jednom taktu načíst maximálně jednu instrukci

### Explicitní paralelní zpracování instrukcí
 - **VLIW**
   - Very Long Instruction Word
   - jednoduchý řadič
   - nepoužívá se
 - **Superskalární architektura**
   - složitější řadič
   - řadíč rozhoduje o paralelním provádění instrukcí
   - rozhoduje na základě obsazenosti pracovních registrů

### Prediktory skoků
 - Slouží k předběžnému odhadnutí, jestli se skok provede či nikoli
 - Dobré např. u smyček
 - **Při prvním volání** má prediktor **50% úspěšnost**
 - **Celková úspěšnost je 98%**

## Snižování spotřeby
 - **Technologické** (s postupem času)
   - Nižší vyžadované napětí
   - Nižší frekvence, nižší spotřeba (ARM big.LITTLE)
   - Výrobní technologie (méně nanometrů = více úsporné)
 - **Na úrovni hardware**
   - Softwarové snížení frekvence nebo napětí
   - Vypnutí nepoužívaných jader

## Rozšířené instrukční sady
 - rozšiřují možnosti instrukčních sad
 - **SIMD** (single instruction, multiple data)
   - umožňuje zpracovat více dat najednou pomocí vektorových výpočtů
 - **FMA** (fused multiply add)
   - umožňuje matematické operace s desetinnými čísly
 - **MMX** (multi media extension)
   - zpracování multimediálních dat
   - maticové výpočty (více vektorů najednou, 3D grafika)
   - pracuje jen s celými čísly
 - **3DNOW** (AMD MMX)
 - **SSE** (Intel odpověď na 3DNOW)
   - umožňuje práci s až 128 bitovými vektory
   - přidává datový typ double
 - **AVX** (AMD SSE)
   - umožňuje práci s až 256 bitovými vektory
   - AVX-512 → 521 bitové vektory
 
### Zabezpečení
 - šifrování dat → AES instruction set
 - hashování dat → SHA instruction set
 
