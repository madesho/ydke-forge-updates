# YDKE Forge 4.1

## Aggiornamento dell'interfaccia

**Material 3 Expressive attivo**
L'interfaccia passa all'ultima versione stabile di Material 3, che porta le API espressive fuori da experimental e le rende disponibili senza impostazioni. Il risultato visivo resta fedele a quello attuale: nessuno spostamento di layout, forme o colori. Verificato su tema chiaro, scuro e nero puro AMOLED.

## Correzioni

**Il dettaglio carta non interrogava più la rete dal punto di vista**
Aprendo il dettaglio di una carta, la traduzione veniva cercata direttamente dalla schermata, tenendo lo stato sparso nella finestra. Ora il lavoro è svolto una sola volta dal gestore dello stato e la schermata riceve solo il risultato. Questo corregge due difetti:

- passando le carte con lo swipe non si ripetevano più ricerche identiche: prima potevano partire contemporaneamente fino a tre ricerche della stessa traduzione, con richieste di rete ridondanti;
- la carta tradotta non veniva più riletta dalla versione non tradotta al riaprire il dettaglio.

**Il passaggio fra le carte con lo swipe e' piu' scattante**
Cambiando carta con il dito o scorrendo la strip in alto, il salto di pagina non era più visibile. Ora la pagina segue in modo coerente.

**Le quantita' scelte non si perdevano più**
Il selettore di quantità per aggiungere a un deck salvato si azzerava in alcuni passaggi. Ora il valore è gestito insieme allo stato del riquadro.

**Copia e incolla sugli appunti**
Le operazioni di copia e incolla usano l'API aggiornata di Android, con il controllo del contenuto vuoto negli appunti che prima mancava.

## Dettagli tecnici

- Compilazione release ottimizzata
- Nessuna modifica a database, traduzioni o carte: il funzionamento offline è identico
- Nessuna modifica all'aggiornamento in-app: la verifica della firma dell'APK resta attiva
