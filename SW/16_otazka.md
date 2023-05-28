# 16 - Výběr dat v SQL
 - SELECT, projekce, restrikce, podmínky, seskupování, agregace, spojování tabulek

## SELECT
 - příkaz `SELECT` se v SQL používá k získávání informací z databáze
 - vrací množinu záznamů z jedné nebo více tabulek

```SQL
SELECT sezna sloupců -- * = všechny, jinak odděleno čárkami
FROM seznam tabulek
WHERE restrikce
GROUP BY seskupit dle
HAVING restrikce
ORDER BY dle čeho řadit;
```
