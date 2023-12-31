Problema per un [[sistema distribuito]].

## Definizione

Ad ogni [[entità]] viene fornito un [[9 - Algoritmi distribuiti/1 - Problemi algoritmici/parametro|input]], che usa per scegliere un valore da una [[enumerazione]].

Successivamente, deve accordarsi con almeno un certo numero di altre per selezionare un [[risultato|output]].

Gli algoritmi risolutivi devono sottostare ai seguenti principi:
- [[principio di non-trivialità]]
- [[principio di accordo]]
- [[principio di terminazione]]

## [[restrizioni al modello dei sistemi distribuiti|Restrizioni]]

- **[[restrizione di comunicazione|Comunicazione]]**
	- [[dimensione dei messaggi illimitata]]
	- [[full-duplex]]
- **[[restrizione di affidabilità|Affidabilità]]**
	- [[affidabilità nulla]]
		- [[guasti ubiqui]]
		- [[guasti permanenti]]
		- [[guasti di esecuzione]]
			- [[guasti di esecuzione di crash]]
			- [[niente guasti di esecuzione di omissione]]
			- [[niente guasti di esecuzione bizantini]]
		- [[niente guasti di trasmissione]]
- **[[restrizione di topologia|Topologia]]**
	- [[grafo connesso]]
	- [[grafo completo]]
- **[[restrizione di tempo|Tempo]]**
	- [[ritardo di comunicazione illimitato]]
	- [[risveglio multiplo]]
	- [[terminazione locale]]

## Risolvibilità

> [!Failure]
> Il problema non è risolvibile deterministicamente e asincronicamente:
> - **[[ritardo di comunicazione illimitato]]**
> 	- non si può distinguere un attesa da un [[guasti di esecuzione di crash|crash]]
> - **[[algoritmo deterministico]]**
> 	- non si può avere la certezza che l'[[algoritmo]] sia [[algoritmo corretto|corretto]].
