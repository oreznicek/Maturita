# 21 - Procesory
 - Struktura současných procesorů (x86/64)
 - Techniky optimalizace provádění instrukcí
 - Snižování spotřeby
 - Rozšířené instrukční sady

## CPU

= integrovaný obvod, který provádí strojové instrukce

 - **Samotné jádro (ALU)**
 - **Řadič (Controlller)**
   - řídí procesy
   - dekóduje instrukce
 - **Registry**
   - velmi rychlá paměť
   - slouží pro ukládání mezivýsledků
 - **Vyrovnávací paměť (cache)**
   - rychlejší přístup k datům než z RAM
   - víceúrovňová
   - L1 nejmenší, ale nejrychlejší a je rozdělena na instrukce a data
   - L2 rychlejší a menší než L3
   - L3 největší a nejpomalejší paměť → společná pro všechny jádra (dříve na MB)

### CISC
 - Měl usnadnit práci programátorů
 - složitější instrukce = assembler se dal používat skoro jako HLL

### RISC
 - jednoduché instrukce
 - velké množství pracovních registrů (operace se provádí s těmito registry)

## Struktura současných procesorů
 - Moderní procesory popužívají x86-64 instrukční sadu
 - na venek mají Von Neumannovu architekturu
 - uvnitř Harvardská architektura → L1 je rozdělena na instrukční a datovou

### x86
 - architektura, která je založena na Intel procesoru 8086
 - **CISC** → komplexní instrukce
 - **variabilní délka instrukcí**
 - 16/32/64 bit
   - dnešní moderní CPU používají rozšíření x86-64
 - **zpětně kompatibilní**

## Optimalizace provádění instrukcí


### Fronta instrukcí
 - fronta, do které se vkládají operační kódy instrukcí z operační paměti
 - řadič si z fronty postupně odebírá instrukce
 - nemusíme čekat na operační paměť
   - když se provádí složitější instrukce → načítáme nové instrukce do fronty
   - když se provádí rychlé operace → můžeme rychle číst další instrukci z fronty
 - musí se vyprázdnit v případě, že dojde ke změně běhu programu (přerušení, instrukce skoku)

### Pipelining
 - zřetězení instrukcí
 - současně se provádí více instrukcí
 - každá instrukce se nachází v jiné fázi zpracování
 - velmi urychluje výpočty
 - fáze provedení instrukce
   - **fetch** - načtení instrukce z operační paměti
   - **decode** - dekódování instrukce v řadiči
   - **read** - přečteme obsah pracovních registrů + přenos do TEMP
   - **execute** - provedení instrukce
   - **write** - uložení výsledku do prac. reg.
 - **problémy**
   - volání a návrat podprogramu (musí se zapomenout rozpracované instrukce z fronty instrukcí)
   - je to problém jak u RISC tak u CISC
 - díky tomu vzniklo - **predikce skoků**

### Prediktory skoků
 - Slouží k předběžnému odhadnutí, jestli se skok provede či nikoli
 - Dobré např. u smyček
 - **Při prvním volání** má prediktor **50% úspěšnost**
 - **Celková úspěšnost je 98%**
 - jednobitový/dvoubitový

### Skalární architektura
 - umožňuje procesoru v jednom taktu načíst maximálně jednu instrukci

### Explicitní paralelní zpracování instrukcí
 - **VLIW**
   - Very Long Instruction Word
   - více nezávislých operací se sjednotí do jedné VLIW operace
   - tyto instrukce spouští paralelně 
   - nepoužívá se, místo toho ...
 - **Superskalární architektura**
   - složitější řadič
   - řadič rozhoduje o paralelním provádění instrukcí
   - rozhoduje na základě obsazenosti pracovních registrů
   - dynamičtější


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
 
