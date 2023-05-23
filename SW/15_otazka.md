# 15 - Jazyk SQL
 - Dialekt, standard, DML, DDL, DCL, TCL, INSERT, UPDATE, DELETE, CREATE, ALTER, DROP, GRANT, REVOKE, transakce

## SQL
 - Structured Query Language
 - Dotazovací jazyk
 - Slouží k práci s daty v relačních databázích
 - Nástupce jazyka SEQUEL
 - Jednoduchý jazyk
 - Dialekty - MySQL, SQL Server, ...

### Standard

### Příkazy (sublanguages)
 - SQL obsahuje několik příkazů a ty se dají ještě rozdělit do jednotlivých "podjazyků"
 - příkazy jsou zkrátka rozděleny do kategorií

<table>
	<thead>
		<tr>
			<th>Sublanguage</th>
			<th>Name</th>
			<th>Commands</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>DDL</td>
			<td>Data Definition Language</td>
			<td>CREATE, DROP, ALTER, TRUNCATE</td>
		</tr>
		<tr>
			<td>DML</td>
			<td>Data Manipulation Language</td>
			<td>INSERT, UPDATE, DELETE</td>
		</tr>
		<tr>
			<td>DQL</td>
			<td>Data Query Language</td>
			<td>SELECT</td>
		</tr>
		<tr>
			<td>TCL</td>
			<td>Transaction Control Language</td>
			<td>COMMIT, SAVEPOINT, ROLLBACK</td>
		</tr>
		<tr>
			<td>DCL</td>
			<td>Data Control Language</td>
			<td>GRANT, REVOKE</td>
		</tr>
	</tbody>
</table>

### INSERT
 - vkládá nové záznamy do tabulky

 1. způsob - specifikujeme jméno sloupce a hodnotu, kterou chceme vložit

```SQL
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

 2. způsob - pokud vkládáme hodnoty pro všechny sloupce v tabulce, nemusíme specifikovat jména sloupců, ale hodnoty musí být v pořadí sloupců v dané tabulce

```SQL
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

### UPDATE
 - modifikuje existující záznamy v tabulce
 - `WHERE` specifikuje, které záznamy se mají aktualizovat
   - bez použití podmínky se aktualizují všechny záznamy v tabulce!

```SQL
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### DELETE
 - maže existující záznamy v databázi
 - zase pozor na `WHERE`

```SQL
DELETE FROM table_name WHERE condition;
```

### CREATE
 - vytvoření databáze

```SQL
CREATE DATABASE databasename;
```

 - vytvoření nové tabulky v databázi

```SQL
CREATE TABLE table_name (
    column1 datatype,
    column2 varchar(64),
    column3 int(32),
    ...
);
```

### ALTER
 - používá se k přidání, mazání a modifikování sloupců
 - mění strukturu, ale ne data
 - přidání sloupce:

```SQL
ALTER TABLE Customers
ADD Email varchar(255);
```

 - mazání sloupce:

```SQL
ALTER TABLE Customers
DROP COLUMN Email;
```

 - modifikování sloupce:

```SQL
ALTER TABLE table_name
RENAME COLUMN old_name to new_name;
```

### DROP
 - kompletně smaže celou tabulku z databáze

```SQL
DROP TABLE table_name;
```
### GRANT
 - používá se k poskytnutí oprávnění k tabulkám

### REVOKE
 - odebírá práva

### Transakce
 - Sekvence SQL dotazů, které jsou vykonávány najednou
 - **BEGIN TRANSACTION** → začne novou transakci
 - **COMMIT** → uloží změny vytvořené během transakce
 - **ROLLBACK** → zvrátí všechny změny vytvořené během transakce do stavu před započetím transakce
 - **Použití:**
   - Převod financí z banky do banky
  
