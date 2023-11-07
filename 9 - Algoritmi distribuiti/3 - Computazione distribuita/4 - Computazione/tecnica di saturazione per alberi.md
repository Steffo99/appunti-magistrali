[[algoritmo]] di [[computazione in grafi aciclici]].

> [!Summary]
> Si distribuisce un dato a ogni [[entità]], che effettua la computazione per i dati dei suoi figli e ne invia il risultato al genitore.  
> 
> Processati tutti i dati, viene effettuato un [[broadcast problem|broadcast]] ***dalla radice-[[leader]]*** per distribuire i risultati dell'algoritmo a tutti.

## [[Comportamento]]

### ***`LEADER`***

Invia un ***[[broadcast problem|broadcast]]*** a tutte le altre [[entità]], poi tutte passano ad `ACTIVE`.

### `ACTIVE`

Riceve informazioni finchè non ne ha ricevute tante quante il numero dei suoi vicini meno uno (i suoi figli).

Effettua il calcolo sulle informazioni che ha, poi ne invia il [[risultato]] al vicino rimasto, passando a `PROCESSING`.

### `PROCESSING`

Attende un ulteriore [[messaggio]], ***a meno che non si tratti della radice, che procederà immediatamente***.

Le [[entità]] `PROCESSING` che ricevono il [[messaggio]] ***lo accettano come [[risultato]]***, e poi lo mandano a tutti i loro vicini tranne il mittente, passando a `DONE`.

### `DONE`

Un'[[entità]] `DONE` conosce il [[risultato]] della computazione, e non fa nient'altro.

## [[costo computazionale distribuito|Costo computazionale]]

### [[Comunicazione]]

#### Attivazione

La fase di ***[[broadcast problem|broadcast]]*** ad `ACTIVE` richiede:
$$
\color{LightCoral} (2 \cdot Channels - (Entities - 1))
$$

#### Saturazione

La fase di `ACTIVE` invia un [[messaggio]] per ogni [[entità]], ***esclusa la radice***.
$$
\color{SkyBlue} (Entities - 1)
$$

#### Risoluzione

La fase di `PROCESSING` richiede un ulteriore [[messaggio]] per ogni [[entità]], ***tranne le foglie***:
$$
(Entities - Leaves)
$$
Nel caso peggiore, ci sarà una foglia sola, che quindi richiederà:
$$
\color{SpringGreen} (Entities - 1)
$$

#### Totale

In totale, nel caso peggiore i messaggi scambiati saranno:
$$
{\color{LightCoral} (2 \cdot Channels - (Entities - 1))}
+
{\color{SkyBlue} (Entities - 1)}
+
{\color{SpringGreen} (Entities - 1)}
$$
Ovvero:
$$
4 \cdot Entities - 4
$$

Che [[notazione asintotica|asintoticamente]] è:
$$
\Large O(Entities)
$$