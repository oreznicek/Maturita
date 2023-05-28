# 8 - Návrhové vzory I
 - Návrhové vzory pro vytváření instanci, rozšiřování funkcionality

## Návrhové vzory
 - programátorský ekvivalent matematických vzorečků
 - popisují řešení problémů při vývoji softwaru

### Proč je používat
 - __Urychlují návrh__ (Nevymýšlíme řešení, pouze ho implementujeme)
 - __Kvalitnější návrh__ (Snižují pravděpodobnost potenciálních chyb)
 - __Zjednodušují a zpřesňují komunikaci mezi členy týmu__
 - __Dnes již patří k základním znalostem programátorů__
 - __Nízká chybovost díky ověřené funkčnosti__

## Vzory pro vytváření instancí

### Singleton
 - jedináček
 - maximálně jedna instance dané třídy
   - tato instance by měla být globálně dostupná
 - nesmí být umožněno vytvářet další instance nebo přepsat vytvořenou instanci
 - měl by být thread-safe

### Simple Factory Method
 - definuje statickou metodu, která nahrazuje konstruktor
 - **použití**
   - potřebujeme rozhodnout, zda se má vytvořit nová instance
   - potřebujeme vracet instance různých typů
 - nemusí vracet instanci sebe, ale může si vybrat potomka, jehož instanci následně vrátí

### Pool
 - kolekce instancí daného typu
 - umožňuje znovu použít existující instance třídy
 - statický/dynamický počet instancí
   - statický - pokud dojdou instance nevytváříme nové
   - dynamický - pokud dojdou instance vytváříme nové

### Utility (knihovna)
 - skupina metod, které spolu nějak souvisí
 - matematické funkce, pomocné funkce
 - statické metody (v statické třídě)
 - nepotřebují instanci
 - vhodné znemožnit vytváření instancí

### Originál
 - třída, jejíž instance jsou svými parametry originální
 - neexistuje více jak jedna instance se stejnými parametry
 - pokud chceme v programu vytvořit stejnou instanci podruhé => vrátí tu prvně vytvořenou

## Neměnné objekty

### Přepravka
 - Crate
 - funguje jako kontejner
 - atributy jsou veřejné a konstantní
 - slouží např. k přenosu informací mezi metodami

## Vzory chování

### Služebník
 - Servant
 - poskytuje (definuje) nějaké chování skupině tříd
 - místo definice chování v každé třídě, nebo pokud chování nemůžeme definovat v rodičovské třídě, použijeme servanta
 - dalo by se říct, že ovládá nějakou třídu nebo skupinu tříd

### Template method
 - šablonová metoda
 - definuje kostru algoritmu uvnitř abstraktní třídy
 - rodičovská třída deklaruje jak by měl vypadat algoritmus 
 - následníci tento algoritmus poté implementují
